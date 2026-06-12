---
title: "How modules get loaded?"
date: 2008-07-07
forum: General Help
---

### Post by amba on 2008-07-07
Hi all,
 some time ago i bought an HP laptop, and managed to get sound working (including headphone) by adding this line to /etc/modprobe.d/alsa-base:
 
```

options snd-hda-intel model=hp

```

Then i tricked a bit whole distro in order to get wlan/wacom tablet/ecc to work.
 Now headphone works no more, but laptop sound boxes are fine.
 Just to be sure that distro updates didn't break something, i reinstalled whole kubuntu in other partition, edited ONLY alsa-base with below line, installed all the updates and it still worked.

In the broken partition, alsamixer doesnt shows headphone volume control, just only activated switch. In the new working partition, alsamixer headphone doesnt show a switch, but correctly a separate volume control entry. 
 
 My question is:
 What the hell did touch in the configs? Which config files may be overriding my custom option in alsa-base at boot?
 
 Note: 
 /etc/modules here is same as the new fresh working install. Must look somewhere else.
md5sum of /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko are same in both installs off course.
 
 Thank you very much for patience with a chaotic newbie  :)
 I would like to fix this in the old ubuntu partition, rather than get the new install ready for complete use...

---

### Post by amba on 2008-07-07
after many many many reboots, and switches between old and new install, now old kubuntu works. No clue how it happened.
I was md5sum-ming all the /etc files and home hidden folders.
Still curious what happened :confused:

---

