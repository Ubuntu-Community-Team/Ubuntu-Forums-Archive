---
title: "Stuck during 12.04 update with Configuring grub-pc"
date: 2013-08-26
forum: General Help
---

### Post by UltraAnders on 2013-08-26
I've just booted my desktop for the first time in about 45 days. First thing I did was is to run an update and now I'm stuck.

This is the prompt:
[[img]http://s20.postimg.org/68nonxfdp/grub_pc.png[/img]](http://postimage.org/)[[img]http://s20.postimg.org/a7kw6r40t/Help.png[/img]](http://postimage.org/)
... I haven't removed any drives! I tick my primary drive /dev/sda/, click forward and I get this:
[[img]http://s20.postimg.org/rjl8s6xi5/Continue.png[/img]](http://postimage.org/)[](http://postimage.org/app.php)[img]http://s20.postimg.org/qwmc2o0m5/Help_2.png[/img][/url]
If I click forward without ticking the "Continue without install GRUB" box, I'm back to the first screen. I thought this prompt was telling me I need to (re-)install grub, but the only option to continue **without** install grub :confused:

I've tried ticking /dev/sda/, /dev/sda5 and /dev/sda6 individually and all together.

What should I do please? It seems I don't really have any choice but to continue without installing GRUB??

---

### Post by UltraAnders on 2013-08-26
So that I could get on with my day, I ticked "Continue without installing GRUB?" the Forward. I then let the rest of the update install.

Before restarting, I followed the instructions here: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System), and ran these from the command line:
```
sudo grub-install /dev/sd**a**
sudo update-grub
```Substitute the "**a**" for whatever drive you want to install grub onto.

---

### Post by grahammechanical on 2013-08-26
And? What is the problem now? Does it reboot and do you get to a desktop? I cannot explain why the first box appeared but I guess that as the MBR of sda was ticked as the location (/dev/sda) and not a partition then the utility wanted to confirm that it was not required to install Grub somewhere else. The message was not necessary meaning that Grub need to be re-installed. Only that you had been given an opportunity to change the location and would you confirm that you choose not to change the location by ticking Continue without installing Grub.

By running those two commands you re-installed Grub to the MBR of sda and you updated the Grub configuration files so that any mismatch between the disks/partition's UUIDs (Unique Identifier) mentioned in the second message is avoided.

Are their problems now?

Regards.

---

### Post by UltraAnders on 2013-08-30
No problems. I'm not sure if there would have been a problem if I didn't run those commands. I wanted to be sure though before I rebooted.

After more searching, could it be this issue first reported in 2010?
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/580408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/580408)

---

