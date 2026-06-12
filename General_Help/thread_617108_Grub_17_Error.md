---
title: "Grub 17 Error"
date: 2007-11-19
forum: General Help
---

### Post by amunimanghi on 2007-11-19
Hello,

I recently had to install Windows XP again so I did. Everything went fine for that. Then, I forgot that windows changes the mbr to set itself to automatically boot as the default. My hard drives are setup like this:

1st hard drive: Windows xp (1 partition)
2nd hard drive: Linux (3 partions)

I booted up my live cd of ubuntu and got to a terminal. There i entered these commands:

sudo -i
grub
root (hd1,0)
setup (hd1)

That allowed me to boot using my 2nd hard drive as the default. As grub loaded up, I hit enter to boot into ubuntu and i got the infamous 'grub error 17' message. The weird thing is I can enter the command line of grub and type the following:

kernel /boot/*kernel image*
initrd /boot/*initrd image*
root /dev/sda1

It will then boot but it will freeze after some moments. The freeze has something to do with loading some removable media stuff. That doesn't concern me because ubuntu used to work fine until windows screwed up the mbr. Any idea on how to fix this? By the way, I tried the grub-install --root-directory blah method and that didn't work. I am in windows now and have the ability to access my Linux hard drive through that. Thanks in advanced.

---

### Post by meierfra on 2007-11-19
It seems that you have two different problems. 

To  fix the "error 17" you need to edit the file "boot/grub/menu.lst"  You said you can access the ubuntu partition from Windows. So open the file. Change all the "root (hd1,0)" statements to "root (hd0,0) "  (Since you were  using /dev/sda1 and (hd1,0) I assume that ubuntu is on the first partition of its drive,  If ubuntu is the x+1 partition, you might have to change all root (hd1,x) to (hd0,x) instead.)


This should take care of the "error 17", but it probably won't solve the freezing.

---

