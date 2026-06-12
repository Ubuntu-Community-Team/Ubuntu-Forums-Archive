---
title: "Libre Office Calc help"
date: 2015-10-21
forum: General Help
---

### Post by Fred T on 2015-10-21
Recently had a hard drive crash, am trying to get things working. Running Ubuntu 14.04 LTS. Current issue is with Libre Office 4.2. 

Initially my problem was that Libre Office Calc would not open, but would hang. Menu bar showed it in use and that the program had a file open (right clicking). I was able to start with  the terminal and a now-forgotten command.

Now I get this message:

[I]Either another instance of LibreOffice is accessing your personal settings or your personal settings are locked.
Simultaneous access can lead to inconsistencies in your personal settings. Before continuing, you should make sure user 'root' closes LibreOffice on host 'xxxxx'. Do you really want to continue?[/I]

I need help. I have forgotten everything I knew about Unix in the 80s, so I need to know what to type in. 
Many thanks for your assistance.

---

### Post by kurt18947 on 2015-10-22
You'll need to be able to view and close processes. I use Ubuntu Gnome and use "System Monitor" for this purpose. I sometimes see similar with Firefox, try to open Firefox and get a message there's already an instance of Firefox running. I close the 'invisible' Firefox instance and relaunch in the usual way and all is well.

---

### Post by SeijiSensei on 2015-10-22
Open a terminal and run the command "ps ax | grep calc".  You should see lines like this:
```

 1880 ?        Sl     0:01 /usr/lib/libreoffice/program/oosplash --calc
 1897 ?        Sl   101:48 /usr/lib/libreoffice/program/soffice.bin --calc --splash-pipe=5
 
```
Now enter the command
```

sudo kill -15 1897 1880

```
That tells the operating system to kill those two processes "gracefully."  You'll notice I entered the process IDs in reverse order since one may be spawned by the other.  Run "ps ax" again, and if you still see Calc running, reissue the kill command with "-9" rather than "-15".

I'm a lot more concerned about this message:
> Simultaneous access can lead to inconsistencies in your personal settings. Before continuing, you should make sure user 'root' closes LibreOffice on host 'xxxxx'. Do you really want to continue?

That indicates you, or someone else, is running LO as the root user.  That's a very bad idea.  You should only run applications like this with your own personal account.  If you are running as root because of problems with file permissions you should read this: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Another problem you might encounter is that the file is locked.  In the directory where the files are stored, issue the command "ls -ltra".  You might see something like this:
```
-rw-rw-r--  1 seiji  seiji    70 Aug 14 11:33 .~lock.somefile.ods#
```
Sometimes LO will leave stale lock files around after a crash.  You need to delete this as well with 
```
rm -f .~lock.dw-senate-114.ods#
```
This file is "hidden" because it starts with an initial dot.  The "-a" switch to the ls command lists hidden files as well as normal ones.

---

### Post by Fred T on 2015-10-22
> **SeijiSensei said:**
> Open a terminal and run the command "ps ax | grep calc".  You should see lines like this:
```

 1880 ?        Sl     0:01 /usr/lib/libreoffice/program/oosplash --calc
 1897 ?        Sl   101:48 /usr/lib/libreoffice/program/soffice.bin --calc --splash-pipe=5
 
```


Here is the response

```

ps ax | grep calc
 2377 pts/1    S+     0:00 grep --color=auto [COLOR=#ff0000]calc[/COLOR]

```

Locked files - I found none.

File permissions - I still don't have a good handle on this. It is possible that I have the same password for both root and user. Would changing the pw for either fix the problem?

---

### Post by vasa1 on 2015-10-22
> **Fred T said:**
> ...
File permissions - I still don't have a good handle on this. It is possible that I have the same password for both root and user. Would changing the pw for either fix the problem?

I think it would help you if you **clearly** answer seiji's question about whether you've been running applications as root. Is this a standalone device or are you sharing software over a network?

---

### Post by Fred T on 2015-10-22
> **vasa1 said:**
> I think it would help you if you **clearly** answer seiji's question about whether you've been running applications as root. Is this a standalone device or are you sharing software over a network?

