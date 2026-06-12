---
title: "Sandbox error; programs won't run"
date: 2024-05-08
forum: General Help
---

### Post by david12 on 2024-05-08
I woke up this morning to find that upon starting, my computer would not run certain programs.  Here are the cases:

1. Brave
> david@david-ubuntu01:~$ sudo brave-browser
[sudo] password for david: 
[3571:3571:0508/072450.537344:ERROR:zygote_host_impl_linux.cc(99)] Running as root without --no-sandbox is not supported. See [https://crbug.com/638180](https://crbug.com/638180).

2. Tuta via AppImage
> david@david-ubuntu01:~/applications$ ./tutanota-desktop-linux_0d66b91d4546d31f933693cf28579c01.AppImage
[4310:0508/072816.249466:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /tmp/.mount_tutanoRuG14C/chrome-sandbox is owned by root and has mode 4755.
[appimagelauncher-binfmt-bypass/lib] ERROR: child exited with code 5


As far as I can remember, these programs worked without hesitation two days ago, which was the last time this computer ran.
I am running Ubuntu 24.04
I've no idea what is going on here, your kind suggestions would be most appreciated.  Thanks.

---

### Post by currentshaft on 2024-05-08
k

---

### Post by david12 on 2024-05-08
Until this morning I launched Brave from the GNOME GUI as a normal user.  But now Brave will not launch, nor will some other stuff.  In an attempt to get at what the error might be, and perhaps overcome it, I tried to launch Brave for the command line as root.  It generated the error shown.  I also spoke harshly to my computer and shook it like a pinball machine. Nothing, so far,

Please, do you have any idea what might be causing these errors?

---

### Post by currentshaft on 2024-05-08
na

---

### Post by #&amp;thj^% on 2024-05-08
Please run this and paste back the return, using Code Tags Please:
```
brave-browser
```
It might shed some light, and please don't run a browser with "sudo"

Ninja'd by currentshaft

---

### Post by david12 on 2024-05-08
```
brave-browser
```
This neither starts the program, nor returns anything at all... just blank.
```
google-chrome-stable
```
Likewise, Nada.

---

### Post by #&amp;thj^% on 2024-05-08
Interesting nothing at all???
Please show this now:
EDIT: I was on Arch so I fixed the code below
```
stat /usr/bin/brave-browser 
```
Should look like this.
```

  File: /usr/bin/brave
  Size: 348       	Blocks: 8          IO Block: 4096   regular file
Device: 8,18	Inode: 9571574     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-05-08 11:20:05.000000000 -0600
Modify: 2024-05-08 11:19:01.000000000 -0600
Change: 2024-05-08 11:20:05.695397175 -0600
 Birth: 2024-05-08 11:20:05.695397175 -0600
```

---

### Post by david12 on 2024-05-08
> -rwxr-xr-x 1 david david 123506095 May  2 21:24 tutanota-desktop-linux_0d66b91d4546d31f933693cf28579c01.AppImage

As I mentioned above, when I shut my computer down two days ago, everything was working fine.  I have used this AppImage often and repeatedly.  I have not set umask;  I have not re-downloaded the AppImage.

---

### Post by david12 on 2024-05-08
```
david@david-ubuntu01:~/applications$ stat /usr/bin/brave
stat: cannot statx '/usr/bin/brave': No such file or directory
```

```
david@david-ubuntu01:~/applications$ locate brave
/etc/alternatives/brave-browser
/etc/apparmor.d/brave
/etc/apt/sources.list.d/brave-browser-release.list
/etc/cron.daily/brave-browser
/etc/default/brave-browser
/etc/sysctl.d/30-brave.conf
.....and many, many lines of info thereafter

```

I think something may be really, really broken here.

---

### Post by #&amp;thj^% on 2024-05-08
I missed that part for Appimage, after reading the errors shown can you try with a flag "--disable-gpu-sandbox" at the end of your command.

---

### Post by david12 on 2024-05-08
oops.

```
david@david-ubuntu01:~/applications$ stat /opt/brave.com/brave
  File: /opt/brave.com/brave
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 8,2    Inode: 10485867    Links: 6
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-05-08 12:22:45.242530443 -0600
Modify: 2024-05-06 07:18:02.957387042 -0600
Change: 2024-05-06 07:18:02.957387042 -0600
 Birth: 2024-04-27 15:38:25.692047149 -0600
david@david-ubuntu01:~/applications$ 

```

wrong directory, sorry

---

### Post by #&amp;thj^% on 2024-05-08
> **david12 said:**
> oops.

```
david@david-ubuntu01:~/applications$ stat /opt/brave.com/brave
  File: /opt/brave.com/brave
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 8,2    Inode: 10485867    Links: 6
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-05-08 12:22:45.242530443 -0600
Modify: 2024-05-06 07:18:02.957387042 -0600
Change: 2024-05-06 07:18:02.957387042 -0600
 Birth: 2024-04-27 15:38:25.692047149 -0600
david@david-ubuntu01:~/applications$ 

```
That Looks right, but please try my suggestion in my post above

---

### Post by david12 on 2024-05-08
```
david@david-ubuntu01:~/applications$ ./tutanota-desktop-linux_0d66b91d4546d31f933693cf28579c01.AppImage --disable-gpu-sandbox
[6137:0508/123244.513022:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly.
Rather than run without sandboxing I'm aborting now. You need to make sure that /tmp/.mount_tutanom4ULYS/chrome-sandbox is owned by root and has mode 4755.
[appimagelauncher-binfmt-bypass/lib] ERROR: child exited with code 5
```

I hope I have done this correctly; it does not seem to have changed the outcome.

---

### Post by #&amp;thj^% on 2024-05-08
> **david12 said:**
> 

I hope I have done this correctly; it does not seem to have changed the outcome.

You did, 
That is a puzzle I need to think about, just one thing to check while I think here....is this installed?
```
[COLOR="#FF0000"] apt policy libfuse2t64[/COLOR]
libfuse2t64:
  Installed: 2.9.9-8.1build1
  Candidate: 2.9.9-8.1build1
  Version table:
 *** 2.9.9-8.1build1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by david12 on 2024-05-08
yup.

```
david@david-ubuntu01:~$  apt policy libfuse2t64
libfuse2t64:
  Installed: 2.9.9-8.1build1
  Candidate: 2.9.9-8.1build1
  Version table:
 *** 2.9.9-8.1build1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2024-05-08
Ok now try with flag  "--disable-setuid-sandbox" at the end.

---

### Post by david12 on 2024-05-08
```
david@david-ubuntu01:~/applications$ ./tutanota-desktop-linux_0d66b91d4546d31f933693cf28579c01.AppImage --disable-setuid-sandbox
[8033:0508/131227.939672:FATAL:zygote_host_impl_linux.cc(127)] No usable sandbox! Update your kernel or see https://chromium.googlesource.com/chromium/src/+/main/docs/linux/suid_sandbox_development.md
for more information on developing with the SUID sandbox. If you want to live dangerously and need an immediate workaround, you can try using --no-sandbox.
[appimagelauncher-binfmt-bypass/lib] ERROR: child exited with code 5

```

---

### Post by #&amp;thj^% on 2024-05-08
That appimage needs to be built for 24.04, or you need to get a hold of that maintainer on github.
If we continuance disabling features it becomes a security flaw. :(
Are you opposed to installing it as a ".deb" That's my install on Noble.
 ```
 apt policy brave-browser
brave-browser:
  Installed: 1.65.126
  Candidate: 1.65.130
  Version table:
     1.65.130 500
        500 https://brave-browser-apt-release.s3.brave.com stable/main amd64 Packages
 *** 1.65.126 500

```
I also firejail it, with different flags ie:
```
firejail brave-browser
### Or with more
firejail --private brave-browser
```
I'm more of CLI type user.

---

### Post by david12 on 2024-05-08
Thank you for your help.  I need to step away for a little while.  I have been concerned since I started working with snaps and sandboxes on Xubuntu 23.10 that I was going to run into an issue.  (I updated to Ubuntu 24.04 because I thought I might escape. I actually like the xfce user interface better, and I see that that is your wheelhouse.)  And things were going fine, until this morning, when they didn't.  That's the piece that is making no sense to me.  Why work well on Monday and then on Wednesday not? 
Thanks again for your help, I will check the thread upon my return.

---

### Post by #&amp;thj^% on 2024-05-08
I under stand that totally, I rid myself of all snaps and snapd. Not ready for production here.
```
apt-mark showhold
snapd

```

---

