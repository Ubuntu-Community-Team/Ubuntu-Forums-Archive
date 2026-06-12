---
title: "Help to reinstall grub needed"
date: 2006-12-17
forum: General Help
---

### Post by Russty of Oz on 2006-12-17
HI!

I have had to reinstall windows and now I need to reinstall grub.  I have searched the forum and found what is suppose to work, but I just get this:

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

What am I doing wrong?   

This is what my HD looks like.

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2028    16289878+   7  HPFS/NTFS
/dev/hda2            2029        6378    34941375   83  Linux
/dev/hda3            6379        9950    28692090   83  Linux
/dev/hda4            9951        9964      112455    5  Extended
/dev/hda5            9951        9964      112423+  82  Linux swap / Solaris

---

### Post by tommcd on 2006-12-17
You can reinstall with a live CD like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Or with the alternate CD like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
If that don't work then get a super grub disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
hope this helps.
EDIT: I guess you may have tried this already. But the super grub disk should work.

---

### Post by Russty of Oz on 2006-12-17
Thanks, I will have to look at all that tomorrow now.

---

### Post by Russty of Oz on 2006-12-18
Well, I have spent hours trying all those things, even super grub.  I still get the grub list at boot up but when I select linux, I keep getting the same "Error 15 : file not found" ](*,) :confused: 

Is there anything else I can do?  Perhaps uninstall grub and try to install it again perhaps??  

Any help would be much appreciated as I can't use my Kubuntu at the moment.  :(

---

### Post by Russty of Oz on 2006-12-18
*bump*

---

### Post by ayoli on 2006-12-18
i have to reinstall grub in the past , i used this guide:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)
it worked

---

### Post by Russty of Oz on 2006-12-18
I have tried that several times but still no luck:( 

Any other ideas anyone?

---

### Post by Russty of Oz on 2006-12-18
Is there someway I can copy my whole linux partition and reinstall it??

Just wondering.

---

### Post by croppyboy on 2006-12-18
I just installed Vista Business about a week ago (over an XP install) and had to reinstall grub . . . I used this guide [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")and used the Super Grub method . . . it worked liked a charm . . .

---

### Post by Russty of Oz on 2006-12-19
I have now tried everything but the only thing that has worked is using super grub, I chose the option to "boot linux directly" and I was able to use my Kubuntu at last.  However, I have also tried the fix MBR thing and it said it was successful but when I boot it still says Error 15 can't find file.   :confused: 

So does anyone else have any suggestions?   Otherwise the only way I can boot Kubie is to use the super grub cd.  

:-k

---

### Post by ciscosurfer on 2006-12-19
> **Russty of Oz said:**
> I have now tried everything but the only thing that has worked is using super grub, I chose the option to "boot linux directly" and I was able to use my Kubuntu at last.  However, I have also tried the fix MBR thing and it said it was successful but when I boot it still says Error 15 can't find file.   :confused: 

So does anyone else have any suggestions?   Otherwise the only way I can boot Kubie is to use the super grub cd.  

:-kI would take croppyboy's advice above and use this link to reinstall GRUB to your MBR: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Russty of Oz on 2006-12-19
OK, I have gone through that again and tried to mount my linux partition, and now when I boot into linux it says **Error 22 Partition does not exist**  ](*,)

I can't use the Alternate CD as I always get "signal out of range" 

SIGH! :(

---

### Post by bodhi.zazen on 2006-12-19
Which partition is your root partition?

Installing grub is not too hard, you are very close.

Assuming your root partition is /dev/hda2:

First boot to your HD (with the super grub disk)

Open a terminal.

```
sudo grub
```Brings you to the grub prompt.

Type:```
root (hd0,1)
setup (hd0)
quit
```

If your root partition is /dev/hda3, same thing ...
At the grub prompt:```
root (hd0,2)
setup (hd0)
quit
```

Reboot and you should be good to go :)

---

### Post by Russty of Oz on 2006-12-20
My linux is hda2 so I did all that and put in root (hd0,1) then setup (hd0) but it still wont boot.

It looks as though I am going to have to do a total reinstall :(

---

### Post by Russty of Oz on 2006-12-20
Could it be that I need to mount my linux partition?  How do I do that?  Or how do I find out if it is already mounted?

---

### Post by bodhi.zazen on 2006-12-20
> **Russty of Oz said:**
> Could it be that I need to mount my linux partition?  How do I do that?  Or how do I find out if it is already mounted?

Perhaps yes.

To see if it is mounted:

cat /etc/mtab

Unless you mounted it, however, it is not likely to be mounted.

To mount:```
sudo mkdir /media/ubuntu
sudo mount /dev/hda2 /media/ubuntu
```

and re-install grub.

---

### Post by Russty of Oz on 2006-12-20
Thanks, I will give that a try later. :)

---

### Post by Russty of Oz on 2006-12-20
> **bodhi.zazen said:**
> Perhaps yes.

To see if it is mounted:

cat /etc/mtab

Unless you mounted it, however, it is not likely to be mounted.

To mount:```
sudo mkdir /media/ubuntu
sudo mount /dev/hda2 /media/ubuntu
```

and re-install grub.

Well I tried all that but when I try to boot it now says Error 17 Cannot mount partition

SIGH:-? 

It looks as though I just have to boot it from the super grub disc every time.  :(

---

### Post by holdinout on 2006-12-20
Would the GRUB super boot help me? See: "Help! Can't load OS (3rd post)"

---

### Post by Russty of Oz on 2006-12-20
> **holdinout said:**
> Would the GRUB super boot help me? See: "Help! Can't load OS (3rd post)"

I think it should help, as you can tell it to boot windows only if you want.  I used it to get windows to boot on its own so I could then try to reinstall grub, it worked fine for windows, it was just like it was the only OS there, it booted straight into it.  So use Super Grub and choose the windows option.

---

