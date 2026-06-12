---
title: "Boot error with Systemd"
date: 2015-10-20
forum: General Help
---

### Post by adlerhn on 2015-10-20
I have Gnome Ubuntu installed in my system, with a bunch of other desktop environments installed, including KDE.

Since I upgraded to Ubuntu 15.10 about 2 or 3 weeks ago, most of the times that I boot my system, instead of going to gdm for the log in screen (as the default I have configured), the system shows some other login screen (I think it is sddm's). This other login screen restarts itself every couple of seconds for some reason, so I cannot log in.

I have tried so far:
[LIST]
[*]sudo dpkg-reconfigure gdm
[*]Selecting different kernels
[*]Starting in safe mode
[*]fsck
[/LIST]

My only workaround is to select Upstart during boot. Then it boots perfectly, every time.

Note that booting with Systemd used to work perfectly before the upgrade to 15.10.

Any idea of how to debug this boot issue?

---

### Post by Cavsfan on 2015-10-20
> **adlerhn said:**
> I have Gnome Ubuntu installed in my system, with a bunch of other desktop environments installed, including KDE.

Since I upgraded to Ubuntu 15.10 about 2 or 3 weeks ago, most of the times that I boot my system, instead of going to gdm for the log in screen (as the default I have configured), the system shows some other login screen (I think it is ssdm's). This other login screen restarts itself every couple of seconds for some reason, so I cannot log in.

I have tried so far:
[LIST]
[*]sudo dpkg-reconfigure gdm 
[*]Selecting different kernels 
[*]Starting in safe mode 
[*]fsck 
[/LIST]

My only workaround is to select Upstart during boot. Then it boots perfectly, every time.

Note that booting with Systemd used to work perfectly before the upgrade to 15.10.

Any idea of how to debug this boot issue?

This will tell you what display manager you are using. 
```
cat /etc/X11/default-display-manager
```

I am using lightdm and have no problems.

---

### Post by adlerhn on 2015-10-20
```
cat /etc/X11/default-display-manager
```

/usr/sbin/gdm

Testing the 3 DMs I have installed:

[LIST]
[*]If I select sddm as the DM, the log in works fine, funny enough.
[*]With lightdm, the greeter is visible for 2 seconds, and then the screen just goes black until I restart the computer.
[*]With gdm selected, sddm's is actually the greeter that appears upon boot (restarts every couple of seconds).
[/LIST]

---

### Post by QDR06VV9 on 2015-10-20
Are you sure it is not [B]SDDM?
[/B]I know Fedora is talking about Droping out KDM for SDDM.
[COLOR=#333333][FONT=Helvetica Neue] [/FONT][/COLOR][bug report in ubuntu's tracker for sddm packaging]("https://bugs.launchpad.net/ubuntu/+bug/1157742")

---

### Post by adlerhn on 2015-10-20
You are right. Too many consonants in a row. I have amended my post.

In Ubuntu 15.10, I don't have KDM at all (at least, not installed). Only SDDM.

---

### Post by adlerhn on 2015-10-20
On a further look, SDDM is not really restarting itself. The system is just showing the text-mode boot messages every couple of seconds and then goes back to SDDM. Trying to log in at that point freezes the system, and upon restart I see the notification of an Xorg crash ([https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1237904](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1237904)). Not sure if related, but only happens when I try to log in using Systemd and gdm.

My main question at this point is, if I have GDM selected as my DM, why would I see the SDDM greeter when I boot with Systemd? Might the Systemd issue be causing Xorg to crash? May the Xorg issue be causing Systemd to launch SDDM as a fallback? Might they be unrelated issues afterall?

---

### Post by QDR06VV9 on 2015-10-20
Still early for bugs triaged.
Try this as a work around next time.
to make it work is to switch to tty2 and run .
```
systemctl restart sddm 
```
I don't know for sure just offering help.
Edit:
Some more helpful Tips
```
sudo systemctl disable sddm
sudo systemctl enable gdm
```

Using any DM that works or of Preference.

---

### Post by adlerhn on 2015-10-20
```
sudo systemctl disable sddm
sudo systemctl enable gdm
```

That made the trick! Thanks a lot. Now the computer boots fine with gdm and Systemd.

For reference, the output of the commands was:

```
$ sudo systemctl disable sddm
[sudo] password for myuser: 
Synchronizing state of sddm.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install disable sddm
insserv: warning: current start runlevel(s) (empty) of script `sddm' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `sddm' overrides LSB defaults (0 1 6).

$ sudo systemctl enable gdm
Synchronizing state of gdm.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable gdm
```

Out of curiosity, any idea of what may have happened?

---

### Post by QDR06VV9 on 2015-10-20
> **adlerhn said:**
> [CODE]
Out of curiosity, any idea of what may have happened?

This would be totally just an idea!(Guess!!):D
I seem to know very little about systemd and it is still young in it's Development. Plus 15.10 is in development cycle also.
So sometimes having another New DM installed may influance the Login Mechanism.
So we just set it straight! small hammer. :lolflag:
Regards

---

### Post by zika on 2015-10-21
SystemD is not as young as You write.
To set it &#8222;straight&#8220;...```
sudo dpkg-reconfigure gdm
```

---

### Post by QDR06VV9 on 2015-10-21
For me I should have said it is still young, as I choose not to use it during the 15.04 series,  and remained with upstart in hopes systemd would go away.:o(no such luck)
**as mentioned **he did use "sudo dpkg-reconfigure gdm"
But yes that should have worked. But he got sorted out, that's what we were after.
Best Regards:D

---

### Post by ventrical on 2015-10-21
> **runrickus said:**
> For me I should have said it is still young, as I choose not to use it during the 15.04 series,  and remained with upstart in hopes systemd would go away.:o(no such luck)
Best Regards:D

Even with the (upstart) option available, this whole systemd transition has a lot of converts and newcomers  reeling. With the resources I have I can take it or leave it. I do not really notice any improvement in boot speed etc.. but if the bean counters say so then good for them. As a tester , I  am testing most of my installs with systemD as default.  I rarely get boots errors (so sorry .. cannot add anything to this report here) but I do get  problems when I try to run conventional command like:

```

startx -- :1

```

only rebooting under (upstart) will allow this command to execute correctly.. so it goes to a user_space issue again.

Regards..

---

### Post by adlerhn on 2015-10-26
I just had the same issue with another computer that I just upgraded to Ubuntu 15.10. The same solution applied successfully.

---

