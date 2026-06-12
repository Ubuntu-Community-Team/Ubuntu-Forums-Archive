---
title: "Problem on reboot or shutdown PC"
date: 2018-06-26
forum: General Help
---

### Post by satimis on 2018-06-26
Hi all,

Ubuntu 16.04 desktop (Host)
Oracle VirtualBox

Occasionally I encountered following problem on reboot or shutdown PC.

Remark: VirtualBox was not running

Warning:```

QXcbConnection: Qt Fatal could not connect to display.  rc.local Aborted core dump

```

Either I have to press the "reset' key to reboot or to switch off the PC.  But there is no problem on next re-starting the computer.

I have searched a while and could not find a thread relevant to my case.  Please help.

Thanks

Regards
satimis

---

### Post by TheFu on 2018-06-26
Perhaps if you posted your rc.local and looked at the logfiles for errors?

---

### Post by satimis on 2018-06-26
> **TheFu said:**
> Perhaps if you posted your rc.local and looked at the logfiles for errors?
Hi,

&#10219; cat /etc/rc.local```

.....
virtualbox startvm;
VBoxHeadless -s "pfSense"

exit 0

```

Which logfile shall I check?  There are many of them on /var/log/

Thanks

Regards
satimis

---

### Post by TheFu on 2018-06-27
You cannot run any GUI programs inside rc.local. 
You should be using 
```
VBoxManage startvm "VM name" --type headless
```


You should check all the log files. Look for warnings and errors.  I'd use **egrep** to find those quickly.

---

### Post by satimis on 2018-06-28
> **TheFu said:**
> You cannot run any GUI programs inside rc.local. 
You should be using 
```
VBoxManage startvm "VM name" --type headless
```

You should check all the log files. Look for warnings and errors.  I'd use **egrep** to find those quickly.
Hi,

To check all log files. one by one?  There are many of them.

&#10219; ls /var/log/```

alternatives.log        dmesg.0                   pm-powersave.log.2.gz
alternatives.log.1      dmesg.1.gz                pm-powersave.log.3.gz
alternatives.log.10.gz  dmesg.2.gz                pm-powersave.log.4.gz
alternatives.log.11.gz  dmesg.3.gz                pm-suspend.log
alternatives.log.12.gz  dmesg.4.gz                pm-suspend.log.1
alternatives.log.2.gz   dpkg.log                  pm-suspend.log.2.gz
alternatives.log.3.gz   dpkg.log.1                pm-suspend.log.3.gz
alternatives.log.4.gz   dpkg.log.10.gz            pm-suspend.log.4.gz
alternatives.log.5.gz   dpkg.log.11.gz            prime-offload.log
alternatives.log.6.gz   dpkg.log.12.gz            prime-supported.log
alternatives.log.7.gz   dpkg.log.2.gz             samba
alternatives.log.8.gz   dpkg.log.3.gz             speech-dispatcher
alternatives.log.9.gz   dpkg.log.4.gz             syslog
apport.log              dpkg.log.5.gz             syslog.1
apport.log.1            dpkg.log.6.gz             syslog.2.gz
apport.log.2.gz         dpkg.log.7.gz             syslog.3.gz
apport.log.3.gz         dpkg.log.8.gz             syslog.4.gz
apport.log.4.gz         dpkg.log.9.gz             syslog.5.gz
apport.log.5.gz         faillog                   syslog.6.gz
apport.log.6.gz         fontconfig.log            syslog.7.gz
......

```

Besides on normal booting the problem mentioned never occurred.  It only happened on reboot or shutdown the PC occasionally.

Regards
satimis

---

### Post by kazakore on 2018-06-28
> **satimis said:**
> Hi,

To check all log files. one by one?  There are many of them.

&#10219; ls /var/log/```

