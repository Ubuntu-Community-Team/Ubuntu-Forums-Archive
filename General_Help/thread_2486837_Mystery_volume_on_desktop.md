---
title: "Mystery volume on desktop"
date: 2023-05-13
forum: General Help
---

### Post by lou6 on 2023-05-13
Yesterday a new mystery icon appeared on my Ubuntu 22.04 desktop.  It's labeled "537 MB Volume" but there is no such volume mounted on my system.  When opened it appears to contain the same items as my Home folder but there are no file labels.  I can't delete it.  I'm in the process of making a backup machine for my current working computer (also Ubuntu 22.04) but have had no problems  like this before.  I'd greatly appreciate any and all help...

---

### Post by yancek on 2023-05-13
It might help if you have a smart phone and take a photo of the Desktop and indicate which icon you are referring to when posting it here.

Did you have a flash drive attached and fail to safely remove it?  Do you have only one drive?  Can you post the output of the lsblk command?  Have you rebooted since you first say this?

---

### Post by lou6 on 2023-05-13
I don't have a smart phone so I cannot post a photo

No flash drive has been attached - I have only one hard drive and no other drives are attached - I have rebooted many times since posting

Let me see if I can post lsblk on the new machine - not much has been installed yet so I don't know how I will do it

Stay tuned...

---

### Post by dragonfly41 on 2023-05-13
Try Flameshot app ..

