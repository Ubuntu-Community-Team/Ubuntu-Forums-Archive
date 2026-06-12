---
title: "Ubuntu 19.04 freezes on boot @ Lenovo T440s"
date: 2020-03-19
forum: General Help
---

### Post by ansgar.snow on 2020-03-19
Hey, my first  issue is that I cant see what pc is currently doing on boot, I have a loading screen but when I try ctrl+Fkeys it does nothing, on other linux OS it usualy shows the messages about progress of loading the OS, how can I get such screen in Ubuntu 19.04?

My second issue is that my pc sometimes got frozen on boot, i see the graphical animation showing progress but nothing is really loading and I can only reset the machine. Tried to get through journalctl but Im not sure what is causing this, simply seeing the output from booting the OS would help a lot more as it would show me where it is stuck.

#lshw-> [https://pastebin.pl/view/871d8c9d](https://pastebin.pl/view/871d8c9d)
#lsmod -> [https://pastebin.pl/view/edec29f6](https://pastebin.pl/view/edec29f6)
#journalctl -p err -> [https://pastebin.pl/view/639befe7](https://pastebin.pl/view/639befe7)

---

### Post by Impavidus on 2020-03-20
To see all those messages instead of the splash screen you can hit escape.

Ubuntu 19.04 has reached end of live and is no longer supported. Install 19.10. It might solve your issue.

---

### Post by guiverc on 2020-03-20
[http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)   (note: depending on which mirror you are using, it may still exist; it may not)

---

### Post by ansgar.snow on 2020-03-20
Pardon my mistake, I am at 19.10 already, not 19.04.
Unfortunately hitting [Escape] does nothing on boot, idk if that freezes that hard or just this feature is not enabled for me.

---

### Post by him610 on 2020-03-20
> To see all those massages instead of the splash screen you can hit escape.
To see them at every boot up, edit */etc/default/grub*. 
Change the line that begins,
```

GRUB_CMDLINE_LINUX_DEFAULT....

```
to read,
```

GRUB_CMDLINE_LINUX_DEFAULT="text"

```
I do this on all of my machines.

---

