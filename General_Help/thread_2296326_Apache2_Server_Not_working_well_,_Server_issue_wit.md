---
title: "Apache2 Server Not working well , Server issue with getting path"
date: 2015-09-25
forum: General Help
---

### Post by AyogRai on 2015-09-25
I have Ubuntu 14.04.3 LTS server with lamp server Installed in it 


Problem which i have facing is regarding path issue of css and State define Misbehaving server


if we this code 


```
defined('ROOT_PATH') || define('ROOT_PATH', realpath(dirname(__FILE__) . ''));
```


or


    ```
defined('ROOT_PATH') || define('ROOT_PATH', getcwd());
```


website not load correctly 


if we give static path like `192.168.1.99` which is address of server, website load with no error 


Same problem in 


```
`define('SITE_STAGE','production'); ` 
```


if we use static stage website take db credentials from define credentials but if we use 


    ```
if(preg_match('/192.168/',$_SERVER['REMOTE_ADDR'])){
        define('SITE_STAGE','development');     
        define("TEST",true);
    }else{
        define('SITE_STAGE','production');
        define("TEST",false);
```

site show error and take db credentials from production (other server details) which are not correct for localhost.......if we refresh site load when refresh again site gives error


this not happens every time........after some time server on probably 2 or 3 hour after.....start misbehaving like this........and if i restart the apache2 problem gone.....but same after some time come again and again........really got confused what to do.......we have 40 network pc which are accessing server....and made changes from their in code and load website from their PC


we  max php memory size.....upload limit and everything but still facing problem 


****`PHP Variables`****


    ```
Variable                     Value
    _SERVER["HTTP_HOST"]          192.168.1.99
    _SERVER["HTTP_CONNECTION"]      -alive
    _SERVER["HTTP_ACCEPT"]    text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    _SERVER["HTTP_UPGRADE_INSECURE_REQUESTS"]    1
    _SERVER["HTTP_USER_AGENT"]    Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.99 Safari/537.36
    _SERVER["HTTP_ACCEPT_ENCODING"]    gzip, deflate, sdch
    _SERVER["HTTP_ACCEPT_LANGUAGE"]    en-GB,en-US;q=0.8,en;q=0.6
    _SERVER["PATH"]    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
    _SERVER["SERVER_SIGNATURE"]    <address>Apache/2.4.7 (Ubuntu) Server at 192.168.1.99 Port 80</address>
    _SERVER["SERVER_SOFTWARE"]    Apache/2.4.7 (Ubuntu)
    _SERVER["SERVER_NAME"]    192.168.1.99
    _SERVER["SERVER_ADDR"]    192.168.1.99
    _SERVER["SERVER_PORT"]    80
    _SERVER["REMOTE_ADDR"]    192.168.1.100
    _SERVER["DOCUMENT_ROOT"]    /var/www/html
    _SERVER["REQUEST_SCHEME"]    http
    _SERVER["CONTEXT_PREFIX"]    no value
    _SERVER["CONTEXT_DOCUMENT_ROOT"]    /var/www/html
    _SERVER["SERVER_ADMIN"]    webmaster@localhost
    _SERVER["SCRIPT_FILENAME"]    /var/www/html/info.php
    _SERVER["REMOTE_PORT"]    55589
    _SERVER["GATEWAY_INTERFACE"]    CGI/1.1
    _SERVER["SERVER_PROTOCOL"]    HTTP/1.1
    _SERVER["REQUEST_METHOD"]    GET
    _SERVER["QUERY_STRING"]    no value
    _SERVER["REQUEST_URI"]    /info.php
    _SERVER["SCRIPT_NAME"]    /info.php
    _SERVER["PHP_SELF"]    /info.php
    _SERVER["REQUEST_TIME_FLOAT"]    1443084741.898
    _SERVER["REQUEST_TIME"]    1443084741

```

****`Environment`****


    ```
Variable    Value
    APACHE_RUN_DIR    /var/run/apache2
    APACHE_PID_FILE    /var/run/apache2/apache2.pid
    PATH    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
    APACHE_LOCK_DIR    /var/lock/apache2
    LANG    C
    APACHE_RUN_USER    www-data
    APACHE_RUN_GROUP    www-data
    APACHE_LOG_DIR    /var/log/apache2
    PWD    /
```




****`XCache Cacher`****


    ```
XCache Cacher Module    enabled
    Readonly Protection    disabled
    Page Request Time    2015-09-24 14:22:21
    Cache Init Time    2015-09-24 13:02:39
    Cache Instance Id    1580
    Opcode Cache    enabled, 62,914,560 bytes, 1 split(s), with 8192 slots each
    Variable Cache    enabled, 4,194,304 bytes, 1 split(s), with 8192 slots each
    Shared Memory Schemes    mmap


    Directive    Local Value    Master Value
    xcache.admin.enable_auth    On    On
    xcache.allocator    bestfit    bestfit
    xcache.cacher    On    On
    xcache.count    1    1
    xcache.gc_interval    0    0
    xcache.mmap_path    /dev/zero    /dev/zero
    xcache.readonly_protection    Off    Off
    xcache.shm_scheme    mmap    mmap
    xcache.size    60M    60M
    xcache.slots    8K    8K
    xcache.stat    On    On
    xcache.ttl    0    0
    xcache.var_allocator    bestfit    bestfit
    xcache.var_count    1    1
    xcache.var_gc_interval    300    300
    xcache.var_maxttl    0    0
    xcache.var_namespace    no value    no value
    xcache.var_namespace_mode    0    0
    xcache.var_size    4M    4M
    xcache.var_slots    8K    8K
    xcache.var_ttl    0    0
```


