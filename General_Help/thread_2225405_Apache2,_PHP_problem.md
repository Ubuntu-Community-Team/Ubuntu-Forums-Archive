---
title: "Apache2, PHP problem"
date: 2014-05-21
forum: General Help
---

### Post by peter104 on 2014-05-21
Hey guys,

I hope im posting in the correct part of the forum.

Im having a little problem with my webserver, it stops working from time to time.

This is what i see in /var/apache2/error.log```


[Sun May 18 06:41:56.139844 2014] [mpm_prefork:notice] [pid 1180] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Sun May 18 06:41:56.139893 2014] [core:notice] [pid 1180] AH00094: Command line: '/usr/sbin/apache2'
[Mon May 19 23:01:07.432463 2014] [mpm_prefork:error] [pid 1180] AH00161: server reached MaxRequestWorkers setting, consider raising the MaxRequestWorkers setting
[Wed May 21 08:37:56.348614 2014] [core:notice] [pid 1180] AH00052: child pid 6697 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.579226 2014] [core:notice] [pid 1180] AH00052: child pid 6585 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.602184 2014] [core:notice] [pid 1180] AH00052: child pid 6761 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.602289 2014] [core:notice] [pid 1180] AH00052: child pid 6746 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.602389 2014] [core:notice] [pid 1180] AH00052: child pid 7670 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.602482 2014] [core:notice] [pid 1180] AH00052: child pid 6772 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.602600 2014] [core:notice] [pid 1180] AH00052: child pid 6808 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.602710 2014] [core:notice] [pid 1180] AH00052: child pid 9354 exit signal Segmentation fault (11)
[Wed May 21 08:37:57.602823 2014] [core:notice] [pid 1180] AH00052: child pid 9014 exit signal Segmentation fault (11)
[Wed May 21 08:38:04.858533 2014] [core:error] [pid 1180] AH00046: child process 3808 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858541 2014] [core:error] [pid 1180] AH00046: child process 3870 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858549 2014] [core:error] [pid 1180] AH00046: child process 3531 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858557 2014] [core:error] [pid 1180] AH00046: child process 3907 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858632 2014] [core:notice] [pid 1180] AH00052: child pid 3922 exit signal Segmentation fault (11)
[Wed May 21 08:38:04.858641 2014] [core:error] [pid 1180] AH00046: child process 3926 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858649 2014] [core:error] [pid 1180] AH00046: child process 3947 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858824 2014] [core:error] [pid 1180] AH00046: child process 9400 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858832 2014] [core:error] [pid 1180] AH00046: child process 9401 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858841 2014] [core:error] [pid 1180] AH00046: child process 9430 still did not exit, sending a SIGKILL
[Wed May 21 08:38:04.858849 2014] [core:error] [pid 1180] AH00046: child process 9432 still did not exit, sending a SIGKILL
[Wed May 21 08:38:05.861136 2014] [core:notice] [pid 1180] AH00052: child pid 3828 exit signal Segmentation fault (11)
[Wed May 21 08:38:05.862296 2014] [core:notice] [pid 1180] AH00052: child pid 7587 exit signal Segmentation fault (11)
[Wed May 21 08:38:05.862368 2014] [core:notice] [pid 1180] AH00052: child pid 6718 exit signal Segmentation fault (11)
[Wed May 21 08:38:05.862641 2014] [core:notice] [pid 1180] AH00052: child pid 9400 exit signal Segmentation fault (11)
[Wed May 21 08:38:05.862865 2014] [core:notice] [pid 1180] AH00052: child pid 9432 exit signal Segmentation fault (11)
[Wed May 21 08:38:05.862989 2014] [mpm_prefork:notice] [pid 1180] AH00169: caught SIGTERM, shutting down
[Wed May 21 08:46:40.343301 2014] [mpm_prefork:notice] [pid 1167] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Wed May 21 08:46:40.362777 2014] [core:notice] [pid 1167] AH00094: Command line: '/usr/sbin/apache2'
[Wed May 21 09:48:47.859697 2014] [mpm_prefork:notice] [pid 1167] AH00169: caught SIGTERM, shutting down
[Wed May 21 09:57:39.577436 2014] [mpm_prefork:notice] [pid 1188] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Wed May 21 09:57:39.610659 2014] [core:notice] [pid 1188] AH00094: Command line: '/usr/sbin/apache2'

```
If any other info is needed, just let me know.

