---
title: "Help Me Install Grub!"
date: 2007-10-13
forum: General Help
---

### Post by ehdtkqorl123 on 2007-10-13
Hi, I was using vista installed desktop.
Today i downloaded ubuntu 7.10 which is unstable for now.
I wanted to use dual booting for vista and ubuntu. so I had sda3 for vista, then I partitioned vista drive so that I could have sda5 for installing ubuntu. After installing ubuntu using sda5, sda6 and sda7 were created. I don't knpw what sda7 does... anyways, after installation, I reboot my computer, and GRUB didn't appear.
So I used live CD to check if grub is installed or not..

so I typed

----------------
sudo grub
find /boot/grub/state1
ERROR: doesnt exist
----------------

so this means when I installed ubuntu, grub was not installed so I couldn't see grub upon booting.

Now when I type 
sudo fdisk-l

I get

/dev/sda1        HPFS/NTFS

/dev/sda2        HPFS/NTFS

/dev/sda3        W95 Ext'd (LBA)                // VISTa

/dev/sda4        HPFS/NTFS                      // partition for back-up purpose

/dev/sda5        HPFS/NTFS                      // empty

/dev/sda6        Linux                               // created after installing ubuntu

/dev/sda7        Linux swap/solaris           // created after installing ubuntu




So I want to install grub by using

sudo grub-install 


However, I have no idea what should follow "sudo grub-install" command.

Also, what does sda7 do?




Summary : Upon the first inatllation of grub using the following command, what should be in (    )? 

sudo grub-install (    );

I believe it should be one of 

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4
/dev/sda5
/dev/sda6
/dev/sda7..


thanks in advance

---

### Post by logos34 on 2007-10-13
typo:

> sudo grub
find /boot/grub/sta[COLOR="Red"]t[/COLOR]e1
ERROR: doesnt exist

should be sta[COLOR="Blue"]g[/COLOR]e1

if you want to use Grub to dual boot vista and ubuntu, mount your ubuntu root partition from the live cd and then do:

sudo grub-install (hd0)

or 

sudo grub-install /dev/sda

either way Grub gets written to MBR

---

