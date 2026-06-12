---
title: "Can't get to graphical login screen when booting"
date: 2023-10-04
forum: General Help
---

### Post by luxvera4 on 2023-10-04
Ubuntu 22.04 was installed and is running on my machine. Recently, I updated grub files using "apt." Afterwards, **I can't get to Graphical Login session and end up with TTY login session when booting**. **How do I fix this issue?** I appreciate your valuable and prompt input!!

---

### Post by Bashing-om on 2023-10-04
Hello luxvera4 - Welcome to the Forums.

At this TTY login prompt - after logging into the system - what results from terminal command:
```

systemctl restart display-manager

```

see where we go from here.

[INDENT]in the process, somewhere
[/INDENT]

---

### Post by luxvera4 on 2023-10-04
Thank you for replying! Here is the results from terminal command:

> systemctl restart display-manager

===== AUTHENTIFICATION FOR org.freedesktop.systemd1.manage-units ===

Authentification is required to restart 'gdm3.service'
Authentification as: BlessedDonkey,,, (blesseddonkey)
Password: 

==== AUTHENTIFICATION COMPLETE ===============

PLEASE LET ME KNOW WHAT I SHOULD DO!

---

### Post by Bashing-om on 2023-10-04
luxvera4;

Well no errors - that is a good thing.

Did the GUI start ? 
ctl+alt+F1
??

Maybe Yes
[INDENT][INDENT]could be No[/INDENT][/INDENT]

---

### Post by luxvera4 on 2023-10-04
Well, ctl-alt-F1 doesn't do anything. Should I use a boot-repair tool using a bootable usb?

---

### Post by Bashing-om on 2023-10-05
luxvera4 - Well -- not ... but

> 
Should I use a boot-repair tool using a bootable usb?

Short answer is NO - as you do boot to a terminal then grub is not at fault - the issue lies within the GUI layer.
Unless that is that I fail to understand what you refer to as "TTY login session"; that might be a grub prompt or a grub rescue prompt ?

So, we need to find out what is *NOT* going on with the Desktop Environment. And that is which one ?
Please post back - between code tags - the result of this command:
```

loginctl show-session $XDG_SESSION_ID

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see here if we are dealing with X11 or Wayland. Then scratch our heads and figure out what next to look at. The Xorg.0.log file ?? Maybe --


[INDENT]It is a process
[/INDENT]

---

### Post by luxvera4 on 2023-10-05
First off, a screenshot of TTY login session right after booting is attached: ubuntu_tty_login.jpg
Next, a screenshot showing the result of loginctl is attached: loginctl.jpg

Please let me understand what is going on and what to do!

---

### Post by Bashing-om on 2023-10-05
luxvera4; Great

^ Confirms you are at a real terminal :D
The command's results tells us that the display is not started. No idea yet as to the why not.

We get any hint's in Xorg's lofgfile ?
```

cat .local/share/xorg/Xorg.0.log | nc termbin.com 9999

```
where here the result is a URL -  Pass that link back here; we see if we can read anything of value.

[INDENT]Gots to be a reason[/INDENT]

---

### Post by luxvera4 on 2023-10-05
Thank you for further suggestion. Here is the output from the terminal:

> cat .local/share/xorg/Xorg.0.log | nc termbin.com 9999
> nc: getaddrinfo for host "termbin.com" port 9999: Name or service not known

Hope the above output will give you a clue!

---

### Post by Bashing-om on 2023-10-05
luxvera4; My bad

In that I failed to recall that "nc" is not installed by default. In our software repository :D

To use "NC" to facilitate a pastebin ( you may use any pastebin method you prefer) run in terminal:
```

sudo apt update
sudo apt upgrade
sudo apt install netcat-openbsd

```

Now try >>
```

cat .local/share/xorg/Xorg.0.log | nc termbin.com 9999

```

Be aware that .local/share/xorg/ is the new location of the Xorg log file in the later releases of Ubuntu proper.

[INDENT]still - looking for that reason why not
[/INDENT]

---

### Post by luxvera4 on 2023-10-05
I ran apt commands as instructed. nc is available: 
> which nc
> /usr/bin/nc

>  cat .local/share/xorg/Xorg.0.log | nc termbin.com 9999
> nc: getaddrinfo for host "termbin.com" port 9999: Name or service not known

I suspect something went wrong with grub files. If I run boot-repair using USB boot device, don't you think it will replace corrupted grub files with default grub files?

---

### Post by luxvera4 on 2023-10-05
I did as instructed:

> sudo apt update
> sudo apt upgrade
> sudo apt install netcat-openbsd

NC is available: 
> which nc
> /usr/bin/nc

> cat .local/share/xorg/Xorg.0.log | nc termbin.com 9999
> nc: getaddrinfo for host "termbin.com" port 9999: Name or service not known

Questions: (1) If I run boot-repair on USB bootable device, don't you think it will replace corrupted grub files with default grub files?
            
                 (2) What if I reinstall the same version of UBUNTU 22.04? The existing files will be preserved afrer reinstalling. What do you think?

---

### Post by Bashing-om on 2023-10-05
luxvera4 - Hummm ..

Maybe nc is telling us that the file does not exist ?

OK - old location >>
what shows
```

ls -al /var/log/Xorg.0.log

```

While I still do not believe that grub is at fault here - will not hurt a thing to run the report.

edit for #2.
Nuclear solution always works --- but we learn nothing in taking that option.

-which way did he go, George-

---

### Post by luxvera4 on 2023-10-08
> ls -al /var/log/Xorg.0.log
> -rw-r--r-- 1 root root Dec 10 2021 /var/log/Xorg.0.log

You know what? The issue has been resolved! I can log in as before! :o
Thank you for discussing with me!

---

### Post by Bashing-om on 2023-10-08
luxvera4 - Great

Please relate to us what the solution was - and >>
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]up up and away
[/INDENT]

---

### Post by minhbui on 2024-09-01
Hi I have the same problem. Still stucked with the tty1 login . I need to type start display-manager or ( Start gdm3) each time to access to graphical login page as normally.
How to you resolved your problem. Please and thank you.

---

