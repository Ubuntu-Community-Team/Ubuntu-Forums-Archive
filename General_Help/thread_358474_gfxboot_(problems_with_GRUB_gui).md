---
title: "gfxboot (problems with GRUB gui)"
date: 2007-02-10
forum: General Help
---

### Post by Beastboy26 on 2007-02-10
> Quote:
Originally Posted by WishMaster View Post
Step1:
download [http://quasarfreak.googlepages.com/g....97-5_i386.deb](http://quasarfreak.googlepages.com/g....97-5_i386.deb)

Step2:
Download a 'theme'. See the first post for this.

Step3:
Remove the old GRUB.
Open a terminal and type:
sudo apt-get remove grub

Step4:
Install gfxboot. Find the downloaded .deb and dubbleclick it. A graphical installer will take over.

Step5:
We are going to move the 'theme' we just downloaded.
Open a terminal, cd to the folder where you downloaded the theme and type:
sudo cp message.suse /boot/grub/
Offcourse "message.suse" can be replaced by the one you downloaded

Step6:
Backup menu.lst and edit the original to use gfxboot.
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
This will open up a textfile.
Insert a new first line that says:
gfxmenu /boot/grub/message.suse
Once again: the message.suse can be replaced

Step7:
sudo su
grub
Now you are in the "grub-console".
grub> find /boot/grub/stage1
(hd0,1) # this is my output, yours may be different, you may even get multiples if you've lots of versions of linux.
grub> root (hd0,1)
grub> setup (hd0,1)
grub> quit

Now we are back in the normal console.
Just 1 more command to go...
take a look at the output. it has the form: (hdx,y)
the x:
0 =a
1 = b
2 = c
....

grub-install /dev/hdxy

An example:
*) if your output was (hd0,1) then what you have to type is: grub-install /dev/hda1
*) if your output was (hd1,6) then what you have to type is: grub-install /dev/hdb6

Get the idea?

Step8:
reboot and enjoy your gfxboot


I followed these steps up to the point where you use the command

grub-install /dev/hda2 #hda2 is what i got from the grub> find /boot/grub/stage1

instead i had to use

grub-install /dev/sda

beause i have a serial ATA hdd ??? anyways it worked ... except for one minor inconvenience... when i try to boot into windoze xp , it just loops back to the grub menu.... any ideas?

---