Any help to solve this would be greatly appreciated 


Server information:
```
user@vevs12:~$ apache2 -v
Server version: Apache/2.4.7 (Ubuntu)
Server built: Apr 3 2014 12:20:28
user@vevs12:~$ php -v
PHP 5.5.9-1ubuntu4 (cli) (built: Apr 9 2014 17:11:57)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.5.0, Copyright (c) 1998-2014 Zend Technologies
with Zend OPcache v7.0.3, Copyright (c) 1999-2014, by Zend Technologies
```

---

### Post by peter104 on 2014-05-26
Hello,

Am i in the wrong thread? No answers at all..

I did some troubleshooting and found gdb, so i did a backtrace with that after a crash.

Here's the output, hoping someone has some tips.
```

(gdb) attach 1536
Attaching to process 1536
Reading symbols from /bin/bash...(no debugging symbols found)...done.
Reading symbols from /lib/x86_64-linux-gnu/libtinfo.so.5...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libtinfo.so.5
Reading symbols from /lib/x86_64-linux-gnu/libdl.so.2...Reading symbols from /usr/lib/debug//lib/x86_64-linux-gnu/libdl-2.19.so...done.
done.
Loaded symbols for /lib/x86_64-linux-gnu/libdl.so.2
Reading symbols from /lib/x86_64-linux-gnu/libc.so.6...Reading symbols from /usr/lib/debug//lib/x86_64-linux-gnu/libc-2.19.so...done.
done.
Loaded symbols for /lib/x86_64-linux-gnu/libc.so.6
Reading symbols from /lib64/ld-linux-x86-64.so.2...Reading symbols from /usr/lib/debug//lib/x86_64-linux-gnu/ld-2.19.so...done.
done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnss_compat.so.2...Reading symbols from /usr/lib/debug//lib/x86_64-linux-gnu/libnss_compat-2.19.so...done.
done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_compat.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnsl.so.1...Reading symbols from /usr/lib/debug//lib/x86_64-linux-gnu/libnsl-2.19.so...done.
done.
Loaded symbols for /lib/x86_64-linux-gnu/libnsl.so.1
Reading symbols from /lib/x86_64-linux-gnu/libnss_nis.so.2...Reading symbols from /usr/lib/debug//lib/x86_64-linux-gnu/libnss_nis-2.19.so...done.
done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_nis.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnss_files.so.2...Reading symbols from /usr/lib/debug//lib/x86_64-linux-gnu/libnss_files-2.19.so...done.
done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_files.so.2
0x00007f97081a998c in __libc_waitpid (pid=-1, stat_loc=0x7fffd1c7ffb8, options=10) at ../sysdeps/unix/sysv/linux/waitpid.c:31
31      ../sysdeps/unix/sysv/linux/waitpid.c: No such file or directory.
(gdb) c
Continuing.
^C
Program received signal SIGINT, Interrupt.
0x00007f97081a998c in __libc_waitpid (pid=-1, stat_loc=0x7fffd1c7ffb8, options=10) at ../sysdeps/unix/sysv/linux/waitpid.c:31
31      in ../sysdeps/unix/sysv/linux/waitpid.c
(gdb) backtrace
#0  0x00007f97081a998c in __libc_waitpid (pid=-1, stat_loc=0x7fffd1c7ffb8, options=10) at ../sysdeps/unix/sysv/linux/waitpid.c:31
#1  0x0000000000445956 in ?? ()
#2  0x0000000000446c3b in wait_for ()
#3  0x00000000004377eb in execute_command_internal ()
#4  0x000000000043784e in execute_command ()
#5  0x00000000004211ee in reader_loop ()
#6  0x000000000041f729 in main ()
(gdb) backtrace full
#0  0x00007f97081a998c in __libc_waitpid (pid=-1, stat_loc=0x7fffd1c7ffb8, options=10) at ../sysdeps/unix/sysv/linux/waitpid.c:31
        resultvar = 18446744073709551104
        oldtype = 16336904
#1  0x0000000000445956 in ?? ()
No symbol table info available.
#2  0x0000000000446c3b in wait_for ()
No symbol table info available.
#3  0x00000000004377eb in execute_command_internal ()
No symbol table info available.
#4  0x000000000043784e in execute_command ()
No symbol table info available.
#5  0x00000000004211ee in reader_loop ()
No symbol table info available.
#6  0x000000000041f729 in main ()
No symbol table info available.
(gdb)
```