alternatives.log        dmesg.0                   pm-powersave.log.2.gz
alternatives.log.1      dmesg.1.gz                pm-powersave.log.3.gz
alternatives.log.10.gz  dmesg.2.gz                pm-powersave.log.4.gz
alternatives.log.11.gz  dmesg.3.gz                pm-suspend.log
alternatives.log.12.gz  dmesg.4.gz                pm-suspend.log.1
alternatives.log.2.gz   dpkg.log                  pm-suspend.log.2.gz
alternatives.log.3.gz   dpkg.log.1                pm-suspend.log.3.gz
alternatives.log.4.gz   dpkg.log.10.gz            pm-suspend.log.4.gz
alternatives.log.5.gz   dpkg.log.11.gz            prime-offload.log
alternatives.log.6.gz   dpkg.log.12.gz            prime-supported.log
alternatives.log.7.gz   dpkg.log.2.gz             samba
alternatives.log.8.gz   dpkg.log.3.gz             speech-dispatcher
alternatives.log.9.gz   dpkg.log.4.gz             syslog
apport.log              dpkg.log.5.gz             syslog.1
apport.log.1            dpkg.log.6.gz             syslog.2.gz
apport.log.2.gz         dpkg.log.7.gz             syslog.3.gz
apport.log.3.gz         dpkg.log.8.gz             syslog.4.gz
apport.log.4.gz         dpkg.log.9.gz             syslog.5.gz
apport.log.5.gz         faillog                   syslog.6.gz
apport.log.6.gz         fontconfig.log            syslog.7.gz
......

```




As already stated use grep or similar to search the contents of all the files at once for you!

[https://linuxacademy.com/blog/linux/grep-tutorial-searching-file-contents/](https://linuxacademy.com/blog/linux/grep-tutorial-searching-file-contents/)

---

### Post by TheFu on 2018-06-28
Simple file "globbing" using easy regex patterns is one of the most powerful capabilities on Unix.  
[https://help.ubuntu.com/community/ShellGlobbing](https://help.ubuntu.com/community/ShellGlobbing)
[https://www.linuxjournal.com/content/bash-extended-globbing](https://www.linuxjournal.com/content/bash-extended-globbing)

BTW, you almost never need the '.' in any globbing.   ***jpg** and ***.jpg** are effectively the same. The '.' matching any-single-character, while * matches all characters.   In Windows, we see *.* as a pattern, but that isn't needed on Unix. ***** matches all files that don't begin with a . (period).  So I'd use **/var/log/*g** to glob lo**g** files in that path. We can also glob with '*' matching surrounded by other characters  So ***conf*g **is a valid pattern.

Linux doesn't care about "extensions"- the OS doesn't use them.  Extensions are handy for humans and some GUI programs, but pretty much everything else uses the "magic number" in the file header to determine a file type.   The 'file' command uses that as well, not an extension. [https://linux.die.net/man/1/file](https://linux.die.net/man/1/file)  Sorry, that's OT stuff.

Looking at compressed logs usually isn't necessary because bad things tend to happen in every log when there is an issue, but you can use gunzip -c as a "filter" when that is needed.** gunzip -c /var/log/*gz | egrep -i 'warn|err' | more** for example.

I teach both of these concepts in my first 2 classes on Linux since they save so much time.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) teaches this stuff in a clear way, I've found.

Globbing is a powerful skill to have and master.

BTW, we all have gaps in our knowledge.  I learned most of this stuff watching other people on my team at work and then later reading Unix admin/power user books which solidified the understanding.

---

### Post by satimis on 2018-06-28
Hi TheFu,

Thanks for your links

> **TheFu said:**
>  - snip -
Looking at compressed logs usually isn't necessary because bad things tend to happen in every log when there is an issue, but you can use gunzip -c as a "filter" when that is needed.** gunzip -c /var/log/*gz | egrep -i 'warn|err' | more** for example.
- snip 
&#10219; gunzip -c /var/log/*gz | egrep -i 'warn' | more```

Binary file (standard input) matches

```

&#10219; gunzip -c /var/log/*gz | egrep -i 'QXcbConnection' | more```

Binary file (standard input) matches

```

&#10219; gunzip -c /var/log/*gz | egrep -i 'Qt|fatal' | more```

Binary file (standard input) matches

```

&#10219; gunzip -c /var/log/*gz | egrep -i 'dump' | more```

