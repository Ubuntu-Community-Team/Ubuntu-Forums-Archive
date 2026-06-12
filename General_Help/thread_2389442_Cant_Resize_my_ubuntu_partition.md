---
title: "Cant Resize my ubuntu partition"
date: 2018-04-17
forum: General Help
---

### Post by cyberartech on 2018-04-17
i have dual boot ubuntu and windows.

i've got unallocated space by decreasing windows partition sda4 100gb.

Im facing problem that i Cant Resize my ubuntu partition. 

i have tried many solution from google and forum.
and i have tried many things and still can solve my problem.

-i'm trying on ubuntu live usb
-swap already swapoff
-all disk unmounted
still cant resize add unallocated for my ubuntu partition

here is some some SS from my laptop

-my partition in gparted
[https://drive.google.com/file/d/10XrjqMji4jkFYSxBCK91DZL4dWIOHcS-/view](https://drive.google.com/file/d/10XrjqMji4jkFYSxBCK91DZL4dWIOHcS-/view)

-i cant resize extended sda2
[https://drive.google.com/file/d/1S1rKK65Xjk7Lsr8zExX3-GjMLHrkKpya/view](https://drive.google.com/file/d/1S1rKK65Xjk7Lsr8zExX3-GjMLHrkKpya/view)

-i cant resize ubuntu partition sda5
[https://drive.google.com/file/d/1YsWBtBXGF6DYiRqrOLI3jWEgmxDWKGJ2/view](https://drive.google.com/file/d/1YsWBtBXGF6DYiRqrOLI3jWEgmxDWKGJ2/view)

---

### Post by Impavidus on 2018-04-17
Your sda3 is in the way, you have to move that first. I don't know what your sda3 is. Maybe a Windows boot partition or something like that? I don't know if that's safe to move or may damage Windows.

---

### Post by Mark Phelps on 2018-04-17
For moving sda3, I recommend the use of a third-party Windows partitioning tool known as Minitool Partition Wizard. This is a free partitioning tool and you should download their Boot CD ISO file to a local drive.
 
You can get it from here: [http://downloads.tomsguide.com/MiniTool-Partition-Wizard-Bootable-CD,0301-51034.html](http://downloads.tomsguide.com/MiniTool-Partition-Wizard-Bootable-CD,0301-51034.html)
 
Once you have this, you have a choice of media to create:
1) If you can boot from CD, download and install ImgBurn and use the Write Image to Disk option to create a bootable CD.
2) If you can boot from USB, download and install RUFUS and use the option to create a bootable USB stick from the ISO file.
 
Boot your PC with the media you created. You should now be able to do partition changes without problems.
 
Good Luck

---

### Post by cyberartech on 2018-04-17
> **Impavidus said:**
> Your sda3 is in the way, you have to move that first. I don't know what your sda3 is. Maybe a Windows boot partition or something like that? I don't know if that's safe to move or may damage Windows.

 thats the problem. im looking for this solution for 3 days surfing the internet. now it works perfectly. thank you so much

---