/Peter

---

### Post by SeijiSensei on 2014-05-26
As the error message says, you should raise the "MaxRequestWorkers" ceiling in /etc/apache2/mods-available/mpm_worker.conf, then restart Apache.  The default is 150 so maybe 250 or 500 will be better.

Yours must be a fairly busy site.  I never have to meddle with these settings on the sites I manage.

---

### Post by peter104 on 2014-05-26
Hi, and thanks for your reply and info on where to find that setting. But the thing is, its not a very busy site. Its only a company site. [www.valeng.com]("http://www.valeng.com")

These are the settings in mpm_worker.conf

<IfModule mpm_worker_module>
        StartServers                     2
        MinSpareThreads          25
        MaxSpareThreads          75
        ThreadLimit                      64
        ThreadsPerChild          25
        MaxRequestWorkers         150
        MaxConnectionsPerChild   0
</IfModule>


I will try to raise the "MaxRequestWorkers" and see what happens.

I think i know what caused this problem, This site was first installed on a Ubuntu 13.10. Then i upgraded it to 14.04, and the website stopped working, after a quick google search i found out that my Document root was wrong, it had changed to /var/www/html but the site was in /var/www so i changed the Document root back to /var/www in the 000-default.conf file.
But now im thinking that was not the best choice. I have no idea how to fix it tho. Or if im on the right track even. Could this be the problem?

---

### Post by SeijiSensei on 2014-05-27
I don't think so, though I'd suggest moving the site into /var/www/html so it will be compliant with future Ubuntu releases.

What do you see in /var/log/apache2/access.log?  Are you being hit with requests at a very high frequency?  Are there lots of little objects that are downloaded along with the main page(s)?  Figuring out the reason for the high demand is probably the only solution other than masking its symptoms with MaxRequestWorkers.

---

### Post by peter104 on 2014-05-27
Allright, i actually did move it to /var/www/html earlier today. I read what you said, "to be compliant with future releases"

I see quite alot in access.log 

Do you want me to paste a bit of it?

Im not sure how to determine if im being hit with a high frequency of requests. It looks like there is alot :)

Yeah, i would much prefer to figure out the reason rather then just meddle with MaxRequestWorkers.

Really appreciating your help btw.

Thanks
Pete

---

### Post by dragonfly41 on 2014-05-27
Could possibly be a DoS attack ...

Experiment with this module .. mod_qos
[http://opensource.adnovum.ch/mod_qos/](http://opensource.adnovum.ch/mod_qos/)

---

### Post by SeijiSensei on 2014-05-28
I'm wondering about denial of service as well.

Browse access.log and see if lots of requests originate from just a few IP addresses.  If so, you can reduce the problem considerably with a few iptables rules so that packets from those hosts get dropped at the doorstep and never reach Apache.

Another useful tool might be a web log summarizer like **analog** or **webalizer**.  Both of those are in the repositories.  They'll report the most frequent visitors to your site, so you can determine whether the high traffic sources are legitimate requests.

---

### Post by peter104 on 2014-06-03
Thanks guys, i'll try those tools. I know that moving the site files to /html shoulden't affect it. But since i moved the document root to /var/www/html the site has worked. 
I did check the apache log, and there is numerous connections from a ip series from russia. So it might very well be a denial of service. 
If the problem occurs again i will start adding addresses to deny in my firewall.

Thanks again
Pete

---

### Post by Jimit_Shah on 2015-01-02
Thank a lot.
I have configure typo7 . latest version of typo3 CMS and got this error in my screen.

==============================================================
Calculated absolute path to tslib directory does not exist.

Something in the main file, folder and link structure is wrong and must be fixed! A typical document root contains a couple of symbolic links:
* A symlink "typo3_src" pointing to the TYPO3 CMS core.
* A symlink "typo3" - the backend entry point - pointing to "typo3_src/typo3"
* A symlink "index.php" - the frontend entry point - points to "typo3_src/index.php"
==========================================================================================================================

After then I replace the value in /etc/apache2/mods-available/mpm_event.conf
-> maxRequestWorkers = 250 instead of 150.

It works Fine now. I hope I not found this error anymore. 
Thanks to this post. :p

---