update-alternatives 2017-01-22 13:02:53: run with --force --install /etc/ld.so.c
onf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/nvidia-340/ld.s
o.conf 8604 --slave /usr/share/man/man1/nvidia-xconfig.1.gz x86_64-linux-gnu_man
_nvidiaxconfig.gz /usr/share/man/man1/alt-nvidia-340-xconfig.1.gz --slave /usr/s
hare/man/man1/nvidia-smi.1.gz x86_64-linux-gnu_nvidia-smi.1.gz /usr/share/man/ma
n1/alt-nvidia-340-smi.1.gz --slave /usr/share/man/man1/nvidia-cuda-mps-control.1
.gz x86_64-linux-gnu_nvidia-cuda-mps-control.1.gz /usr/share/man/man1/alt-nvidia
-340-cuda-mps-control.1.gz --slave /usr/share/man/man1/nvidia-persistenced.1.gz 
x86_64-linux-gnu_man_persistenced.gz /usr/share/man/man1/alt-nvidia-340-persiste
nced.1.gz --slave /usr/bin/nvidia-smi x86_64-linux-gnu_nvidia_smi /usr/lib/nvidi
......

```
Large output

&#10219; gunzip -c /var/log/*gz | egrep -i 'Aborted|core|dump' | more```

update-alternatives 2017-01-22 13:02:53: run with --force --install /etc/ld.so.c
onf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/nvidia-340/ld.s
o.conf 8604 --slave /usr/share/man/man1/nvidia-xconfig.1.gz x86_64-linux-gnu_man
_nvidiaxconfig.gz /usr/share/man/man1/alt-nvidia-340-xconfig.1.gz --slave /usr/s
hare/man/man1/nvidia-smi.1.gz x86_64-linux-gnu_nvidia-smi.1.gz /usr/share/man/ma
n1/alt-nvidia-340-smi.1.gz --slave /usr/share/man/man1/nvidia-cuda-mps-control.1
.gz x86_64-linux-gnu_nvidia-cuda-mps-control.1.gz /usr/share/man/man1/alt-nvidia
-340-cuda-mps-control.1.gz --slave /usr/share/man/man1/nvidia-persistenced.1.gz 
x86_64-linux-gnu_man_persistenced.gz /usr/share/man/man1/alt-nvidia-340-persiste
nced.1.gz --slave /usr/bin/nvidia-smi x86_64-linux-gnu_nvidia_smi /usr/lib/nvidi
a-340/bin/nvidia-smi --slave /usr/bin/nvidia-xconfig x86_64-linux-gnu_nvidia_xco
nfig /usr/lib/nvidia-340/bin/nvidia-xconfig --slave /usr/bin/nvidia-bug-report.s
h x86_64-linux-gnu_nvidia_bug_report /usr/lib/nvidia-340/bin/nvidia-bug-report.s
....
....

```
Also large output

Regards
satimis

---

### Post by TheFu on 2018-06-28
> Looking at compressed logs usually isn't necessary
The egrep just finds the files you need to look at in more detail.

But back to the original issue - did you even try to use the **VBoxManage startvm "VM name" --type headless ** command?  The original error is what happens whenever a GUI app tries to run and there isn't any X/session available for a connection. There are other reasons too, but at boot, with what you are doing in rc.local, that is the most likely issue.

---

### Post by satimis on 2018-06-29
> **TheFu said:**
> The egrep just finds the files you need to look at in more detail.

&#10219; gunzip -c /var/log/*gz | egrep -i 'Aborted|core|dump' | grep .gz```

