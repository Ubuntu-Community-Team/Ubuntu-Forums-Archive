---
title: "Systemd v. Upstart - which do I use?"
date: 2015-08-24
forum: General Help
---

### Post by marseille2 on 2015-08-24
I'm confused about starting services or enabling them at boot. My system (trusty) has both upstart and systemd (from a previous update). When I read the release of the update... it said it would put on systemd. Can I use the command systemctl to start/enable services? I'm confused by contradictory tutorials and conversations. Some say no... but I've already installed a program to use systemctl. I'm wondering if I made a big mistake, and just broke something.

---

### Post by v3.xx on 2015-08-24
I was not aware that 14o4 now had the option.  Will have to check it out.

I have been using both and switching between both in 15.10 without breakage.  So I consider it to be safe.  But mileage can vary, so user beware :)  Also I think uStudio uses a different kernel and this is untested by me.

[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

---

### Post by QDR06VV9 on 2015-08-24
What is the output of
```
[COLOR=#000000][FONT=Ubuntu Mono]pidof systemd && echo "systemd" || echo "other"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]other[/FONT][/COLOR]
```

And
```
[COLOR=#000000][FONT=Ubuntu Mono]pidof /sbin/init && echo "sysvinit" || echo "other"
[/FONT][/COLOR]1 sysvinit[COLOR=#222222][FONT=Verdana]
```[/FONT][/COLOR]
[COLOR=#000000]The one(1) indicates i am using upstart and also below the 1 it shows "sysvinit"[/COLOR]

---

### Post by marseille2 on 2015-08-24
Looks like I get the same thing:

```
[COLOR=#000000][FONT=Ubuntu Mono]
$ pidof systemd && echo "systemd" || echo "other"
other

[/FONT][/COLOR]$ pidof /sbin/init && echo "sysvinit" || echo "other"
1
sysvinit 
```


So I guess I'm using upstart, and messed up. Ouch.

---

### Post by ian-weisser on 2015-08-24
14.04 was released using Upstart, and should continue to use Upstart for it's supported life. The whole point of an LTS release is that the software doesn't change over the release life. Changing init during life would be a fairly severe change.

In order to use systemd, you either need to manually change over 14.04, or install Ubuntu 15.04.

---

