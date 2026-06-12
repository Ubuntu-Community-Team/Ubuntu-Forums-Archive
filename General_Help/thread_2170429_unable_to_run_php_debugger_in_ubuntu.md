---
title: "unable to run php debugger in ubuntu"
date: 2013-08-26
forum: General Help
---

### Post by anzeige12 on 2013-08-26
Hallo,

I'm not sure if my threat is in the wright place. I saw that there is a  forum room Development & Programming at ubuntuforums.org, but I  think it is only for programmers of ubuntu programs. I only want to  debug a mediawiki extension which works fine for mediawiki 1.16.5 but  not for 1.20.6

But my problem is that I am not able to run any debugger for php. I have  found a lot of debugger tutorials for Java but for php it seems to be  much more difficult. 

The best way would be to configure my Eclipse so that it can debug the  php code (I tried sublime text 2 also but got the same problems). I  installed xdebug and zend as Eclipse extensions (but to be honest: I  don't know if they are both needed or only one of those). But when I'm  setting breakpoints and do the debug function it only runs through the  code without stopping at the breakpoints. Additionally it does not stop  at first line I marked this option in the debug settings. (On the other  hand the Java debugging works fine). I tried it for different Eclipse  versions (Indigo, Kepler and even Zend Eclipse) but it was the same for  every configuration. 

I read that the php.ini file (which I have as /etc/php5/apache2/php.ini  and /etc/php5/cli/php.ini -> don't know which one to edit so I edit  both) is important for debugging. In a forum I read the hint to fill in  the following code into the php.ini (see [http://www.eclipse.org/forums/index.php/t/173287/](http://www.eclipse.org/forums/index.php/t/173287/) ):

```

xdebug.remote_autostart=off
;extension=xdebug.so <-- is this needed?
zend_extension= /Applications/MAMP/bin/php5.3/lib/php/extensions/no-debug-no n-zts-20090626/xdebug.so "
xdebug.remote_enable=On
xdebug.remote_autostart=off
xdebug.remote_handler=dbgp
xdebug.remote_mode=req
xdebug.remote_host=localhost                         ;127.0.0.1
xdebug.remote_port=9000
xdebug.idekey=

```

Because I had no MAMP installation I was wondering how to set the  zend_extension variable. I installed zend again following this link [http://ncona.com/2012/09/debugging-php-code-with-xdebug/](http://ncona.com/2012/09/debugging-php-code-with-xdebug/) where the installation via

```

sudo apt-get install php5-xdebug 
```

is discribed which installs xdebug (and so it does for zend?). The  console told me that I can find under /etc/php5/conf.d/xdebug.ini. In  this file I had only one entry 

```
 zend_extension=/usr/lib/php5/20090626+lfs/xdebug.so 
```

so I thought this could be the right file for the zend_extension  variable in my php.ini file(s) so I filled that in there. Unfortunately  the Eclipse debuggers still don't work. 

I don't have to use Eclipse (but it would be nice if I could). Does  anyone know why this doesn't work in Eclipse or knows a step-by-step  tutorial to use another IDE or something?

---

### Post by VMC on 2013-08-26
Sorry, but I have no knowledge of php programming, but you might want to have a mod change the topic title to reflect **php** and not **pdf**. 
Someone with php  knowledge would pass this by.

---

### Post by anzeige12 on 2013-08-26
Thank you for the hint. I reported the mistake at "Report Post".

---

### Post by SeijiSensei on 2013-08-26
I don't know why you would need to use a dedicated debugger for PHP scripts.  When run as an Apache module, PHP writes errors to /var/log/apache2/error.log.  You can also configure the destination for errors in php.ini.

I've been writing in PHP for over a decade and find the easiest method is to use "tail -f /var/log/apache2/error.log" in a terminal window and watch to see what happens when I open the page.  But then I avoid using programs like Eclipse and simply enter scripts directly into a text editor like jed or emacs.  I've written thousands of lines of PHP code using this method.

---

### Post by anzeige12 on 2013-08-26
This log file only reports the errors? So I am not able to watch what happens to the variables when I run through the code line by line or to the next breakpoint (the breakpoints can easily be set or deleted; easier than inserting an own message which reports the values of my variables after every "interesting" step)?

An IDE can also jump into the functions and out of them. When I have a stack of 15 php files which are nested this could be easier. What do you think?

If it is so easy to work without IDE why do a lot of programmers (especially in the case of Java) use those debugging tools?
It need not to be a big IDE like Eclipse but a possibility to use it in sublime text 2 would be great. There is a programmer ( [Stuart Herbert]("http://www.youtube.com/user/stuherbertvids?feature=watch") ) which explains in a lot of videos why he uses sublime text 2 for debugging in php and how to configure the editor skins etc (that they look beautiful) but I haven't seen one of those videos with a hello world example how to use it. But perhaps I have missed it!?

---

### Post by dragonfly41 on 2013-08-26
I've just posted on another topic and noticed your post.

Running localhost/phpinfo.php

```

<?php phpinfo(); ?>

```

in the phpinfo dump is XDebug enabled?

For comparison .. this is my xdebug setting in my php.ini which is in /etc/php5/apache2/php.ini

; ========= xdebug =========

zend_extension="/usr/lib/php5/20090626+lfs/xdebug.so"
xdebug.remote_enable=1
xdebug.remote_host=localhost
xdebug.remote_port=9000
xdebug.remote_mode=req
xdebug.remote_handler=dbgp 
xdebug.remote_log="/home/dl/xdebug/log"
xdebug.show_exception_trace=0
xdebug.show_local_vars=9
xdebug.show_mem_delta=0
xdebug.trace_format=0
xdebug.trace_html=1
xdebug.auto_trace=1 
xdebug.profiler_enable=1
xdebug.profiler_output_name = "callgrind.out.%R"
xdebug.profiler_output_dir="/home/dl/xdebug/cachegrind_output"


You can install Kcachegrind to read the xdebug dumps. 

Regarding IDE's / editors .. currently I use Komodo Free Editor (not the IDE which is not free).

Alternatively Aptana Studio 3 is nice for PHP development.

---

### Post by anzeige12 on 2013-08-26
```

**xdebug**

 [TABLE="width: 600"]
[TR="class: h"]
[TH]xdebug support[/TH]
[TH]enabled[/TH]
[/TR]
[TR]
[TD="class: e"]Version[/TD]
[TD="class: v"]2.2.3[/TD]
[/TR]
[TR]
[TD="class: e"]IDE Key[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[/TABLE]

[TABLE="width: 600"]
[TR="class: h"]
[TH]Supported protocols[/TH]
[TH]Revision[/TH]
[/TR]
[TR]
[TD="class: e"]DBGp - Common DeBuGger Protocol[/TD]
[TD="class: v"]$Revision: 1.145 $[/TD]
[/TR]
[/TABLE]

[TABLE="width: 600"]
[TR="class: h"]
[TH]Directive[/TH]
[TH]Local Value[/TH]
[TH]Master Value[/TH]
[/TR]
[TR]
[TD="class: e"]xdebug.auto_trace[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.cli_color[/TD]
[TD="class: v"]0[/TD]
[TD="class: v"]0[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.collect_assignments[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.collect_includes[/TD]
[TD="class: v"]On[/TD]
[TD="class: v"]On[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.collect_params[/TD]
[TD="class: v"]0[/TD]
[TD="class: v"]0[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.collect_return[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.collect_vars[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.coverage_enable[/TD]
[TD="class: v"]On[/TD]
[TD="class: v"]On[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.default_enable[/TD]
[TD="class: v"]On[/TD]
[TD="class: v"]On[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.COOKIE[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.ENV[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.FILES[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.GET[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.POST[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.REQUEST[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.SERVER[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump.SESSION[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump_globals[/TD]
[TD="class: v"]On[/TD]
[TD="class: v"]On[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump_once[/TD]
[TD="class: v"]On[/TD]
[TD="class: v"]On[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.dump_undefined[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.extended_info[/TD]
[TD="class: v"]On[/TD]
[TD="class: v"]On[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.file_link_format[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.idekey[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.max_nesting_level[/TD]
[TD="class: v"]100[/TD]
[TD="class: v"]100[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.overload_var_dump[/TD]
[TD="class: v"]On[/TD]
[TD="class: v"]On[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.profiler_aggregate[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.profiler_append[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.profiler_enable[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.profiler_enable_trigger[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.profiler_output_dir[/TD]
[TD="class: v"]/tmp[/TD]
[TD="class: v"]/tmp[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.profiler_output_name[/TD]
[TD="class: v"]cachegrind.out.%p[/TD]
[TD="class: v"]cachegrind.out.%p[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_autostart[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_connect_back[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_cookie_expire_time[/TD]
[TD="class: v"]3600[/TD]
[TD="class: v"]3600[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_enable[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_handler[/TD]
[TD="class: v"]dbgp[/TD]
[TD="class: v"]dbgp[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_host[/TD]
[TD="class: v"]localhost[/TD]
[TD="class: v"]localhost[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_log[/TD]
[TD="class: v"]*no value*[/TD]
[TD="class: v"]*no value*[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_mode[/TD]
[TD="class: v"]req[/TD]
[TD="class: v"]req[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.remote_port[/TD]
[TD="class: v"]9000[/TD]
[TD="class: v"]9000[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.scream[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.show_exception_trace[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.show_local_vars[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.show_mem_delta[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.trace_enable_trigger[/TD]
[TD="class: v"]Off[/TD]
[TD="class: v"]Off[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.trace_format[/TD]
[TD="class: v"]0[/TD]
[TD="class: v"]0[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.trace_options[/TD]
[TD="class: v"]0[/TD]
[TD="class: v"]0[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.trace_output_dir[/TD]
[TD="class: v"]/tmp[/TD]
[TD="class: v"]/tmp[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.trace_output_name[/TD]
[TD="class: v"]trace.%c[/TD]
[TD="class: v"]trace.%c[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.var_display_max_children[/TD]
[TD="class: v"]128[/TD]
[TD="class: v"]128[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.var_display_max_data[/TD]
[TD="class: v"]512[/TD]
[TD="class: v"]512[/TD]
[/TR]
[TR]
[TD="class: e"]xdebug.var_display_max_depth[/TD]
[TD="class: v"]3[/TD]
[TD="class: v"]3[/TD]
[/TR]
[/TABLE]

```

---

### Post by dragonfly41 on 2013-08-26
XDebug does appear to be working .. here is a summary of settings to tweak
[URL="http://http://xdebug.org/docs/all_settings"]
http://xdebug.org/docs/all_settings[/URL]

I would install a cachegrind viewer.

---

### Post by SeijiSensei on 2013-08-26
> **anzeige12 said:**
> This log file only reports the errors? So I am not able to watch what happens to the variables when I run through the code line by line or to the next breakpoint (the breakpoints can easily be set or deleted; easier than inserting an own message which reports the values of my variables after every "interesting" step)?

I use a function I wrote to insert debugging entries like variable and array values.  I also have a stock footer that I use to dump the SESSION values at the bottom of the page.  I started using these tools long ago and never felt a need to use a more traditional debugger.

> An IDE can also jump into the functions and out of them. When I have a stack of 15 php files which are nested this could be easier. What do you think?

If it is so easy to work without IDE why do a lot of programmers (especially in the case of Java) use those debugging tools?

PHP scripting is a lot less complicated than writing in a language like C or Java.  When PHP throws an error it tells you the line number of the file where the error occurred.  That could well be in a file included in another file referenced from a top-level script.

I'm not a professional programmer by training, and I started using PHP back in version 2 or so when it was still largely the brainchild of [Rasmus Lersdorf]("http://en.wikipedia.org/wiki/Rasmus_Lerdorf").  If you are interested in professional tools for PHP development, you need to look into what is available from the [Zend Project]("http://www.zend.com/en/"), particularly [Zend Studio](http://www.zend.com/products/studio/).

---

### Post by anzeige12 on 2013-08-26
Of course I have heard about the Zend products. But they are perhaps to  expensive for me. But what I found is "JetBrains PHPStorm" where I am  using a free 30 days version. I will try that tomorrow and will look for  those things dragonfly41 told me. If this doesn't work I will try to  work without the traditional debuggers as you ([**[COLOR=#000000]SeijiSensei)[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") suggested.

---

### Post by dragonfly41 on 2013-08-27
Can I just add a additional reference to FirePHP

[http://www.firephp.org/](http://www.firephp.org/)

This requires FireBug to be installed to receive the FirePHP debug messages into console.

[https://addons.mozilla.org/en-US/firefox/addon/firebug/](https://addons.mozilla.org/en-US/firefox/addon/firebug/)

type "php" in the search field to see the various PHP development tools available.

...

Returning to the subject of development tools I'm still using Komodo (free) Editor for PHP coding and testing with the help of tools above ... but I'm now starting to learn Laravel framework (note: a steep learning curve).
[URL="http://laravel.com/"]
http://laravel.com/[/URL]

---

### Post by anzeige12 on 2013-08-27
Now I have a possible solution why it didn't work. As I read here: [http://www.jetbrains.com/phpstorm/webhelp/php-debugging-session.html](http://www.jetbrains.com/phpstorm/webhelp/php-debugging-session.html)
xdebug and zend can't be used together. Watch by <?php phpinfo(); ?> which is your loaded configuration file and comment out all your zend cases.

---

