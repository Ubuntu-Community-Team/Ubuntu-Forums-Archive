---
title: "Is it possible to remove snapd?"
date: 2018-12-28
forum: General Help
---

### Post by pardeep.saini on 2018-12-28
Hello,
so I'm experiencing very slow launch times for snap applications and have not found any possible solution to make them launch faster.

Is it possible to completely remove snapd and use "normal" applications?

This is the output of snap list
```
Name                  Version         Rev   Tracking  Publisher   Notes
canonical-livepatch   8.1.0           54    stable    canonical[COLOR=#4E9A06]&#10003;[/COLOR]  -
core                  16-2.36.3       6130  stable    canonical[COLOR=#4E9A06]&#10003;[/COLOR]  core
core18                18              536   stable    canonical[COLOR=#4E9A06]&#10003;[/COLOR]  base
gnome-3-26-1604       3.26.0          74    stable/…  canonical[COLOR=#4E9A06]&#10003;[/COLOR]  -
gnome-logs            3.30.0          45    stable/…  canonical[COLOR=#4E9A06]&#10003;[/COLOR]  -
gnome-system-monitor  3.30.0          57    stable/…  canonical[COLOR=#4E9A06]&#10003;[/COLOR]  -
gtk-common-themes     0.1-4-g88bc1b2  818   stable/…  canonical[COLOR=#4E9A06]&#10003;[/COLOR]  -

```

I have already removed gnome calculator, gnome characters and vlc.

---

### Post by deadflowr on 2018-12-28
yeah, you can simply uninstall snapd via apt.
Note you'll lose the livepatch function so you will need to reboot into new kernels with all the patches applied from now on.
Might have to deactivate your livepatch token as well and remove that snap, but that's outside anything I'd know about.
Found this though,
deactivate  with
```
sudo snap run canonical-livepatch disable
```
and remove
```
sudo snap remove canonical-livepatch 
```

---

### Post by pardeep.saini on 2018-12-28
I have no problem with rebooting my pc, I do it everyday so I don't think loosing the livepatch functionality will be an issue for me.

If I do uninstall snapd, will the snap applications be uninstalled with it? if yes, how can I then found the "normal" applications?

And what is the purpose of core and core18 snap applications? can they be removed without problems?

---

### Post by mc4man on 2018-12-28
> **pardeep.saini said:**
> I have no problem with rebooting my pc, I do it everyday so I don't think loosing the livepatch functionality will be an issue for me.

If I do uninstall snapd, will the snap applications be uninstalled with it? if yes, how can I then found the "normal" applications?

And what is the purpose of core and core18 snap applications? can they be removed without problems?

Just go 
```
sudo apt purge snapd
```
core and core18 snaps are for snapd & installed snaps only, when you remove snapd they're of no use & will be removed.

The only app you have that's a snap to replace is gnome-system-monitor, just install as normal, i.e,
```
sudo apt install gnome-system-monitor
```

As far as remnants, you can remove ~/snap  folder & if inclined look at the /var/lib/snapd/snaps folder to see if it or any files or folders in it are left, can be removed if there.

---

### Post by oldfred on 2018-12-28
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)
boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341) 

Better way than below brute force by item.
This does it all:
sudo apt autoremove --purge snapd

This was all the steps (from my history) I did:
34  snap list
   35  sudo snap remove gnome-logs
   36  sudo snap remove gnome-calulator
   37  sudo snap remove gnome-calculator
   38  sudo snap remove gnome-characters
   39  sudo snap remove gnome-system-monitor
   40  sudo snap remove core
   41  snap list
   42  sudo snap remove gnome-3-26-1604
   43  sudo snap remove core
   44  snap list
   45  df
   46  
   47  snap list
   48  sudo snap remove core
   49  sudo umount /snap/core/4407
   50  sudo umount /snap/core/4571
   51  sudo umount /snap/core/4327
   52  sudo umount /snap/core/4571
   53  snap list
   54  df
   55  sudo umount /snap/core/4571
   56  ls -l /snap/core
   57  sudo systemctl stop snapd
   58  sudo umount /snap/core/4571
   59  sudo snap remove core 

      
 snap changes  
           
 sudo apt remove --purge snapd

---

### Post by HermanAB on 2018-12-29
Ayup, like desktop search and cloud services, snap seems to be another one of those CPU sapping bright ideas that no common users really need.

The result is that when I need a truly fast machine, I use Slackware, which is a completely crapfree distro, reminiscent of OpenBSD.

---

### Post by pardeep.saini on 2018-12-29
Thanks to all of you guys, I followed your instructions and managed to remove snapd.

I reinstalled the applications from apt and now, finally, they are opening fast.

Thanks, again.

---

### Post by kmkwood on 2019-02-27
Thank you for the information.  A few days ago I could no longer start opera because of problems with the ~/snap/opera directory.  I couldn't find out how to correct it, so I was happy to find out how to remove snap.

I am very disappointed that ubuntu 18 came with snap -- but without warning about it!  When I started up opera, all my passwords were gone.  There was nothing about how to migrate from the non-snap to the snap version -- and don't let anyone tell you that the transition is transparent and automatic.  It wasn't for me.

---

