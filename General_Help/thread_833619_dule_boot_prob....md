---
title: "dule boot prob..."
date: 2008-06-18
forum: General Help
---

### Post by illbashu on 2008-06-18
ok so i managed to get windows installed but now grub doesn't boot up so i cant boot into ubuntu...

btw i didn't delete ubuntu, so is there a way i can get a boot screen where i have the option to boot into windows or ubuntu?  


1 more question is there a way to get xp to see linux partation?

---

### Post by iaculallad on 2008-06-18
You need to [restore GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after you installed your windoze OS and you can view/explore Linux partitions (Ext2/Ext3) on windoze using [explore2fs]("http://www.chrysocome.net/explore2fs").

---

### Post by fooman on 2008-06-18
sorry already answered above

---

### Post by illbashu on 2008-06-18
for some reason i cant boot from my cd, it istalled fine but evertime i boot from it to try it out i get this weard desplay error i did the cd check and it came out clean :/... does anyone know what i am talking about?

---

### Post by iaculallad on 2008-06-18
Post us the weird error it displays so we know what we are tackling.

---

### Post by illbashu on 2008-06-19
thx it fixed itself :)

i am getting grub error 15

4. You will get a grub prompt (see below) which we will use to find the root partition and install grub to the MBR (hd0,0)

    *

         [ Minimal BASH-like line editing is supported.   For 
               the   first   word,  TAB  lists  possible  command
               completions.  Anywhere else TAB lists the possible
               completions of a device/filename. ]

      grub>

      Type the following and press enter:

      find /boot/grub/stage1 
grub error 15

      Using this information, set the root device:

      grub> root (hd0,1)

      Install Grub:

      grub> setup (hd0)

      Exit Grub:

      grub> quit

---