****`apache2handler`****


    ```
Apache Version    Apache/2.4.7 (Ubuntu)
    Apache API Version    20120211
    Server Administrator    webmaster@localhost
    Hostname:Port    web-server:80
    User/Group    www-data(33)/33
    Max Requests    Per Child: 0 - Keep Alive: on - Max Per Connection: 100
    Timeouts    Connection: 300 - Keep-Alive: 5
    Virtual Server    Yes
    Server Root    /etc/apache2
    Loaded Modules    core mod_so mod_watchdog http_core mod_log_config mod_logio mod_version mod_unixd mod_access_compat mod_alias mod_auth_basic mod_authn_core mod_authn_file mod_authz_core mod_authz_host mod_authz_user mod_autoindex mod_deflate mod_dir mod_env mod_filter mod_mime prefork mod_negotiation mod_php5 mod_rewrite mod_setenvif mod_status
    
    Directive    Local Value    Master Value
    engine    1    1
    last_modified    0    0
    xbithack    0    0
```


****`Core`****


****`PHP Version    5.5.9-1ubuntu4.12`****


    ```
Directive    Local Value    Master Value
    allow_url_fopen    On    On
    allow_url_include    Off    Off
    always_populate_raw_post_data    Off    Off
    arg_separator.input    &    &
    arg_separator.output    &    &
    asp_tags    Off    Off
    auto_append_file    no value    no value
    auto_globals_jit    On    On
    auto_prepend_file    no value    no value
    browscap    no value    no value
    default_charset    no value    no value
    default_mimetype    text/html    text/html
    disable_classes    no value    no value
    disable_functions    pcntl_alarm,pcntl_fork,pcntl_waitpid,pcntl_wait,pcntl_wifexited,pcntl_wifstopped,pcntl_wifsignaled,pcntl_wexitstatus,pcntl_wtermsig,pcntl_wstopsig,pcntl_signal,pcntl_signal_dispatch,pcntl_get_last_error,pcntl_strerror,pcntl_sigprocmask,pcntl_sigwaitinfo,pcntl_sigtimedwait,pcntl_exec,pcntl_getpriority,pcntl_setpriority,    pcntl_alarm,pcntl_fork,pcntl_waitpid,pcntl_wait,pcntl_wifexited,pcntl_wifstopped,pcntl_wifsignaled,pcntl_wexitstatus,pcntl_wtermsig,pcntl_wstopsig,pcntl_signal,pcntl_signal_dispatch,pcntl_get_last_error,pcntl_strerror,pcntl_sigprocmask,pcntl_sigwaitinfo,pcntl_sigtimedwait,pcntl_exec,pcntl_getpriority,pcntl_setpriority,
    display_errors    Off    Off
    display_startup_errors    Off    Off
    doc_root    no value    no value
    docref_ext    no value    no value
    docref_root    no value    no value
    enable_dl    Off    Off
    enable_post_data_reading    On    On
    error_append_string    no value    no value
    error_log    no value    no value
    error_prepend_string    no value    no value
    error_reporting    22527    22527
    exit_on_timeout    Off    Off
    expose_php    On    On
    extension_dir    /usr/lib/php5/20121212    /usr/lib/php5/20121212
    file_uploads    On    On
    highlight.comment    #FF8000    #FF8000
    highlight.default    #0000BB    #0000BB
    highlight.html    #000000    #000000
    highlight.keyword    #007700    #007700
    highlight.string    #DD0000    #DD0000
    html_errors    On    On
    ignore_repeated_errors    Off    Off
    ignore_repeated_source    Off    Off
    ignore_user_abort    Off    Off
    implicit_flush    Off    Off
    include_path    .:/usr/share/php:/usr/share/pear    .:/usr/share/php:/usr/share/pear
    log_errors    On    On
    log_errors_max_len    1024    1024
    mail.add_x_header    On    On
    mail.force_extra_parameters    no value    no value
    mail.log    no value    no value
    max_execution_time    5000    5000
    max_file_uploads    20    20
    max_input_nesting_level    64    64
    max_input_time    5000    5000
    max_input_vars    1000    1000
    memory_limit    2000M    2000M
    open_basedir    no value    no value
    output_buffering    4096    4096
    output_handler    no value    no value
    post_max_size    2000M    2000M
    precision    14    14
    realpath_cache_size    16K    16K
    realpath_cache_ttl    120    120
    register_argc_argv    Off    Off
    report_memleaks    On    On
    report_zend_debug    On    On
    request_order    GP    GP
    sendmail_from    no value    no value
    sendmail_path    /usr/sbin/sendmail -t -i     /usr/sbin/sendmail -t -i 
    serialize_precision    17    17
    short_open_tag    On    On
    SMTP    localhost    localhost
    smtp_port    25    25
    sql.safe_mode    Off    Off
    sys_temp_dir    no value    no value
    track_errors    Off    Off
    unserialize_callback_func    no value    no value
    upload_max_filesize    2000M    2000M
    upload_tmp_dir    no value    no value
    user_dir    no value    no value
    user_ini.cache_ttl    300    300
    user_ini.filename    .user.ini    .user.ini
    variables_order    GPCS    GPCS
    xmlrpc_error_number    0    0
    xmlrpc_errors    Off    Off
    zend.detect_unicode    On    On
    zend.enable_gc    On    On
    zend.multibyte    Off    Off
    zend.script_encoding    no value
```

---

