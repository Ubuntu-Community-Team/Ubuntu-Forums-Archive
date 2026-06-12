---
title: "Default to command line boot in 12.10"
date: 2013-01-01
forum: General Help
---

### Post by thetomcraig on 2013-01-01
Hey can anyone help me make my Ubuntu 12.10 machine boot to command line by default?  All the help I have found was outdated.

---

### Post by haqking on 2013-01-01
edit /etc/default/grub with editor of choice such as gedit or nano

```
gksudo gedit /etc/default/grub
```

find this line
```

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

change to

```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”
```

```
sudo update-grub
```

This should work unless something has changed in 12.10, I cant say categorically as i dont use Ubuntu.

Peace

---

### Post by JiuJitsu500 on 2013-01-01
I'm pretty sure haqking is right, that's how it's worked for a long time. Note that you'll have to use nano, not gedit, once you get into text-only mode. I'm also sure that since you want to get there at boot, you most likely know that. Or, you're an insane man on a text-based rampage... 

I'll try it on a VM real quick, gimme a minute.

*EDIT yup, nothing's changed.

---

### Post by thetomcraig on 2013-01-01
Yes this worked! Thanks, you guys are awesome.

---

