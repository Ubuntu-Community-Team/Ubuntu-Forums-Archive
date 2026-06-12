---
title: "Apache2 and PHP"
date: 2005-06-03
forum: General Help
---

### Post by Metz on 2005-06-03
I've search through the forums for help...found a couple of threads and done everything specified....and read the installation/help in UbuntoGuide.....still no luck

Whenever I try to open the testphp.php file created during the guide...I still get the 'Open With' dialog.... :(:(

Help !?!?! This is driving me around the bend....

---

### Post by ghostrifle on 2005-06-03
Post the relevant config files and we'll have a look.

For example the following files:

```

/etc/apache2/apache2.conf
/etc/apache2/httpd.conf
/etc/php4/apache2/php4.ini

```

and in /etc/apache2/mods-enabled the following files:

```

actions.load  cgi.load  php4.conf  php4.load  userdir.conf  userdir.load

```

---

### Post by nilus on 2005-06-03
How did you installed it?
I installed apache2, php and mysql via apt-get and it works without any change in configuration files.
Did you tryed typing in your browser the url: [http://localhost/testphp.php](http://localhost/testphp.php) ?

---

### Post by Metz on 2005-06-04
Here are the files as requested....

Thanks for any help you can provide guys :)

(I've had to put them on my webspace coz they're too big to post here)

[http://www.zoo.co.uk/~z0001222/files/apache2.conf](http://www.zoo.co.uk/~z0001222/files/apache2.conf)
[http://www.zoo.co.uk/~z0001222/files/httpd.conf](http://www.zoo.co.uk/~z0001222/files/httpd.conf)
[http://www.zoo.co.uk/~z0001222/files/php.ini](http://www.zoo.co.uk/~z0001222/files/php.ini)  (I don't have a php4.ini)
[http://www.zoo.co.uk/~z0001222/files/cgi.load](http://www.zoo.co.uk/~z0001222/files/cgi.load)
[http://www.zoo.co.uk/~z0001222/files/php4.conf](http://www.zoo.co.uk/~z0001222/files/php4.conf)
[http://www.zoo.co.uk/~z0001222/files/userdir.conf](http://www.zoo.co.uk/~z0001222/files/userdir.conf)
[http://www.zoo.co.uk/~z0001222/files/userdir.load](http://www.zoo.co.uk/~z0001222/files/userdir.load)

php4.load and actions.load don't exist on my setup.

---

### Post by Metz on 2005-06-04
I don't have a php4.ini ?!....only php.ini

[u]
/etc/php4/apache2/php.ini (Part 1)
[/u]

```

[PHP]

;;;;;;;;;;;
; WARNING ;
;;;;;;;;;;;
; This is the default settings file for new PHP installations.
; By default, PHP installs itself with a configuration suitable for
; development purposes, and *NOT* for production purposes.
; For several security-oriented considerations that should be taken
; before going online with your site, please consult php.ini-recommended
; and http://php.net/manual/en/security.php.


;;;;;;;;;;;;;;;;;;;
; About this file ;
;;;;;;;;;;;;;;;;;;;
; This file controls many aspects of PHP's behavior.  In order for PHP to
; read it, it must be named 'php.ini'.  PHP looks for it in the current
; working directory, in the path designated by the environment variable
; PHPRC, and in the path that was defined in compile time (in that order).
; Under Windows, the compile-time path is the Windows directory.  The
; path in which the php.ini file is looked for can be overridden using
; the -c argument in command line mode.
;
; The syntax of the file is extremely simple.  Whitespace and Lines
; beginning with a semicolon are silently ignored (as you probably guessed).
; Section headers (e.g. [Foo]) are also silently ignored, even though
; they might mean something in the future.
;
; Directives are specified using the following syntax:
; directive = value
; Directive names are *case sensitive* - foo=bar is different from FOO=bar.
;
; The value can be a string, a number, a PHP constant (e.g. E_ALL or M_PI), one
; of the INI constants (On, Off, True, False, Yes, No and None) or an expression
; (e.g. E_ALL & ~E_NOTICE), or a quoted string ("foo").
;
; Expressions in the INI file are limited to bitwise operators and parentheses:
; |        bitwise OR
; &        bitwise AND
; ~        bitwise NOT
; !        boolean NOT
;
; Boolean flags can be turned on using the values 1, On, True or Yes.
; They can be turned off using the values 0, Off, False or No.
;
; An empty string can be denoted by simply not writing anything after the equal
; sign, or by using the None keyword:
;
;  foo =         ; sets foo to an empty string
;  foo = none    ; sets foo to an empty string
;  foo = "none"  ; sets foo to the string 'none'
;
; If you use constants in your value, and these constants belong to a
; dynamically loaded extension (either a PHP extension or a Zend extension),
; you may only use these constants *after* the line that loads the extension.
;
; All the values in the php.ini-dist file correspond to the builtin
; defaults (that is, if no php.ini is used, or if you delete these lines,
; the builtin defaults will be identical).


;;;;;;;;;;;;;;;;;;;;
; Language Options ;
;;;;;;;;;;;;;;;;;;;;

; Enable the PHP scripting language engine under Apache.
engine = On

; Allow the <? tag.  Otherwise, only <?php and <script> tags are recognized.  
; NOTE: Using short tags should be avoided when developing applications or
; libraries that are meant for redistribution, or deployment on PHP
; servers which are not under your control, because short tags may not
; be supported on the target server. For portable, redistributable code,
; be sure not to use short tags.
short_open_tag = On

; Allow ASP-style <% %> tags.
asp_tags = Off

; The number of significant digits displayed in floating point numbers.
precision    =  12

; Enforce year 2000 compliance (will cause problems with non-compliant browsers)
y2k_compliance = On

; Output buffering allows you to send header lines (including cookies) even
; after you send body content, at the price of slowing PHP's output layer a
; bit.  You can enable output buffering during runtime by calling the output
; buffering functions.  You can also enable output buffering for all files by
; setting this directive to On.  If you wish to limit the size of the buffer
; to a certain size - you can use a maximum number of bytes instead of 'On', as
; a value for this directive (e.g., output_buffering=4096).
output_buffering = Off

; You can redirect all of the output of your scripts to a function.  For
; example, if you set output_handler to "mb_output_handler", character
; encoding will be transparently converted to the specified encoding.
; Setting any output handler automatically turns on output buffering.
; Note: People who wrote portable scripts should not depend on this ini
;       directive. Instead, explicitly set the output handler using ob_start().
;       Using this ini directive may cause problems unless you know what script 
;       is doing.
; Note: You cannot use both "mb_output_handler" with "ob_iconv_handler"
;       and you cannot use both "ob_gzhandler" and "zlib.output_compression". 
;output_handler =

; Transparent output compression using the zlib library
; Valid values for this option are 'off', 'on', or a specific buffer size
; to be used for compression (default is 4KB)
; Note: Resulting chunk size may vary due to nature of compression. PHP 
;       outputs chunks that are few hundreds bytes each as a result of 
;       compression. If you prefer a larger chunk size for better 
;       performance, enable output_buffering in addition.
; Note: You need to use zlib.output_handler instead of the standard
;       output_handler, or otherwise the output will be corrupted.
zlib.output_compression = Off

; You cannot specify additional output handlers if zlib.output_compression
; is activated here. This setting does the same as output_handler but in
; a different order.
;zlib.output_handler =

; Implicit flush tells PHP to tell the output layer to flush itself
; automatically after every output block.  This is equivalent to calling the
; PHP function flush() after each and every call to print() or echo() and each
; and every HTML block.  Turning this option on has serious performance
; implications and is generally recommended for debugging purposes only.
implicit_flush = Off

; The unserialize callback function will be called (with the undefined class'
; name as parameter), if the unserializer finds an undefined class
; which should be instanciated.
; A warning appears if the specified function is not defined, or if the
; function doesn't include/implement the missing class.
; So only set this entry, if you really want to implement such a 
; callback-function.
unserialize_callback_func=

; When floats & doubles are serialized store serialize_precision significant
; digits after the floating point. The default value ensures that when floats
; are decoded with unserialize, the data will remain the same.
serialize_precision = 100

; Whether to enable the ability to force arguments to be passed by reference
; at function call time.  This method is deprecated and is likely to be
; unsupported in future versions of PHP/Zend.  The encouraged method of
; specifying which arguments should be passed by reference is in the function
; declaration.  You're encouraged to try and turn this option Off and make
; sure your scripts work properly with it in order to ensure they will work
; with future versions of the language (you will receive a warning each time
; you use this feature, and the argument will be passed by value instead of by
; reference).
allow_call_time_pass_reference = On

; Safe Mode
;
safe_mode = Off

; By default, Safe Mode does a UID compare check when
; opening files. If you want to relax this to a GID compare,
; then turn on safe_mode_gid.
safe_mode_gid = Off

; When safe_mode is on, UID/GID checks are bypassed when
; including files from this directory and its subdirectories.
; (directory must also be in include_path or full path must
; be used when including)
safe_mode_include_dir =        

; When safe_mode is on, only executables located in the safe_mode_exec_dir
; will be allowed to be executed via the exec family of functions.
safe_mode_exec_dir =

; Setting certain environment variables may be a potential security breach.
; This directive contains a comma-delimited list of prefixes.  In Safe Mode,
; the user may only alter environment variables whose names begin with the
; prefixes supplied here.  By default, users will only be able to set
; environment variables that begin with PHP_ (e.g. PHP_FOO=BAR).
;
; Note:  If this directive is empty, PHP will let the user modify ANY
; environment variable!
safe_mode_allowed_env_vars = PHP_

; This directive contains a comma-delimited list of environment variables that
; the end user won't be able to change using putenv().  These variables will be
; protected even if safe_mode_allowed_env_vars is set to allow to change them.
safe_mode_protected_env_vars = LD_LIBRARY_PATH

; open_basedir, if set, limits all file operations to the defined directory
; and below.  This directive makes most sense if used in a per-directory
; or per-virtualhost web server configuration file. This directive is
; *NOT* affected by whether Safe Mode is turned On or Off.
;open_basedir =

; This directive allows you to disable certain functions for security reasons.
; It receives a comma-delimited list of function names. This directive is
; *NOT* affected by whether Safe Mode is turned On or Off.
disable_functions =

; This directive allows you to disable certain classes for security reasons.
; It receives a comma-delimited list of class names. This directive is
; *NOT* affected by whether Safe Mode is turned On or Off.
disable_classes =

; Colors for Syntax Highlighting mode.  Anything that's acceptable in
; <font color="??????"> would work.
;highlight.string  = #DD0000
;highlight.comment = #FF9900
;highlight.keyword = #007700
;highlight.bg      = #FFFFFF
;highlight.default = #0000BB
;highlight.html    = #000000


;
; Misc
;
; Decides whether PHP may expose the fact that it is installed on the server
; (e.g. by adding its signature to the Web server header).  It is no security
; threat in any way, but it makes it possible to determine whether you use PHP
; on your server or not.
expose_php = On


;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;

max_execution_time = 30     ; Maximum execution time of each script, in seconds
max_input_time = 60 ; Maximum amount of time each script may spend parsing request data
memory_limit = 8M      ; Maximum amount of memory a script may consume (8MB)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Error handling and logging ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

; error_reporting is a bit-field.  Or each number up to get desired error
; reporting level
; E_ALL             - All errors and warnings
; E_ERROR           - fatal run-time errors
; E_WARNING         - run-time warnings (non-fatal errors)
; E_PARSE           - compile-time parse errors
; E_NOTICE          - run-time notices (these are warnings which often result
;                     from a bug in your code, but it's possible that it was
;                     intentional (e.g., using an uninitialized variable and
;                     relying on the fact it's automatically initialized to an
;                     empty string)
; E_CORE_ERROR      - fatal errors that occur during PHP's initial startup
; E_CORE_WARNING    - warnings (non-fatal errors) that occur during PHP's
;                     initial startup
; E_COMPILE_ERROR   - fatal compile-time errors
; E_COMPILE_WARNING - compile-time warnings (non-fatal errors)
; E_USER_ERROR      - user-generated error message
; E_USER_WARNING    - user-generated warning message
; E_USER_NOTICE     - user-generated notice message
;
; Examples:
;
;   - Show all errors, except for notices
;
;error_reporting = E_ALL & ~E_NOTICE
;
;   - Show only errors
;
;error_reporting = E_COMPILE_ERROR|E_ERROR|E_CORE_ERROR
;
;   - Show all errors except for notices
;
error_reporting  =  E_ALL & ~E_NOTICE

; Print out errors (as a part of the output).  For production web sites,
; you're strongly encouraged to turn this feature off, and use error logging
; instead (see below).  Keeping display_errors enabled on a production web site
; may reveal security information to end users, such as file paths on your Web
; server, your database schema or other information.
display_errors = On

; Even when display_errors is on, errors that occur during PHP's startup
; sequence are not displayed.  It's strongly recommended to keep
; display_startup_errors off, except for when debugging.
display_startup_errors = Off

; Log errors into a log file (server-specific log, stderr, or error_log (below))
; As stated above, you're strongly advised to use error logging in place of
; error displaying on production web sites.
log_errors = Off

; Set maximum length of log_errors. In error_log information about the source is
; added. The default is 1024 and 0 allows to not apply any maximum length at all.
log_errors_max_len = 1024

; Do not log repeated messages. Repeated errors must occur in same file on same
; line until ignore_repeated_source is set true.
ignore_repeated_errors = Off

; Ignore source of message when ignoring repeated messages. When this setting 
; is On you will not log errors with repeated messages from different files or
; sourcelines.
ignore_repeated_source = Off

; If this parameter is set to Off, then memory leaks will not be shown (on
; stdout or in the log). This has only effect in a debug compile, and if 
; error reporting includes E_WARNING in the allowed list
report_memleaks = On

; Store the last error/warning message in $php_errormsg (boolean).
track_errors = Off

; Disable the inclusion of HTML tags in error messages.
;html_errors = Off
  
; If html_errors is set On PHP produces clickable error messages that direct 
; to a page describing the error or function causing the error in detail.
; You can download a copy of the PHP manual from http://www.php.net/docs.php 
; and change docref_root to the base URL of your local copy including the
; leading '/'. You must also specify the file extension being used including 
; the dot.
;docref_root = "/phpmanual/"
;docref_ext = .html
  
; String to output before an error message.
;error_prepend_string = "<font color=ff0000>"

; String to output after an error message.
;error_append_string = "</font>"

; Log errors to specified file.
;error_log = filename

; Log errors to syslog (Event Log on NT, not valid in Windows 95).
;error_log = syslog


;;;;;;;;;;;;;;;;;
; Data Handling ;
;;;;;;;;;;;;;;;;;
;
; Note - track_vars is ALWAYS enabled as of PHP 4.0.3

; The separator used in PHP generated URLs to separate arguments.
; Default is "&". 
;arg_separator.output = "&amp;"

; List of separator(s) used by PHP to parse input URLs into variables.
; Default is "&". 
; NOTE: Every character in this directive is considered as separator!
;arg_separator.input = ";&"

; This directive describes the order in which PHP registers GET, POST, Cookie,
; Environment and Built-in variables (G, P, C, E & S respectively, often
; referred to as EGPCS or GPC).  Registration is done from left to right, newer
; values override older values.
variables_order = "EGPCS"

; Whether or not to register the EGPCS variables as global variables.  You may
; want to turn this off if you don't want to clutter your scripts' global scope
; with user data.  This makes most sense when coupled with track_vars - in which
; case you can access all of the GPC variables through the $HTTP_*_VARS[],
; variables.
;
; You should do your best to write your scripts so that they do not require
; register_globals to be on;  Using form variables as globals can easily lead
; to possible security problems, if the code is not very well thought of.
register_globals = Off

; This directive tells PHP whether to declare the argv&argc variables (that
; would contain the GET information).  If you don't use these variables, you
; should turn it off for increased performance.
register_argc_argv = On

; Maximum size of POST data that PHP will accept.
post_max_size = 8M

; This directive is deprecated.  Use variables_order instead.
gpc_order = "GPC"

; Magic quotes
;

; Magic quotes for incoming GET/POST/Cookie data.
magic_quotes_gpc = On

; Magic quotes for runtime-generated data, e.g. data from SQL, from exec(), etc.
magic_quotes_runtime = Off    

; Use Sybase-style magic quotes (escape ' with '' instead of \').
magic_quotes_sybase = Off

; Automatically add files before or after any PHP document.
auto_prepend_file =
auto_append_file =

; As of 4.0b4, PHP always outputs a character encoding by default in
; the Content-type: header.  To disable sending of the charset, simply
; set it to be empty.
;
; PHP's built-in default is text/html
default_mimetype = "text/html"
;default_charset = "iso-8859-1"

; Always populate the $HTTP_RAW_POST_DATA variable.
;always_populate_raw_post_data = On


;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;

; UNIX: "/path1:/path2"  
;include_path = ".:/usr/share/php"
;
; Windows: "\path1;\path2"
;include_path = ".;c:\php\includes"

; The root of the PHP pages, used only if nonempty.
; if PHP was not compiled with FORCE_REDIRECT, you SHOULD set doc_root
; if you are running php as a CGI under any web server (other than IIS)
; see documentation for security issues.  The alternate is to use the
; cgi.force_redirect configuration below
doc_root =

; The directory under which PHP opens the script using /~username used only
; if nonempty.
user_dir =

; Directory in which the loadable extensions (modules) reside.
; extension_dir = "./"

; Whether or not to enable the dl() function.  The dl() function does NOT work
; properly in multithreaded servers, such as IIS or Zeus, and is automatically
; disabled on them.
enable_dl = On

; cgi.force_redirect is necessary to provide security running PHP as a CGI under
; most web servers.  Left undefined, PHP turns this on by default.  You can
; turn it off here AT YOUR OWN RISK
; **You CAN safely turn this off for IIS, in fact, you MUST.**
; cgi.force_redirect = 1

; if cgi.nph is enabled it will force cgi to always sent Status: 200 with
; every request.
; cgi.nph = 1

; if cgi.force_redirect is turned on, and you are not running under Apache or Netscape 
; (iPlanet) web servers, you MAY need to set an environment variable name that PHP
; will look for to know it is OK to continue execution.  Setting this variable MAY
; cause security issues, KNOW WHAT YOU ARE DOING FIRST.
; cgi.redirect_status_env = ;

; cgi.fix_pathinfo provides *real* PATH_INFO/PATH_TRANSLATED support for CGI.  PHP's
; previous behaviour was to set PATH_TRANSLATED to SCRIPT_FILENAME, and to not grok
; what PATH_INFO is.  For more information on PATH_INFO, see the cgi specs.  Setting
; this to 1 will cause PHP CGI to fix it's paths to conform to the spec.  A setting
; of zero causes PHP to behave as before.  Default is zero.  You should fix your scripts
; to use SCRIPT_FILENAME rather than PATH_TRANSLATED.
; cgi.fix_pathinfo=0

; FastCGI under IIS (on WINNT based OS) supports the ability to impersonate
; security tokens of the calling client.  This allows IIS to define the
; security context that the request runs under.  mod_fastcgi under Apache
; does not currently support this feature (03/17/2002)
; Set to 1 if running under IIS.  Default is zero.
; fastcgi.impersonate = 1;

; cgi.rfc2616_headers configuration option tells PHP what type of headers to
; use when sending HTTP response code. If it's set 0 PHP sends Status: header that
; is supported by Apache. When this option is set to 1 PHP will send
; RFC2616 compliant header.
; Default is zero.
;cgi.rfc2616_headers = 0 
 

;;;;;;;;;;;;;;;;
; File Uploads ;
;;;;;;;;;;;;;;;;

; Whether to allow HTTP file uploads.
file_uploads = On

; Temporary directory for HTTP uploaded files (will use system default if not
; specified).
;upload_tmp_dir =

; Maximum allowed size for uploaded files.
upload_max_filesize = 2M


;;;;;;;;;;;;;;;;;;
; Fopen wrappers ;
;;;;;;;;;;;;;;;;;;

; Whether to allow the treatment of URLs (like http:// or ftp://) as files.
allow_url_fopen = On

; Define the anonymous ftp password (your email address)
;from="john@doe.com"

; Define the User-Agent string
; user_agent="PHP"

; Default timeout for socket based streams (seconds)
default_socket_timeout = 60

; If your scripts have to deal with files from Macintosh systems,
; or you are running on a Mac and need to deal with files from
; unix or win32 systems, setting this flag will cause PHP to
; automatically detect the EOL character in those files so that
; fgets() and file() will work regardless of the source of the file.
; auto_detect_line_endings = Off


;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;
;
; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename.extension
;
; For example, on Windows:
;
;   extension=msql.dll
;
; ... or under UNIX:
;
;   extension=msql.so
;
; Note that it should be the name of the module only; no directory information 
; needs to go here.  Specify the location of the extension with the
; extension_dir directive above.

; Example lines:

;extension=mysql.so
;extension=gd.so


;;;;;;;;;;;;;;;;;;;
; Module Settings ;
;;;;;;;;;;;;;;;;;;;

[Syslog]
; Whether or not to define the various syslog variables (e.g. $LOG_PID,
; $LOG_CRON, etc.).  Turning it off is a good idea performance-wise.  In
; runtime, you can define these variables by calling define_syslog_variables().
define_syslog_variables  = Off

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = me@example.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
;sendmail_path =

[Java]
;java.class.path = .\php_java.jar
;java.home = c:\jdk
;java.library = c:\jdk\jre\bin\hotspot\jvm.dll 
;java.library.path = .\

[SQL]
sql.safe_mode = Off

[ODBC]
;odbc.default_db    =  Not yet implemented
;odbc.default_user  =  Not yet implemented
;odbc.default_pw    =  Not yet implemented

; Allow or prevent persistent links.
odbc.allow_persistent = On

; Check that a connection is still valid before reuse.
odbc.check_persistent = On

; Maximum number of persistent links.  -1 means no limit.
odbc.max_persistent = -1

; Maximum number of links (persistent + non-persistent).  -1 means no limit.
odbc.max_links = -1  

; Handling of LONG fields.  Returns number of bytes to variables.  0 means
; passthru.
odbc.defaultlrl = 4096  

; Handling of binary data.  0 means passthru, 1 return as is, 2 convert to char.
; See the documentation on odbc_binmode and odbc_longreadlen for an explanation
; of uodbc.defaultlrl and uodbc.defaultbinmode
odbc.defaultbinmode = 1  

[MySQL]
; Allow or prevent persistent links.
mysql.allow_persistent = On

; Maximum number of persistent links.  -1 means no limit.
mysql.max_persistent = -1

; Maximum number of links (persistent + non-persistent).  -1 means no limit.
mysql.max_links = -1

; Default port number for mysql_connect().  If unset, mysql_connect() will use
; the $MYSQL_TCP_PORT or the mysql-tcp entry in /etc/services or the
; compile-time value defined MYSQL_PORT (in that order).  Win32 will only look
; at MYSQL_PORT.
mysql.default_port =

```

---

### Post by ghostrifle on 2005-06-04
Well, without futher looking at your config files: Did you install libapache2-mod-php4 ??? Installing php4 and apache2 isn't enough... you need the mentioned package above too.

---

### Post by GrumpySimon on 2005-06-04
I'm not sure how Ubuntu handles Apache (I prefer to do it myself), but you need to tell apache to parse php files with the php module. 

In the httpd.conf file, add this line:
```

LoadModule mod_php /path/to/apache2/modules/mod_php.so

```
Where the last part links directly to the mod_php file.

Restart apache (/etc/init.d/apachectl restart), and try again.

It's been a while since I've used the enabled/disabled system that ubuntu uses (and then it was when I was using Debian), but you should just be able to link (ln -s) the php.conf file inside the enabled directory. If you can show me a ls -lR of the /etc/apache2 directory I can probably give more info.

--Simon

---

### Post by Metz on 2005-06-04
ls- lR on /etc/apache2

```

.:
total 55
-rw-r--r--  1 root root 12480 2005-06-03 22:14 apache2.conf
-rw-r--r--  1 root root 12482 2005-05-06 09:21 apache2.conf~
drwxr-xr-x  2 root root  1024 2005-05-14 18:54 conf.d
-rw-r--r--  1 root root   748 2005-05-06 09:14 envvars
-rw-r--r--  1 root root   268 2005-05-14 18:54 httpd.conf
-rw-r--r--  1 root root 12441 2005-05-06 09:21 magic
drwxr-xr-x  2 root root  2048 2005-06-03 22:32 mods-available
drwxr-xr-x  2 root root  1024 2005-06-03 22:32 mods-enabled
-rw-r--r--  1 root root    10 2005-05-14 18:54 ports.conf
-rw-r--r--  1 root root  2266 2005-05-06 09:21 README
drwxr-xr-x  2 root root  1024 2005-05-14 18:54 sites-available
drwxr-xr-x  2 root root  1024 2005-05-14 18:54 sites-enabled
drwxr-xr-x  2 root root  1024 2005-05-06 09:21 ssl

./conf.d:
total 1
-rw-r--r--  1 root root 24 2005-05-14 18:54 charset

./mods-available:
total 47
-rw-r--r--  1 root root   66 2005-05-06 09:21 actions.load
-rw-r--r--  1 root root   60 2005-05-06 09:21 asis.load
-rw-r--r--  1 root root   70 2005-05-06 09:21 auth_anon.load
-rw-r--r--  1 root root   68 2005-05-06 09:21 auth_dbm.load
-rw-r--r--  1 root root   74 2005-05-06 09:21 auth_digest.load
-rw-r--r--  1 root root  130 2005-05-06 09:21 auth_ldap.load
-rw-r--r--  1 root root   62 2005-05-06 09:21 cache.load
-rw-r--r--  1 root root   70 2005-05-06 09:21 cern_meta.load
-rw-r--r--  1 root root   61 2005-05-06 09:21 cgid.conf
-rw-r--r--  1 root root   60 2005-05-06 09:21 cgid.load
-rw-r--r--  1 root root   58 2005-05-06 09:21 cgi.load
-rw-r--r--  1 root root   37 2005-05-06 09:21 dav_fs.conf
-rw-r--r--  1 root root   64 2005-05-06 09:21 dav_fs.load
-rw-r--r--  1 root root   58 2005-05-06 09:21 dav.load
-rw-r--r--  1 root root   66 2005-05-06 09:21 deflate.load
-rw-r--r--  1 root root   72 2005-05-06 09:21 disk_cache.load
-rw-r--r--  1 root root   66 2005-05-06 09:21 expires.load
-rw-r--r--  1 root root   72 2005-05-06 09:21 ext_filter.load
-rw-r--r--  1 root root   72 2005-05-06 09:21 file_cache.load
-rw-r--r--  1 root root   66 2005-05-06 09:21 headers.load
-rw-r--r--  1 root root   60 2005-05-06 09:21 imap.load
-rw-r--r--  1 root root   66 2005-05-06 09:21 include.load
-rw-r--r--  1 root root   60 2005-05-06 09:21 info.load
-rw-r--r--  1 root root   60 2005-05-06 09:21 ldap.load
-rw-r--r--  1 root root   70 2005-05-06 09:21 mem_cache.load
-rw-r--r--  1 root root   90 2005-05-06 09:21 mime_magic.conf
-rw-r--r--  1 root root   72 2005-05-06 09:21 mime_magic.load
-rw-r--r--  1 root root  133 2005-04-01 15:16 php4.conf
-rw-r--r--  1 root root   59 2005-04-01 15:16 php4.load
-rw-r--r--  1 root root  840 2005-05-06 09:21 proxy.conf
-rw-r--r--  1 root root   78 2005-05-06 09:21 proxy_connect.load
-rw-r--r--  1 root root   70 2005-05-06 09:21 proxy_ftp.load
-rw-r--r--  1 root root   72 2005-05-06 09:21 proxy_http.load
-rw-r--r--  1 root root  316 2005-05-06 09:21 proxy.load
-rw-r--r--  1 root root   66 2005-05-06 09:21 rewrite.load
-rw-r--r--  1 root root   66 2005-05-06 09:21 speling.load
-rw-r--r--  1 root root 3545 2005-05-06 09:21 ssl.conf
-rw-r--r--  1 root root   58 2005-05-06 09:21 ssl.load
-rw-r--r--  1 root root   64 2005-05-06 09:21 suexec.load
-rw-r--r--  1 root root   70 2005-05-06 09:21 unique_id.load
-rw-r--r--  1 root root  244 2005-05-06 09:21 userdir.conf
-rw-r--r--  1 root root   66 2005-05-06 09:21 userdir.load
-rw-r--r--  1 root root   70 2005-05-06 09:21 usertrack.load
-rw-r--r--  1 root root   74 2005-05-06 09:21 vhost_alias.load

./mods-enabled:
total 0
lrwxrwxrwx  1 root root 36 2005-05-14 18:54 cgi.load -> /etc/apache2/mods-available/cgi.load
lrwxrwxrwx  1 root root 37 2005-06-03 22:32 php4.conf -> /etc/apache2/mods-available/php4.conf
lrwxrwxrwx  1 root root 37 2005-06-03 22:32 php4.load -> /etc/apache2/mods-available/php4.load
lrwxrwxrwx  1 root root 40 2005-05-14 18:54 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx  1 root root 40 2005-05-14 18:54 userdir.load -> /etc/apache2/mods-available/userdir.load

./sites-available:
total 2
-rw-r--r--  1 root root 1225 2005-05-06 09:21 default

./sites-enabled:
total 0
lrwxrwxrwx  1 root root 36 2005-05-14 18:54 000-default -> /etc/apache2/sites-available/default

./ssl:
total 0


```

---

### Post by GrumpySimon on 2005-06-04
What does php4.load say? It should contain that LoadModule directive.

--Simon

---

### Post by Metz on 2005-06-04
[QUOTE=GrumpySimon]What does php4.load say? It should contain that LoadModule directive.

--Simon[/QUOTE]
 I didn't have a php4.load file :(

I've completely broken it now......I've gone through a reinstallation of apache2, php4 and mysql.....and I now get "Connection refused when attempting to contact localhost" in Firefox :(

I need to find a brick wall to headbutt to convince myself this effort will all be worth it.

hehe...I'm a developer....not a sysadmin....it really must be a different mentality and it's going to take me time to change....:):p

---

### Post by GrumpySimon on 2005-06-04
[QUOTE=Metz]I didn't have a php4.load file :(

I've completely broken it now......I've gone through a reinstallation of apache2, php4 and mysql.....and I now get "Connection refused when attempting to contact localhost" in Firefox :(

I need to find a brick wall to headbutt to convince myself this effort will all be worth it.

hehe...I'm a developer....not a sysadmin....it really must be a different mentality and it's going to take me time to change....:):p[/QUOTE]
 Ok, delete php4.load and make a new one. 

1) Relax :)

2) Work out where libphp4.so is installed. It's probably /usr/lib/apache2/. If it's not there, then run this command:
```

locate libphp4.so

```
& remember where it is. 

It may also be called mod_php4.so.

3) cd /etc/apache2

4) sudo su

5) gedit mods-available/php4.load

6) Enter this as is:
```

LoadModule mod_php /usr/lib/apache2/libphp4.so

```

7) save file

8) restart apache 
```

/etc/init.d/apachectl restart

```

