---
title: "Ubuntu bootloader error need help"
date: 2019-05-06
forum: General Help
---

### Post by jwct1995 on 2019-05-06
[COLOR=#1D2129][FONT=Helvetica]After I use this code, Next restart my ubuntu loader gone[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]**sudo nano /etc/default/grub**[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][I]# GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="Ubuntu 15.100"[/I][/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]**sudo update-grub**[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]Now I'm using try Ubuntu without install 
And 
go to volume I install my ubuntu 
***dev/sda10/etc/default/grub***[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]and change it back to original [/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]*GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`*

then save it 

the problem is how can i **update grub** for my original Ubuntu?[/FONT][/COLOR]

---

### Post by oldfred on 2019-05-06
I change my entry just like that and it works:

#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Bionic_18_04'

My menu entry is this:
menuentry 'Bionic_18_04 GNU/Linux' --class bionic_18_04 -

And even my UEFI entry:
Boot0001* bionic_18_04    

But UEFI boot only uses the /EFI/ubuntu/grub.cfg so having the new UEFI entry really does not work as separate entry.

---

### Post by coffeecat on 2019-05-06
Support, not chat.

*Thread moved to **General Help**.*

---