It would help if I knew, too. I couldn't figure it out from the page provided. As for a network, my other computer is windows only, this one Ubuntu only. I use the windows to write files to at the end of the day. I don't share software between them.

---

### Post by vasa1 on 2015-10-22
> **Fred T said:**
> It would help if I knew, too. ...
In that case, you could post the output of **ps -eHF | grep calc** and, just in case, **ps -eHF | grep libre**:

```
07:32 AM ~ $ ps -eHF | grep calc
vasa1     2802  1467  0  4414  1188   1 07:31 ?        00:00:00         bash /home/vasa1/bin/scalc
vasa1     2803  2802  0 34179  3252   1 07:31 ?        00:00:00           /opt/libreoffice4.4/program/oosplash --calc
vasa1     2820  2803  1 265862 102576 0 07:31 ?        00:00:01             /opt/libreoffice4.4/program/soffice.bin --calc --splash-pipe=5
vasa1     2948  2931  0  4248   920   1 07:32 pts/1    00:00:00               grep --color=auto calc
07:32 AM ~ $ 
```
My path is different because I installed LibO from TDF and not from the repos.

---

### Post by Fred T on 2015-10-22
> **vasa1 said:**
> In that case, you could post the output of **ps -eHF | grep calc** and, just in case, **ps -eHF | grep libre**:



```
fred@basement:~$ ps -eHF | grep calc 
fred      3222  3192  0  3986  2196   5 21:28 pts/4    00:00:00             grep --color=auto calc
fred@basement:~$ ps -eHF | grep libre
fred      3226  3192  0  3986  2196   0 21:29 pts/4    00:00:00             grep --color=auto libre


```

---

### Post by vasa1 on 2015-10-23
Please also try ```
ps -eHF | grep -E 'UID|libre*'
```and make sure that LibreOffice Calc has been started.

I get```
11:34 AM ~ $ ps -eHF | grep -E 'UID|libre*'
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
vasa1     4153  4074  0  4248   920   0 11:34 pts/1    00:00:00               grep --color=auto -E UID|libre*
vasa1     4096  4095  0 34179  3252   1 11:32 ?        00:00:00           /opt/libreoffice4.4/program/oosplash --calc
vasa1     4113  4096  0 284267 102528 1 11:32 ?        00:00:01             /opt/libreoffice4.4/program/soffice.bin --calc --splash-pipe=5
11:34 AM ~ $ 
```where the UID column shows that I'm running Calc as user vasa1 and not as root.

---

### Post by Fred T on 2015-10-23
> **vasa1 said:**
> Please also try ```
ps -eHF | grep -E 'UID|libre*'
```and make sure that LibreOffice Calc has been started.

I get```
11:34 AM ~ $ ps -eHF | grep -E 'UID|libre*'
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
vasa1     4153  4074  0  4248   920   0 11:34 pts/1    00:00:00               grep --color=auto -E UID|libre*
vasa1     4096  4095  0 34179  3252   1 11:32 ?        00:00:00           /opt/libreoffice4.4/program/oosplash --calc
vasa1     4113  4096  0 284267 102528 1 11:32 ?        00:00:01             /opt/libreoffice4.4/program/soffice.bin --calc --splash-pipe=5
11:34 AM ~ $ 
```where the UID column shows that I'm running Calc as user vasa1 and not as root.

If you are asking me to start LibreOffice Calc before running the command, I can't get Calc to run without clicking yes in the warning message

[I]Either another instance of LibreOffice is accessing your personal settings or your personal settings are locked.
Simultaneous access can lead to inconsistencies in your personal  settings. Before continuing, you should make sure user 'root' closes  LibreOffice on host 'xxxxx'. Do you really want to continue?[/I]

At this point I don't know if I want to click yes.

---

### Post by vasa1 on 2015-10-23
> **Fred T said:**
> ...
At this point I don't know if I want to click yes.
It may not be necessary. Just run the command. If there's an instance running, it'll show up. If nothing shows up, that warning is probably meaningless. You may need to use a new profile; your old one (with your settings) maybe corrupted.

See [https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)

---

### Post by col48 on 2015-10-23
1. To see if LO is running:

