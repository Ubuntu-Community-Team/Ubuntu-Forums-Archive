---
title: "chipset drivers"
date: 2013-04-15
forum: General Help
---

### Post by LinuxUser666 on 2013-04-15
Hello fellow Linux users, I wold like to ask you one question.
I am running on Xubuntu 12.04 LTS on my Acer AspireOne that uses gma500 chipset that is very "specific". But my Wifi card is fully functional, although my BT is not able to share data, it just recognises devices around. 
I found some solutions here [https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h) considering the driver issues.
Problem is I have no bootloader. It does not appear at all and to access the system I must open the console an type in 

```
sudo service lightdm restart  
```

I do not know what to do, please help.

---

### Post by gorkypah on 2013-04-15
...

---

### Post by Hadaka on 2013-04-15
Hi, did you go to /etc/default/grub and add
the options per the link you posted???
*IF YES then you need to update grub..
```
sudo update-grub
```

---

### Post by LinuxUser666 on 2013-04-15
Ok I posted my thread in wrong topic section...:lolflag: thanks for your help. Btw can this be done by upgrading distro version?

---

### Post by LinuxUser666 on 2013-04-15
you mean this? 


# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.GRUB_DEFAULT="0"GRUB_HIDDEN_TIMEOUT=0GRUB_HIDDEN_TIMEOUT_QUIET=falseGRUB_TIMEOUT=10GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem=1908mb"GRUB_CMDLINE_LINUX=""# Uncomment to disable graphical terminal (grub-pc only)#GRUB_TERMINAL=console# The resolution used on graphical terminal# note that you can use only modes which your graphic card supports via VBE# you can see them in real GRUB with the command `vbeinfo'#GRUB_GFXMODE=640x480# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux#GRUB_DISABLE_LINUX_UUID=true# Uncomment to disable generation of recovery mode menu entries#GRUB_DISABLE_LINUX_RECOVERY="true"# Uncomment to get a beep at grub start#GRUB_INIT_TUNE="480 440 1"

Yes I have did that and did sudo update-grub

---

### Post by Hadaka on 2013-04-15
Hi, before you go any further i strongly advise you to
back up your grub file BEFORE any changes,,
```
sudo cp /etc/default/grub /etc/default/grub.old
```
where you put the options from the link you included will not
make a difference as you put them in a line starting with a "#"
attached is a screen shot of where to insert that ONE line.

---

### Post by mikewhatever on 2013-04-17
> **LinuxUser666 said:**
> Hello fellow Linux users, I wold like to ask you one question.
I am running on Xubuntu 12.04 LTS on my Acer AspireOne that uses gma500 chipset that is very "specific". But my Wifi card is fully functional, although my BT is not able to share data, it just recognises devices around. 
I found some solutions here [https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h) considering the driver issues.
Problem is I have no bootloader. It does not appear at all and to access the system I must open the console an type in 

```
sudo service lightdm restart  
```

I do not know what to do, please help.

What you call "no bootloader" is really just a black screen - a known issue with 12.04 and the GMA500.
Check out the [-->wiki page<--]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") for workarounds.

---

### Post by wildmanne39 on 2013-04-17
*Thread moved to **General Help**.*

---

