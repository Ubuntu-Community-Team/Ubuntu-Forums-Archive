---
title: "How Do You Start Ubuntu in &quot;init 3&quot;"
date: 2007-06-19
forum: General Help
---

### Post by LakeWind on 2007-06-19
How do you start up Ubuntu in "init 3" from the grub menu options? I came over from OpenSUSE and starting in "init 3" was very easy (enter "init 3" in kernel options during the grub menu).

The reason I am asking is that this weekend I installed Ubuntu in my daughter's computer. After the install was complete and fully customized, we decided to change out her video adapter (from an ATI to nVidia so that the restricted drivers and 3d acceleration would work). Upon rebooting, I expected that I could easily boot into init 3 and run "dpkg-reconfigure xserver-xorg"... to setup the new adapter. No such luck. I couldn't boot to a command prompt even when booting in recovery mode and editing the grub options. I must be overlooking something very simple. SO... we re-installed everything and now it's working. 

There must be a way but I am missing it... OR is this just not possible now with upstart?

Any help would be appreciated.

Thanks!  ;)

---

### Post by dreadlord_chris on 2007-06-19
> **LakeWind said:**
> How do you start up Ubuntu in "init 3" from the grub menu options? I came over from OpenSUSE and starting in "init 3" was very easy (enter "init 3" in kernel options during the grub menu).

The reason I am asking is that this weekend I installed Ubuntu in my daughter's computer. After the install was complete and fully customized, we decided to change out her video adapter (from an ATI to nVidia so that the restricted drivers and 3d acceleration would work). Upon rebooting, I expected that I could easily boot into init 3 and run "dpkg-reconfigure xserver-xorg"... to setup the new adapter. No such luck. I couldn't boot to a command prompt even when booting in recovery mode and editing the grub options. I must be overlooking something very simple. SO... we re-installed everything and now it's working. 

There must be a way but I am missing it... OR is this just not possible now with upstart?

Any help would be appreciated.

Thanks!  ;)

Actually, from the login screen you could either select Sessions > Terminal Session (I think is what it's called) **or** press Control-Alt-F1 which will bring up tty1. After logging in, if you really want "init 3" then:
```

sudo telinit 3

```
will put you there. Not really necessary though - you can just shut down GDM from there:
```

sudo /etc/init.d/gdm stop
suod dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

You could also have just reconfigured xserver-xorg from Recovery Mode - actually, I'm pretty sure that Recovery Mode *is* init 1....

---

### Post by warcriminal on 2007-06-19
There is a guide to initlevels and startup at;

[http://www.goitexpert.com/entry.cfm?entry=Manage-Linux-INIT-or-Startup-Scripts](http://www.goitexpert.com/entry.cfm?entry=Manage-Linux-INIT-or-Startup-Scripts)

---

