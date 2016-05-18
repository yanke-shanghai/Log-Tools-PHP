Log-Tools-PHP
===================
一个简单的php程序，用于数据日志的获取，落到本地目录
***
###　　　　　　　　　　Author:DMINER
###　　　　　　E-mail:yanke_shanghai@126.com
　
===================
使用说明
--------
###接口解释
```php
    //落调试日志
    public function debug_log($s_log) {
        $this->write_log($s_log, 0); 
    }   

    //落错误日志
    public function error_log($s_log) {
        $this->write_log($s_log, 1); 
    }   

    //写日志接口
    private function write_log($s_log, $type) {
        if(date("Ymd", time()) !== $this->i_last_time) {
            $this->close_file();
            $this->open_file($type);
        }   

        if($type === 0) {
            if($this->r_debug === false)
                $this->open_file($type);
            fwrite($this->r_debug, date("[Y-m-d H:m:s]") . $s_log . "\n");
        } else {
            if($this->r_error === false)
                $this->open_file($type);
            fwrite($this->r_error, date("[Y-m-d H:m:s]") . $s_log . "\n");
        }   
    }   
```
