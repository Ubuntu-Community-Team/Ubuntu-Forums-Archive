---
title: "[SOLVED] Suspend/Power Management Issue"
date: 2008-05-03
forum: General Help
---

### Post by ryth on 2008-05-03
Hi there,

Hopefully someone can help me out with this.  

Under screensaver -> power management I have Suspend/Hibernate **turned off** but for some reason my computer still goes into suspend mode after a unspecified amount of inactivity.

I have tried to disable my power management seettings in xorg.conf as labelled here: **[http://ubuntuforums.org/showpost.php?p=2651344&postcount=6](http://ubuntuforums.org/showpost.php?p=2651344&postcount=6)**

I don't mind using suspend, except that it kicks in when I don't want it to (i.e. grabbing a torrent or whatever) so for now I'd like to only enter that state manually.

System specs:

ATI RadeonX1950 XT
AMD 64 X2 4200
Hardy Heron i386

Cheers.

---

### Post by ryth on 2008-05-05
gratuitous bump. 

Issue still happening even though I've reset the power management settings twice now.  any insight would be appreciated.

---

### Post by ryth on 2008-05-26
Well after a few weeks of tinkering I was able to figure this out.

Here were the steps I followed to 100% disable all power management.

1.  Installed **Boot Up Manager**

```
sudo apt-get install bum
```

2.  De-select the following services
[LIST]
[*]powernowd
[*]apmd
[*]acpi-support
[*]acpid
[/LIST]

3.  Disable **Gnome-Power-Manager** from starting up when you boot into gnome.
```
System->Preferences->Sessions
```

Hope that helps anyone else who might be trying to trouble-shoot this.

Cheers.

---

