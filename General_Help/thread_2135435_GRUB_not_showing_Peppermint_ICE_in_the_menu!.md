---
title: "GRUB not showing Peppermint ICE in the menu!"
date: 2013-04-14
forum: General Help
---

### Post by paradoxcy on 2013-04-14
OS: Ubuntu 12,04
Netbook : Acer Aspire One D270

Hi Friends.

I chose to have Ubuntu 12.04 and Peppermint ICE as a dual boot. Since Installing from the live CD, the option of loading Peppermint OS is not appearing in the menu. On googling another thread ([http://askubuntu.com/questions/171947/ubuntu-does-not-put-fedora-into-grub-menu](http://askubuntu.com/questions/171947/ubuntu-does-not-put-fedora-into-grub-menu)) I found out a way to check if Peppermint is there on my system still. I ran the commands and saw that there is Pepperming OS still installed somewhere on the hard drive. I just don't have a option to boot it. Please find snapshot attached.

Any clues as to how to get back Peppermint into the GRUB menu?

Regards,
Debayan

---

### Post by fantab on 2013-04-14
If you have not installed GRUB or whatever from Peppermint then you have Grub from Ubuntu install, right?

Boot into Ubuntu and MOUNT the peppermint partition '/', then:

```
sudo update-grub
```

Edit: I guess you already tried that. I didn't see the attached thumbnail.

---

### Post by paradoxcy on 2013-04-14
Ha Ha.

Any new tips then

Regards,
Debayan

---

### Post by grahammechanical on 2013-04-14
Do not mind me saying so but you ran those commands in the wrong order. After you installed Grub from Ubuntu in the MBR you than updated the configuration file. Do it the other way around.

```
sudo update-grub
``` ```
sudo grub-install /dev/sda
``` Remember, whenever one of these installs gets a kernel update it may also update the Grub configuration files. The last Grub to be updated and installed into MBR will be the Grub that puts its menu on the screen. So, decide which OS you want to be in control of Grub and be ready to load into the OS and run those two commands again.

Regards.

---

### Post by paradoxcy on 2013-04-14
Ok Graham,

What I want to do is keep ubuntu in control of GRUB.

I will follow your advice though. Just update in case your suggestion changes based on my reply.

And I don't mind anybody correcting me because I am a ubuntu 'virgin'

Regards,
Debayan

---

### Post by paradoxcy on 2013-04-14
Ok. Graham. That did not work. No peppermint on GRUB even after running the commands in the order you suggested.

Regards.

---

### Post by oldfred on 2013-04-14
Your screen shot in post #1 showed grub found it, so it should be on menu.

Best then to see details of what is where, you can run this from you Ubuntu install or a live installer:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