update-alternatives 2017-01-22 13:02:53: run with --force --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/nvidia-340/ld.so.conf 8604 --slave /usr/share/man/man1/nvidia-xconfig.1.gz x86_64-linux-gnu_man_nvidiaxconfig.gz /usr/share/man/man1/alt-nvidia-340-xconfig.1.gz --slave /usr/share/man/man1/nvidia-smi.1.gz x86_64-linux-gnu_nvidia-smi.1.gz /usr/share/man/man1/alt-nvidia-340-smi.1.gz --slave /usr/share/man/man1/nvidia-cuda-mps-control.1.gz x86_64-linux-gnu_nvidia-cuda-mps-control.1.gz /usr/share/man/man1/alt-nvidia-340-cuda-mps-control.1.gz --slave /usr/share/man/man1/nvidia-persistenced.1.gz x86_64-linux-gnu_man_persistenced.gz /usr/share/man/man1/alt-nvidia-340-persistenced.1.gz --slave /usr/bin/nvidia-smi x86_64-linux-gnu_nvidia_smi /usr/lib/nvidia-340/bin/nvidia-smi --slave /usr/bin/nvidia-xconfig x86_64-linux-gnu_nvidia_xconfig /usr/lib/nvidia-340/bin/nvidia-xconfig --slave /usr/bin/nvidia-bug-report.sh x86_64-linux-gnu_nvidia_bug_report /usr/lib/nvidia-340/bin/nvidia-bug-report.s
......

```

&#10219; gunzip -c /var/log/*gz | egrep -i 'dump' | grep .gz | grep var
No output

&#10219; gunzip -c /var/log/*gz | egrep -i 'dump' | grep .gz | grep log
No output

&#10219; gunzip -c /var/log/*gz | egrep -i 'dump' | grep .gz | grep usr```

update-alternatives 2017-01-22 13:02:53: run with --force --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/nvidia-340/ld.so.conf 8604 --slave /usr/share/man/man1/nvidia-xconfig.1.gz x86_64-linux-gnu_man_nvidiaxconfig.gz /usr/share/man/man1/alt-nvidia-340-xconfig.1.gz --slave /usr/share/man/man1/nvidia-smi.1.gz x86_64-linux-gnu_nvidia-smi.1.gz /usr/share/man/man1/alt-nvidia-340-smi.1.gz --slave /usr/share/man/man1/nvidia-cuda-mps-control.1.gz x86_64-linux-gnu_nvidia-cuda-mps-control.1.gz /usr/share/man/man1/alt-nvidia-340-cuda-mps-control.1.gz --slave /usr/share/man/man1/nvidia-persistenced.1.gz x86_64-linux-gnu_man_persistenced.gz /usr/share/man/man1/alt-nvidia-340-persistenced.1.gz --slave /usr/bin/nvidia-smi x86_64-linux-gnu_nvidia_smi /usr/lib/nvidia-340/bin/nvidia-smi --slave /usr/bin/nvidia-xconfig x86_64-linux-gnu_nvidia_xconfig /usr/lib/nvidia-340/bin/nvidia-xconfig --slave /usr/bin/nvidia-bug-report.sh x86_64-linux-gnu_nvidia_bug_report /usr/lib/nvidia-340/bin/nvidia-bug-report.sh --slave /usr/bin/nvidia-debugdump x86_64-linux-gnu_nvidia-debugdump /usr/lib/nvidia-340/bin/nvidia-debugdump --slave /usr/bin/nvidia-cuda-mps-control x86_64-linux-gnu_nvidia-cuda-mps-control /usr/lib/nvidia-340/bin/nvidia-cuda-mps-control
....