If you have System Monitor (on my 12.04 it can be found under Applications > System Tools) choose the Processes tab and look for soffice.bin in the list of Process Names.  The user who owns the process is given. You may need to check these fields are ticked in Edit>Preferences and that View has All Processes selected.  if you are running Calc, the Command Line field will show the full path to LO then have calc as a parameter.  If you and root are both running LO, there will be two instances. (As an aside: if I open LO Calc and then LO Writer then close LO Calc, the instance of LO in System Monitor retains calc as the parameter)

2. If you have not been editing anything in LO (not just Calc), it is hard to see how you could damage anything important by killing stale lock files or by checking Yes on first opening LO.

3. In Unix, there was a distinct 'root' user.  In Ubuntu this is not so; the first user set up - ie you, for a single user machine - can exercise root privileges by preceding the relevant Terminal command by sudo (su or gksudo may do the same).  You will be prompted for your *usual* password if you have not used sudo within the last few minutes.  Trivial example, sudo cat foo prints to the terminal the file foo, whereas cat foo will only do this if you have read access.

4. Seiji has warned about running LO as root.  It's very risky to run as root any software which does not need to alter the system in some way (eg by upgrading the kernel).  It is all too easy to clobber accidentally something which may be difficult to recover.  If one of the files you created (so not a system file) has somehow got reassigned to another user like root, ponder how that might have happened (there may be a lesson to learn) and reassign its ownership to yourself - which would have to be done as root - before editing it as your normal user.

---

### Post by Fred T on 2015-10-23
> **col48 said:**
> 1. To see if LO is running:

If you have System Monitor (on my 12.04 it can be found under Applications > System Tools) choose the Processes tab and look for soffice.bin in the list of Process Names.  The user who owns the process is given. You may need to check these fields are ticked in Edit>Preferences and that View has All Processes selected.  if you are running Calc, the Command Line field will show the full path to LO then have calc as a parameter.  If you and root are both running LO, there will be two instances. (As an aside: if I open LO Calc and then LO Writer then close LO Calc, the instance of LO in System Monitor retains calc as the parameter)
I could not get the sys monitor to open from the desktop. It appears in the launcher, but doesn't open. Same as LO calc originally. 
> 
2. If you have not been editing anything in LO (not just Calc), it is hard to see how you could damage anything important by killing stale lock files or by checking Yes on first opening LO.
I did hit the yes button. LO works. I even rebooted and it still works.
> 
3. In Unix, there was a distinct 'root' user.  In Ubuntu this is not so; the first user set up - ie you, for a single user machine - can exercise root privileges by preceding the relevant Terminal command by sudo (su or gksudo may do the same).  You will be prompted for your *usual* password if you have not used sudo within the last few minutes.  Trivial example, sudo cat foo prints to the terminal the file foo, whereas cat foo will only do this if you have read access.
That helps some. We also had sys admin, admin & super. I was able to obtain all. Saved some service calls. But I digress...

I have executed the commands with LO Office & Calc. running:

```
 ps ax | grep calc
 2355 pts/0    S+     0:00 grep --color=auto calc

 ps -eHF | grep calc
fred      2357  2214  0  3986  2204   2 16:45 pts/0    00:00:00             grep --color=auto calc

 ps -eHF | grep libre
fred      1997  1164  0 52835  5600   4 16:39 ?        00:00:00         /usr/lib/libreoffice/program/oosplash --writer
fred      2030  1997  0 308910 128844 2 16:39 ?        00:00:01           /usr/lib/libreoffice/program/soffice.bin --writer --splash-pipe=5
fred      2359  2214  0  3986  2312   3 16:46 pts/0    00:00:00             grep --color=auto libre

ps -eHF | grep -E 'UID|libre*'
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
fred      1997  1164  0 52835  5600   4 16:39 ?        00:00:00         /usr/lib/libreoffice/program/oosplash --writer
fred      2030  1997  0 308910 130872 4 16:39 ?        00:00:01           /usr/lib/libreoffice/program/soffice.bin --writer --splash-pipe=5
fred      2386  2214  0  3986  2200   1 17:10 pts/0    00:00:00             grep --color=auto -E UID|libre*

```

Appears to me that all is well with LO. Now on to the problem with sys monitor.

[SIZE=3]**Thanks for all the help!**[/SIZE]

---

