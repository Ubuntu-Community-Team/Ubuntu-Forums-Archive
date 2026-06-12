---
title: "can't run  sudo thunar  in xubuntu 20.04.02"
date: 2021-09-04
forum: General Help
---

### Post by Seadevil on 2021-09-04
when i type in   "sudo thunar" in the terminal , i am now getting this message:  

$ sudo thunar
thunar: Failed to initialize Xfconf: Error spawning command line ?dbus-launch --autolaunch=defc0a3dd448414a99851110dd72d587 --binary-syntax --close-stderr?: Child process exited with code 1

Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused

 cannot open display: :0.0



how do i fix this?    I am trying to copy files from luckybackup into the /etc/samba    folder...but permission denied.   have to use sudo thunar to do this.

never had a problem before.

---

### Post by TheFu on 2021-09-04
It is a bad idea to use sudo with most, nearly all, GUI programs.  Doesn't luckybackup have a restore capability that will put files back from where they came?  If not, I'd use **sudo rsync [options] source target**.

The error you are seeing is an X/Windows authentication error.  Different userids have different rights, not just to files, but to the "desktop".  When Wayland takes over xubuntu, I don't think this will be possible.

It may be possible to use **pkexec** (instead of sudo). The manpage:
```
NAME
       pkexec - Execute a command as another user

SYNOPSIS
       pkexec [--version] [--disable-internal-agent] [--help]

       pkexec [--user username] PROGRAM [ARGUMENTS...]
```
I wasn't able to get pkexec to work. Kept getting a GDBus.Error ... but considering that I'm not running gnome-anything, that is expected.

I think **systemd** has a method as well, but I've avoided learning anything about systemd for as long as possible.  

[https://askubuntu.com/questions/842914/can-i-open-a-file-manager-as-root-without-using-terminal-in-xubuntu](https://askubuntu.com/questions/842914/can-i-open-a-file-manager-as-root-without-using-terminal-in-xubuntu) says to use **gksu**. First I've heard of that.  I'm not much of a GUI person, sorry.

---

### Post by guiverc on 2021-09-05
> **TheFu said:**
> 
[https://askubuntu.com/questions/842914/can-i-open-a-file-manager-as-root-without-using-terminal-in-xubuntu](https://askubuntu.com/questions/842914/can-i-open-a-file-manager-as-root-without-using-terminal-in-xubuntu) says to use **gksu**. First I've heard of that.  I'm not much of a GUI person, sorry.

`gksu` is deprecated (*removed in both Debian & Ubuntu*); the notice was long ago and from Jeremy Bicha [of Canonical].  I didn't find the notice, but it'll be *akin* to

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=892768](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=892768)

(*quite probably the same day*)

`pkexec`replaced it, and Jeremy Bicha (*if I recall correctly*) blogged about it, which reached Planet Ubuntu (*thus reached UWN which possibly is why I recall some detail vagely*), but it was long ago.

---

