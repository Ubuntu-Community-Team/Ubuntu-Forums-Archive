---
title: "Issues with FirewallD and Discover"
date: 2019-04-29
forum: General Help
---

### Post by mariofanboy-21 on 2019-04-29
Hello, Ever since I installed xfce, I keep having issues with authentication issues like FirewallD and Discover
[URL="https://ibb.co/YZZ16pq"]
[/URL][https://ibb.co/YZZ16pq](https://ibb.co/YZZ16pq)
[https://ibb.co/b5rLDDz](https://ibb.co/b5rLDDz)

---

### Post by wildmanne39 on 2019-05-01
If you have not received a reply in 12 hours feel free to bump your thread to keep it in view.

---

### Post by mariofanboy-21 on 2019-05-04
bump

---

### Post by wildmanne39 on 2019-05-04
Please state what version of Ubuntu you are using, did you install xfce on Ubuntu or are you using xubuntu? the more information you can provide the more likely someone can help you.

---

### Post by mariofanboy-21 on 2019-05-04
I am currently using Ubuntu and Yes I did install xfce as a remote desktop Session. Root Privileges do work there but nowhere else

---

### Post by mariofanboy-21 on 2019-05-05
bump

---

### Post by mariofanboy-21 on 2019-05-05
I have responded to your question on the thread

---

### Post by wildmanne39 on 2019-05-05
This is an older answer that may help:

[https://forum.xfce.org/viewtopic.php?id=9998](https://forum.xfce.org/viewtopic.php?id=9998)

I am not sure it still applies.

---

### Post by #&amp;thj^% on 2019-05-05
Can you show us the output of:
```
apt policy policykit-1-gnome
```
BTW your thread title is a bit confusing as well >> [lubuntu] is there any lxde session installed?
EDIT anyway lets have a look at "policykit-1-gnome"** if it is installed with:**
```
cat /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
[Desktop Entry]
Name=PolicyKit Authentication Agent
Comment=PolicyKit Authentication Agent
Exec=/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
Terminal=false
Type=Application
Categories=
NoDisplay=true
OnlyShowIn=XFCE;Unity;X-Cinnamon;
X-GNOME-AutoRestart=true
AutostartCondition=GNOME3 unless-session gnome
X-Ubuntu-Gettext-Domain=polkit-gnome-1

```

---

### Post by mariofanboy-21 on 2019-05-05
Well This is my result:
```

 policykit-1-gnome:
  Installed: 0.105-7ubuntu2
  Candidate: 0.105-7ubuntu2
  Version table:
 *** 0.105-7ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco/main amd64 Packages
        100 /var/lib/dpkg/status 

```
(Sorry forgot how to out the output in a  code box)

---

### Post by #&amp;thj^% on 2019-05-06
> (Sorry forgot how to out the output in a code box) 
See my Sig below "Code Tags"
I would like to see this also please:
```
cat /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
```

---

### Post by mariofanboy-21 on 2019-05-06
```

[Desktop Entry]
Name=PolicyKit Authentication Agent
Comment=PolicyKit Authentication Agent
Exec=/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
Terminal=false
Type=Application
Categories=
NoDisplay=true
OnlyShowIn=XFCE;Unity;X-Cinnamon;
X-GNOME-AutoRestart=true
AutostartCondition=GNOME3 unless-session gnome
X-Ubuntu-Gettext-Domain=polkit-gnome-1

```

---

### Post by #&amp;thj^% on 2019-05-06
Thanks and that looks ok for a normal set-up but you have a custom user-setup.
So try this for me please:
```
sudoedit /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
```
Now in the line:**"AutostartCondition=GNOME3 unless-session gnome"** put a comment in front of that so it looks exactly like:
```
#AutostartCondition=GNOME3 unless-session gnome
```
Save it and close, And I'm not sure but a log-out and log-in should set it... if not try a reboot.

---

### Post by mariofanboy-21 on 2019-05-06
Attempted your  advice, still have the same issue.

---

### Post by #&amp;thj^% on 2019-05-06
Just to be sure did you also reboot?

---

### Post by mariofanboy-21 on 2019-05-06
I did I think it's something to do with XFCE' session getting root access when needed.

---

### Post by #&amp;thj^% on 2019-05-07
I'm still unclear as to how to advise here, and it looks as gnome is a red-headed step child here.

In a gnome session see if you can run:
```
sudo -l -U yourusername
```
where "yourusername" is the name used to login with.
If that is un-sucessful try this:
```
groups
```
This could take a bit to figure out so hang in here please.

---

### Post by mariofanboy-21 on 2019-05-10
this is what I got 
```

Matching Defaults entries for cardin on cardin-pc:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User cardin may run the following commands on cardin-pc:
    (ALL : ALL) ALL
    (ALL) ALL

```

---

### Post by #&amp;thj^% on 2019-05-10
This problem is seemly caused by sudo looking for directives in a place it cannot find them:
We may be narrowing in on the problem hopefully, may I see this also:
```
cat /etc/nsswitch.conf 
```
so you should have a /etc/nsswitch file entry like the following:
```

sudoers:        files
```
I have to work all day today but should be around tomorrow. (Just a heads-up)
EDIT: **Also show me this please:**
```
which firewalld
which discover
```

---

### Post by mariofanboy-21 on 2019-05-10
For Nsswitch
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd:         files systemd
group:          files systemd
shadow:         files
gshadow:        files


hosts:          files mdns4_minimal [NOTFOUND=return] dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

```

firewalld:
```

/usr/sbin/firewalld

```

discover: n/a

---

### Post by #&amp;thj^% on 2019-05-10
Interesting no discover?? Thread title shows>>"FirewallD and Discover and lubuntu" this can lead to a lot of bad information given to you. That's why we are checking a few things first. ;)
Kind of give me some information here>> like why are we remote-ing and I'm assuming here your remote is to gnome from the XFCE box right?
How are you remote-ing? Are you using xrdp? And are you trying to use sudo from the XFCE-Remote to Gnome?
```
apt policy xrdp
```
And:
```
apt policy ufw
```
**Only if **you "are" using xrdp lets take a look at it via:
```
cat /etc/xrdp/xrdp.sh
``` 
Now to save time since we are on very different time zones or schedules, and again only **"if"** you are in-fact using xrdp, lets also check:
```
cat /etc/xrdp/xrdp.sh 
```
It may be as simple as stopping the "xrdp" from running with:
```
sudo service xrdp stop
```
Then check your sudo commands again from Gnome.

---

### Post by mariofanboy-21 on 2019-05-15
```

xrdp:
  Installed: 0.9.9-1
  Candidate: 0.9.9-1
  Version table:
 *** 0.9.9-1 500
        500 http://archive.ubuntu.com/ubuntu disco/universe amd64 Packages
        100 /var/lib/dpkg/status

```

```

ufw:
  Installed: 0.36-1ubuntu1
  Candidate: 0.36-1ubuntu1
  Version table:
 *** 0.36-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status

```

For xrdp I didn't see the line you presented

---

### Post by mariofanboy-21 on 2019-05-21
Is there anything else i could do?

---

### Post by #&amp;thj^% on 2019-05-21
Well first off I see you have both UFW and FirewallD installed not the best way to set up.(They interfere with each other)
Pick one,(UFW works well enough) then we will see if we can get you straight again.
BTW Let me know how long your going to around today.(On the forums)
My time that I have to help on forums has been reduced significantly as of late, so it helps me to help you if you would be kind enough to watch this thread a little bit better if possible.
Thanks

---

### Post by mariofanboy-21 on 2019-05-21
How do I uninstall one?

---

### Post by #&amp;thj^% on 2019-05-21
Simply running this:
```
sudo apt remove --purge firewalld
```
I consider firewalld more of an advanced user's interface, but first we need to learn how to walk before we jump to run. :)
Now Reboot and see if things work.
EDIT I have to run now for to-nite, let me know when you'll be back in you next reply. Thanks

---

### Post by mariofanboy-21 on 2019-05-22
Thanks

---