9) Try again.

--Simon

---

### Post by Metz on 2005-06-04
Everything done.....but 8), the restart fails.....

```

root@prime-x:/etc/apache2 # /etc/init.d/apachectl restart
bash: /etc/init.d/apachectl: No such file or directory

```

:(

When I try localhost...I still get the same problem :(

---

### Post by GrumpySimon on 2005-06-04
Find something in /etc/init.d that looks apache related. It could be called apache2ctl or httpd, then use that instead of apachectl. 

If there's nothing there like that, then run:
```

killall httpd
killall apache
/etc/apache2/bin/apachectl start

```

--Simon

---

### Post by Metz on 2005-06-04
Okay....I have a /etc/init.d/apache, but no /etc/init.d/apachectl or /etc/init.d/apache2ctl

The killall statements killed nothing.

I have however found a /usr/sbin/apache2ctl...but attempting to start that gives the following....
```

root@prime-x:/etc/apache2 # /usr/sbin/apache2ctl start
Syntax error on line 1 of /etc/apache2/mods-enabled/php4.load:
Cannot load /usr/lib/apache2/libphp4.so into server: /usr/lib/apache2/libphp4.so: cannot open shared object file: No such file or directory

```

---

### Post by Metz on 2005-06-04
Right....I've got localhost to respond again.

But to do so....I had to apt-get install apache.....not apt-get install apache2 ....:confused:

Now I'm going to return to the rest of it...and see if I can get any result on php. I've just tried the testphp.php file....and I'm back to the begining.....firefox still pops up the 'Open With' dialog. :(

---

### Post by GrumpySimon on 2005-06-04
[QUOTE=Metz]Right....I've got localhost to respond again.

But to do so....I had to apt-get install apache.....not apt-get install apache2 ....:confused:

Now I'm going to return to the rest of it...and see if I can get any result on php. I've just tried the testphp.php file....and I'm back to the begining.....firefox still pops up the 'Open With' dialog. :([/QUOTE]
 The only error above is because the file isn't there - have a look for it, and change the path in the php4.load file to where the php4 module file is.

--Simon

---

### Post by Metz on 2005-06-05
This is what I have so far....

```

metz@prime-x:~$ locate libphp4.so
/usr/lib/apache2/modules/libphp4.so
metz@prime-x:~$

```

```

metz@prime-x:/etc/apache2/mods-available$ ls
actions.load      dav_fs.load      mem_cache.load      speling.load
asis.load         dav.load         mime_magic.conf     ssl.conf
auth_anon.load    deflate.load     mime_magic.load     ssl.load
auth_dbm.load     disk_cache.load  php4.conf           suexec.load
auth_digest.load  expires.load     php4.load           unique_id.load
auth_ldap.load    ext_filter.load  php4.load~          userdir.conf
cache.load        file_cache.load  proxy.conf          userdir.load
cern_meta.load    headers.load     proxy_connect.load  usertrack.load
cgid.conf         imap.load        proxy_ftp.load      vhost_alias.load
cgid.load         include.load     proxy_http.load
cgi.load          info.load        proxy.load
dav_fs.conf       ldap.load        rewrite.load

```

```

metz@prime-x:/etc/apache2/mods-available$ more php4.load
LoadModule mod_php /usr/lib/apache2/modules/libphp4.so
metz@prime-x:/etc/apache2/mods-available$

```

```

metz@prime-x:/etc/apache2/mods-available$ more php4.conf
<IfModule mod_php4.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
metz@prime-x:/etc/apache2/mods-available$

```

```

metz@prime-x:/etc/apache2$ ls mods-enabled
cgi.load  php4.conf  php4.load  rewrite.load  userdir.conf  userdir.load
metz@prime-x:/etc/apache2$

```

I'm still trying to figure out what the problem is.....

Go into firefox....url localhost...and I get my default index.html....no problem.

If I then goto [http://localhost/testphp.php](http://localhost/testphp.php).... I still just get the Open Dialog.... :(:( ...as shown below.

---

### Post by Metz on 2005-06-05
I'm begining to beleive this is a problem to do with which version of apache is running....

It would appear the apachectl is what is working.......because if I run "/usr/sbin/apachectl stop", it tells me, quite correctly that httpd has been stopped.

however, if I try to start "/usr/sbin/apache2ctl start", it says....

```

root@prime-x:/etc/apache2 # /usr/sbin/apache2ctl start
Syntax error on line 1 of /etc/apache2/mods-enabled/php4.load:
Can't locate API module structure `mod_php' in file /usr/lib/apache2/modules/libphp4.so: /usr/lib/libapr-0.so.0: undefined symbol: mod_php
root@prime-x:/etc/apache2 #

```



Any more clues as to where to look guys ?? I really really appreciate all the help :):)...I'm reading books, sites...anything I can to try to learn...but at the moment it's proving quite frustrating....:(

---

### Post by Metz on 2005-06-05
WooHoo !! Got it working.... :)

The problem appears to be (as suspected above) that I'm actually running apache 1.3...when what I really want to be running is apache2.

So I focused on getting apache2 running. I stopped the apache server with "/usr/sbin/apachectl stop" and attempted to restart with "/usr/sbin/apache2ctl start" and kept getting the error above.

It seems that this was caused because the loaded module is infact "php4_module" not "mod_php" as specified all over the place. A little editing of httpd and php4.conf saw to that...and bingo !!! I can now start with apache2ctl.

However, it warns me that "php4_module is already loaded...skipping" everytime.

This is because everytime I restart my machine...it's automatically starting apache 1.3....any ideas how I fix that ?! :)

---

### Post by GrumpySimon on 2005-06-05
Excellent :)

The php4_module already loaded error, means quite simply that you've got that LoadModule php4_module twice in the config files. Remove one of them and it goes away.

Now, for automatic startup:
Look inside /etc/rcX.d for SYYapache (where X is probably '3' and YY is probably '99', could also be SYYapachectl) and delete it. Also remove any KYYapache ot KYYapachectl.

This should stop apache1 starting.

To get apache2 to start, look inside /etc/init.d for apache2ctl. If it's not there copy it there: 
```

sudo cp /usr/sbin/apache2ctl /etc/init.d

```
Now: create a link from the apache2ctl into the rcX.d directory that the old apachectl script was in:
```

sudo ln -s /etc/init.d/apache2ctl /etc/rcX.d/S99apache
sudo ln -s /etc/init.d/apache2ctl /etc/rcX.d/K99apache

```

--Simon

---

