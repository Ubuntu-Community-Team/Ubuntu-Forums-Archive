---
title: "Can't remount /tmp to change privileges, 'mount -o remount,exec /tmp' fails"
date: 2019-06-21
forum: General Help
---

### Post by cmacgeox on 2019-06-21
Hello! I'm pretty new to Ubuntu and I'm struggling to change permissions for files in my /tmp folder. A process that worked on my Lubuntu system now fails on my new xps 13 with Ubuntu 18.04.

I'm attempting to build an R package and it requires a file be executable. When running a command in R I get the following error:

ERROR: 'configure' exists but is not executable -- see the 'R Installation and Administration Manual'
 removing ‘/tmp/RtmpZ3gvz6/devtools_install_84c7d0de9d3/spstan'

That's a well documented situation for R users. The /tmp/R... file isn't executable and the [common answer]("https://github.com/r-lib/devtools/issues/32") is to do the following:

[COLOR=#24292E][FONT=-apple-system]sudo mount -o remount,exec /tmp

[/FONT][/COLOR]This fails for me, returning:

mount: /tmp: mount point not mounted or bad option.

So I take it that either /tmp is not mounted or I'm giving it a bad option. I read the manual page and tried some other options (e.g. sudo mount -o remount /tmp) and get the same error. 

So I list out the mounted devices with 'mount' and I see these two among others:

tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1607052k,mode=755)
tmpfs on /run/user/1001 type tmpfs (rw,nosuid,nodev,relatime,size=1607048k,mode=700,uid=1001,gid=1001)

This doesn't help me much though, its now beyond my knowledge base. I don't know how tmpfs related to /tmp. I've spent/wasted hours trying to find an answer. Do I need to mount /tmp? If so, how? If not, what else should I try?

Thank you!

---

### Post by Impavidus on 2019-06-22
Sometimes /tmp is a separate filesystem in RAM. In that case it's a tempfs filesystem mounted at /tmp. It's volatile storage, so the contents are gone automatically when the system shuts down. Whether files can be executed depends not only on file permissions, but also on mount options.

On most Ubuntu systems /tmp is simply part of the root filesystem, so it's not mounted separately. It's not volatile storage, but with standard configuration all files in /tmp are deleted at boot time. You can change permissions of separate files using chmod. To add execute permission:```
chmod u+x filename
```

I don't know about your R problem.

---

### Post by cmacgeox on 2019-06-22
I think the problem here is that this R function I'm running creates a new file that it then tries to run, so there's no way for me to change permissions on the file. Even when setting permissions on contents of the folder recursively with 


```

chmod -R u+x ~/tmp

``` 


any new files are still not be executable, and the problem persists. 


It seems that this is what mount is good for. So I tried creating a new tmp folder and mounting it as tmpfs. After creating a new folder with ```
 mkdir /home/connor/Rtmp
``` I added this line to /etc/fstab:


```
tmpfs           /home/connor/Rtmp            tmpfs   exec,mode=777   0       0 
```


I rebooted and looked at the results which are ambiguous to me because mode=777 made it through but exec didn't:

```

 connor@xps:~$ mount | grep Rtmp
tmpfs on /home/connor/Rtmp type tmpfs (rw,relatime,mode=777)

```

I successfully changed the directory that the R session uses for temporary files (I created /home/connor/.Renviron and added a line with TMPDIR=/home/connor/Rtmp). I restarted the computer. Then opened R with sudo R, ran the compile_dll() line again and got the same error.


I can see in the error message that the files were being written to the new Rtmp folder as I wanted them to be, but it didn't solve the problem.

```

R>pkgbuild::compile_dll()
Re-compiling spstan
&#9472;  installing *source* package ‘spstan’ ...
   ** using staged installation
   ERROR: 'configure' exists but is not executable -- see the 'R Installation and Administration Manual'
&#9472;  removing ‘/home/connor/Rtmp/RtmpjHyMEM/devtools_install_b4a2034229b/spstan’
Error in (function (command = NULL, args = character(), error_on_status = TRUE,  : 
  System command error

```

I still think this is an OS problem rather than an R problem. Just to be clear I looked at the R Manual first, which just says: "[COLOR=#000000][FONT=&amp]Note that [/FONT][/COLOR]TMPDIR[COLOR=#000000][FONT=&amp] will be used to execute [/FONT][/COLOR]configure[COLOR=#000000][FONT=&amp] scripts when installing packages, so if [/FONT][/COLOR]/tmp[COLOR=#000000][FONT=&amp] has been mounted as `[/FONT][/COLOR]noexec[COLOR=#000000][FONT=&amp]', [/FONT][/COLOR]TMPDIR[COLOR=#000000][FONT=&amp] needs to be set to a directory from which execution is allowed." Sounds easy enough...[/FONT][/COLOR]

---

