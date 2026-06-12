---
title: "Command works on command line but not in a launcher"
date: 2013-06-08
forum: General Help
---

### Post by greggc2006 on 2013-06-08
I have a command that I used to use to launch a virtualbox VM with the 'my launcher' gnome shell extension. The command also works in a terminal but when I create a launcher with Alacarte for use in the Gnome shell dock it doesn't seem to work, I briefly see vboxsvc in the process list but no VM is launched and the vboxsvc process drops down the list and dies fairly quickly.

The command looks like:-

```
optirun vboxmanage startvm ~/VirtualBox\ VMs/CAD\ -\ W7/CAD\ -\ W7.vbox
```

I am guessing there is something I need to add to make it work but have no idea what, any ideas???

BTW, the 'optirun' prefix is because I am running on an optimus laptop with bumblebee installed and want my VM to use the Nvidia GPU.

---

### Post by greggc2006 on 2013-06-14
For the benefit of anyone finding this post in search results solution in below thread on LQ:-[URL="http://www.linuxquestions.org/questions/linux-software-2/command-works-on-command-line-but-not-in-a-launcher-4175466054/"]

http://www.linuxquestions.org/questions/linux-software-2/command-works-on-command-line-but-not-in-a-launcher-4175466054/[/URL]

---