```

The .gz file is NOT on /var/log/

> 
But back to the original issue - did you even try to use the **VBoxManage startvm "VM name" --type headless ** command?  The original error is what happens whenever a GUI app tries to run and there isn't any X/session available for a connection. There are other reasons too, but at boot, with what you are doing in rc.local, that is the most likely issue.
Not yet.  

Since posting and up-to-now there is no such a problem happened neither on 'reboot' nor on 'shutdown'.  Such a problem only happened in rare occasion and I could'not predict when it'll happen.  VirtualBox manager was not running.

Also there is no problem on booting PC each day.

Regards
satimis

---

### Post by TheFu on 2018-06-29
I have no idea what the last set of commands is trying to accomplish. Maybe I'm just stupid.

Could the original problem happen only when you reboot and don't login immediately?  That would be my expectation.

---

### Post by satimis on 2018-06-29
> **TheFu said:**
> 
Could the original problem happen only when you reboot and don't login immediately?  That would be my expectation.
1) Problem on reboot
IIRC It happened twice when after running update and upgrade and I have to reboot PC

2) Problem on shutdown
IIRC It happened when I ran "systemctl poweroff" in twice or three occasions.

However it is NOT always happened.  Since my posting until now it has not happened again.

Could you please give me a suggestion, if possible?  What/Where I have to check if the mentioned problem reoccurs?  Thanks

satimis

---

### Post by TheFu on 2018-06-29
If it isn't reproducible,  the updates probably fixed it.
For any errors, check the system logs.

---

### Post by satimis on 2018-06-29
> **TheFu said:**
> If it isn't reproducible,  the updates probably fixed it.
For any errors, check the system logs.
Thanks

satimis

---

### Post by satimis on 2018-06-30
Hi TheFu,

The problem re-occured about 2 hrs ago on normal shutdown the PC by clicking the icon on the right corner of the top menu.  I left the warning hanging and about 30 sec the PC shutdown automatically.

$ tail /var/log/syslog.1 ```

Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Stopped Make remote CUPS printers available locally.
Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Stopping CUPS Scheduler...
Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Stopped CUPS Scheduler.
Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Stopped CUPS Scheduler.
Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Stopping CUPS Scheduler.
Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Started CUPS Scheduler.
Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Started CUPS Scheduler.
Jun 30 09:46:00 ub1604ssd1tb systemd[1]: Started Make remote CUPS printers available locally.
Jun 30 09:46:00 ub1604ssd1tb colord[1215]: (colord:1215): Cd-WARNING **: failed to get session [pid 4936]: No such device or address
Jun 30 09:46:00 ub1604ssd1tb rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1097" x-info="http://www.rsyslog.com"] rsyslogd was HUPed

```

I have no printer connected to the PC.

&#10219; tail /var/log/syslog```

Jun 30 22:13:25 ub1604ssd1tb gnome-session[2170]:     r = adapter.send(request, **kwargs)
Jun 30 22:13:25 ub1604ssd1tb gnome-session[2170]:   File "/usr/lib/python2.7/dist-packages/requests/adapters.py", line 437, in send
Jun 30 22:13:25 ub1604ssd1tb gnome-session[2170]:     raise ConnectionError(e, request=request)
Jun 30 22:13:25 ub1604ssd1tb gnome-session[2170]: ConnectionError: HTTPSConnectionPool(host='vrty.org', port=443): Max retries exceeded with url: /api/stats/56761ju92s/report-config (Caused by NewConnectionError('<requests.packages.urllib3.connection.VerifiedHTTPSConnection object at 0x7f75ff76d6d0>: Failed to establish a new connection: [Errno 110] Connection timed out',))
Jun 30 22:15:43 ub1604ssd1tb gnome-session[2170]: INFO: 2018-06-30 22:15:43,482: regular_change_thread() 'regular_change changes wallpaper'
Jun 30 22:15:43 ub1604ssd1tb gnome-session[2170]: INFO: 2018-06-30 22:15:43,483: set_wallpaper() 'Calling set_wallpaper with /home/satimis/.config/variety/Downloaded/mediarss_vrty_org_rss/rockmap.1920x1200.jpg'
Jun 30 22:15:43 ub1604ssd1tb gnome-session[2170]: INFO: 2018-06-30 22:15:43,483: prepare_thread() 'Prepared buffer contains 45 images'
Jun 30 22:15:43 ub1604ssd1tb gnome-session[2170]: INFO: 2018-06-30 22:15:43,485: do_set_wp() 'Calling do_set_wp with /home/satimis/.config/variety/Downloaded/mediarss_vrty_org_rss/rockmap.1920x1200.jpg, time: 1530368143.49'
Jun 30 22:15:43 ub1604ssd1tb gnome-session[2170]: INFO: 2018-06-30 22:15:43,504: update_indicator() 'Setting file info to: /home/satimis/.config/variety/Downloaded/mediarss_vrty_org_rss/rockmap.1920x1200.jpg'
Jun 30 22:17:01 ub1604ssd1tb CRON[14492]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

Regards
satimis

---