[https://i.imgur.com/FDOzjzf.png](https://i.imgur.com/FDOzjzf.png)

---

### Post by lou6 on 2023-05-13
lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0    7:0    0  63.3M  1 loop /snap/core20/1852
loop1    7:1    0     4K  1 loop /snap/bare/5
loop3    7:3    0  63.3M  1 loop /snap/core20/1879
loop4    7:4    0 241.9M  1 loop /snap/firefox/2579
loop5    7:5    0 349.7M  1 loop /snap/gnome-3-38-2004/137
loop6    7:6    0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop7    7:7    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop8    7:8    0  53.2M  1 loop /snap/snapd/18933
loop9    7:9    0  53.2M  1 loop /snap/snapd/19122
loop10   7:10   0   242M  1 loop /snap/firefox/2667
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /media/lou/74B2-0187
&#9500;&#9472;sda2   8:2    0   513M  0 part /boot/efi
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0 464.8G  0 part /var/snap/firefox/common/host-hunspell

---

### Post by lou6 on 2023-05-13
OK - please see lsblk and screenshot (icon in question is fourth from the top)

Sorry for the lags in posting - I have 2 machines running and the new one is still in development (plus hard to read - no big screen yet).

---

### Post by Holger_Gehrke on 2023-05-13
512 MB in the traditional (1024 based) way are 536,870,912 bytes. Use non-traditional pure decimal ISO units, round it up and you get 537 MB. So the volume on your desktop is most likely /dev/sda1 aka /media/lou/74B2-0187 ...

Holger

---

### Post by lou6 on 2023-05-13
I don't understand why it's showing up where it is.  The machine I'm on now is almost identical and the hard drive is showing as boot and does not have an icon other than Home,,,I hope this is not some strangeness caused by snap.

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0    7:0    0     4K  1 loop /snap/bare/5
loop1    7:1    0  63.3M  1 loop /snap/core20/1852
loop2    7:2    0  63.3M  1 loop /snap/core20/1879
loop4    7:4    0   242M  1 loop /snap/firefox/2645
loop5    7:5    0 349.7M  1 loop /snap/gnome-3-38-2004/137
loop6    7:6    0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop7    7:7    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop8    7:8    0  53.2M  1 loop /snap/snapd/18933
loop9    7:9    0  53.2M  1 loop /snap/snapd/19122
loop10   7:10   0   242M  1 loop /snap/firefox/2667
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0 297.6G  0 part /var/snap/firefox/common/host-hunspell
                                 /
sr0     11:0    1  1024M  0 rom

---

### Post by MAFoElffen on 2023-05-13
+1 on "what" it is... But I have no idea on how it would have gotten added as a folder on the Desktop(???)

That is hard enough to do when you want to do that on purpose, manually. LOL

I'm thinking that there must have somehow been a' .desktop' file added to either '/usr/share/applications/', '/usr/local/share/applications/' or '~/. local/share/applications/'. Those are the folders I would look for that.

---

### Post by lou6 on 2023-05-13
As far as I can see (so far) the new machine seems to working OK - guess I'll continue setting it up and see.  Leaving this open for now...

Here's a further question - where SHOULD the desktop file be and should I remove it from  where it shouldn't be?

---

### Post by yancek on 2023-05-14
I'm using 20.04 and if I right-click on an icon on the Desktop, it will give an option to open with another application.  If you have that, use it or if you have an option to open with a text editor, select that and the Desktop icon should information with a line beginning with 'exec' which will tell the location.  You can also look in the locations mentioned above in the last post by MAFoElffen.

> sda1   8:1    0   512M  0 part /media/lou/74B2-0187 

I see sda2 is your /boot/efi partition but I don't know what the above sda1 is.  Do you have another OS such as windows or did you have it when you purchased the computer and did you create a vfat efi partition during the install of Ubuntu?  sda1 is a vfat partition and may have been the original EFI or another windows partition.  Also, the mount point location (/media/lou) is very unusual for a partition on the main hard drive as that location is generally used for external drives.

---

### Post by lou6 on 2023-05-14
I don't understand why anything should be wrong with this install - I downloaded 22.04 from the Ubuntu website, copied to a usb stick and installed as I have been doing for years.  sda1 the boot partition on this machine (older one) and should be on the new one.  sda2 is the questionable one (the one that shows up as 537 MB mystery partition) and is actually non-functioning as far as I can tell.  I think it should be deleted but I don't know how to do it.

---

### Post by yancek on 2023-05-14
Downloading from the Ubuntu web site is very safe but your download travels over miles of wire and it is possible for it to be corrupted during the download process.  This is why Ubuntu and most other Linux system suggest you do an md5 or shasum on the downloaded iso.  This info is on the web site.  The same holds try for writing to a USB, it is generally safe and successful but there can be unexpected problems.


>  sda1 the boot partition on this machine (older one) and should be on the  new one.  sda2 is the questionable one (the one that shows up as 537 MB  mystery partition) and is actually non-functioning as far as I can  tell.

That seems backward to me.  sda2 shows as your EFI partition which is necessary for an EFI install.  sda1 shows as mounted at /media/lou/74B2-0187 which makes it a vfat partition and being mounted under /media/lou usually means an external drive.
.
>  &#9500;&#9472;sda1   8:1    0   512M  0 part /media/lou/74B2-0187
&#9500;&#9472;sda2   8:2    0   513M  0 part /boot/efi

If you don't solve this soon, you may need to download boot repair from the link below using the 2nd option described on the page and only using the Create BootInfo Summary options.  Do NOT try and repairs but post the link you get when boot repair finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lou6 on 2023-05-14
Not to be argumentative , but this is the lsblk from the machine I am on (also posted earlier) - it has been running fine for a long time.

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0    7:0    0     4K  1 loop /snap/bare/5
loop1    7:1    0  63.3M  1 loop /snap/core20/1852
loop2    7:2    0  63.3M  1 loop /snap/core20/1879
loop4    7:4    0   242M  1 loop /snap/firefox/2645
loop5    7:5    0 349.7M  1 loop /snap/gnome-3-38-2004/137
loop6    7:6    0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop7    7:7    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop8    7:8    0  53.2M  1 loop /snap/snapd/18933
loop9    7:9    0  53.2M  1 loop /snap/snapd/19122
loop10   7:10   0   242M  1 loop /snap/firefox/2667
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0 297.6G  0 part /var/snap/firefox/common/host-hunspell

I appreciate your help but I hope you can see why I'm confused.

---

### Post by lou6 on 2023-05-14
Link from Boot-Repair D9yrjSTd6w

Sorry - it took me a while to setup Boot-Repair and get this posted... thanks for your patience.


Yancek said "If you don't solve this soon, you may need to download boot repair from  the link below using the 2nd option described on the page and only using  the Create BootInfo Summary options.  Do NOT try and repairs but post  the link you get when boot repair finishes here."

Believe me, Sir - If I knew how to solve this I would not have posted here.  I genuinely DO NOT know how to solve this and am asking for help from those wiser than I.  If my pointing out that the machine I have been using for several years seems to contradict some of what you have said, I did not intend to insult you.

---

### Post by lou6 on 2023-05-17
The person who has been helping me has stopped responding - I hope yancek is okay.  

I decided to click on the top result in Boot-Repair to see what would happen (after creating a bootable usb stick and enabling UEFI, etc.) the result was shown on my screen: "GRUB".  I'm not sure what to do with that...

The machine in question is still working normally (except for the phantom item on the desktop).

I hope someone more experienced with the inner workings of Ubuntu will help.  Thank you.

---

### Post by yancek on 2023-05-18
I'm confused also as you can see by looking back at post 5 and then post  8 and 14, the output is different.   In post 5, the output of lsblk shows sda2  as /boot/efi and post 8 and 14  show sda1 as /boot/efi as does the output from  your most recent post.

This is unusual as another member  indicated earlier as the developers of Gnome/Nautilus do not like  Desktop icons and in recent releases of Ubuntu, make it difficult to  create one.
Have you tried the earlier suggestions to open the icon  Desktop file in a text editor or right click on it and select  properties? 

As I mentioned before, if the mount point is in  /media/lou then it should be referring to an external device.  Have you  tried removing it as root user (using sudo)?  As a guess, it may have been a partition on a usb device you had attached at some point and was not properly unmounted.

---

