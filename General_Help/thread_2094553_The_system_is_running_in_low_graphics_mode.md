---
title: "The system is running in low graphics mode"
date: 2012-12-14
forum: General Help
---

### Post by winjeel on 2012-12-14
I had asked this question at Launchpad, but after 2 weeks I still haven't got a reply, and the problem needs to be solved urgently. The original question was posted here: [URL="https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/215711"]https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/215711
[/URL]
In short, I used the normal scheduled system updates and allowed the updater to install updates automatically. The system needed restarting, and that's when the troubles began. It would only go to "The system is running in low graphics mode", and I cannot do any of the options to fix it.

I'm running 64bit 12.04 on a Dell E5520

---

### Post by Rexilion on 2012-12-14
Aside from updating, did you edit anything related to the system? I.e. anything outside the user environment?

If not, provide the contents of the file:

> /var/log/dpkg.log.

P.S. 'Demanding' a 'fast fix', on platforms powered by volunteers, is not a wise approach to signal urgency.

---

### Post by winjeel on 2012-12-14
> **Rexilion said:**
> Aside from updating, did you edit anything related to the system? I.e. anything outside the user environment?
...
P.S. 'Demanding' a 'fast fix', on platforms powered by volunteers, is not a wise approach to signal urgency.

1. Nope, no changes. I don't like to tinker with anything under the bonnet.
**2. I got "Permission denied"**
2. I'm aware of that. I'm also a lot more polite in advance, but I've had to get fixes so many times for Ubuntu in the last few years, I feel that I'm suffering the same as I did when I once used Windows ME. The whole reason why I wanted to depart from Windows! I've had so few problems with XP and so far none with W7. In any case, I do appreciate the help. :)

---

### Post by Rexilion on 2012-12-14
You get permission denied since you have to access it as root:

```
sudo gedit /var/log/dpkg.log
```

or for a terminal:

```
sudo cat /var/log/dpkg.log
```

---

### Post by winjeel on 2012-12-14
I got:
> ** (gedit:925): WARNING **: Command line 'dbus-launch --autolaunch=ca95ebfa36cb528e271e016d00000011 --binary-syntax --close-stderr' --exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
Cannot open display:
Run 'gedit --help' to see a full list of available command line options.

---

### Post by Rexilion on 2012-12-14
I'm sorry, I'm not familiar with 'low graphics mode'.

Perhaps you could boot into a LiveCD (Ubuntu Live?) and try accessing the file from that, and then upload it.

---

### Post by cyberphrog on 2012-12-14
I got the same message during boot-up on my 12.04 system.  There's an issue with my syslog and kern files growing out-of-control.  Once they got to the size where my HD was completely full, I got the 'low-graphics mode' message and it couldn't complete the boot-up.  In the end, I recovered my critical files by booting on an install disk and transferring them to the back-up, then wiping the HD clean and starting anew.

Is your home directory encrypted?

---

### Post by Rexilion on 2012-12-15
> **cyberphrog said:**
> I got the same message during boot-up on my 12.04 system.  There's an issue with my syslog and kern files growing out-of-control.  Once they got to the size where my HD was completely full, I got the 'low-graphics mode' message and it couldn't complete the boot-up.  In the end, I recovered my critical files by booting on an install disk and transferring them to the back-up, then wiping the HD clean and starting anew.

Is your home directory encrypted?

And maybe also provide the output of:

```
df -m
```

If you have to do it from the commandline, use pastebinit:

```
aptitude -yR install pastebinit
df -m | pastebinit
```

And provide us with the link the last command gives you.

---

### Post by winjeel on 2012-12-25
Unfortunately, I chose to be wise and encrypt my Home folder, so I can't recover some things. Currently, I'm accessing the Ubuntu partition of my hdd via USB mounted OS. From here, it seems so easy to just replace the corrupted file with a working one, but which one?

Also, I got a message from LaunchPad saying that there hasn't been any activity on my plea for help for the last 15 days and so it automatically closed the question, so I reopened it: [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/215711](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/215711)

As I've said many times before, thanks in advance for your help.

---

### Post by NM5TF on 2012-12-26
Does your system have an AMD cpu with Nvidia graphics 
card by any chance???

I was having the same problems since kernel 3.2.0-34...I
installed the 3.2.0-35 kernel yesterday and now everything
is working correctly.

I did have to regress to the Nvidia kernel 173.14.35 to get
full 3D Unity to work correctly....the nvidia-current kernel
didn't work for me.

Tommy

---

