---
title: "setting nomodeset with Grub"
date: 2013-05-14
forum: General Help
---

### Post by lostinxlation on 2013-05-14
Hi,
I have a machine that has a dual boot configuration with Ubuntu and Slackware and I need nomodeset for both.
For Ubuntu, I can specify nomodeset in /etc/default/grub, but how can I set it for slackware ?
Per my undestanding, modifying /boot/grub/grub.cfg isn't a good idea as it gets overridden everytime Grub gets updated, and one option I can think of is modifying 30_os_prober in a way that automatically includes nomodeset for other Linux in grub.cfg. 
or is there any other way to set nomodeset for other OS' in different partitions ?

---

### Post by fantab on 2013-05-14
Haven't you installed Slackware-Grub to its own partition? If you did then you should be able to edit the grub file from Ubuntu. I don't use slackware, never have but if it uses grub then it will have /etc/default/grub...

my two cents.

---

### Post by oldfred on 2013-05-14
Grub2's os-prober reads the grub.cfg or menu.lst or whatever other systems use to create its boot stanza for that system. Do you have nomodeset in the Slackware settings? 

What boot loader does Slackware still use?
Update, it defaults to Lilo but you can install grub.

did you add nomodeset and update its lilo install. It looks like it might be this but I am not sure.

append=" vt.default_utf8=0"
Lilo installs part of its boot loading into the PBR like Windows. You should be able to chainload to it like you do Windows.

An alternative is just to create your own boot stanza in 40_custom with the nomodeset included. Just copy the entry os-prober creates into 40_custom and add the nomodeset entry to it.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

