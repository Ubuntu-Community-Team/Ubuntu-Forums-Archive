---
title: "Won't uninstall"
date: 2007-10-20
forum: General Help
---

### Post by JTPete on 2007-10-20
I could not be more disappointed. I have been trying to migrate to linux for 10 years or so. In the past I have even purchased a boxed cd distro trying to get  something that will run on my machine. So I recently read headlines about wubi and I think perhaps linux will now work or if not I should be able to uninstall this experiment and go back to my xp setup. The xubuntu install through wubi seemed to work fine, only no internet connection. I read everything I could find online, support documents and forums, for a wired connection to a LAN. I ran the network setup app countless times with every possible variable, but no luck. So after many hours of frustration I gave up and tried to uninstall with the wubi uninstaller. only it won't, or it says it does but it is still there eating up 11gb of needed space on my small 40gb hard drive. I used xp's add/remove programs, many times, wubi goes through the uninstall but it is still there. I sure want my computer back. Funny I still wish I could use linux but I guess that's gotta wait till I can afford a new box. 

I use a gateway '00 or '01
P4 1.4 640mb ram
linksys ethernet card

---

### Post by ago on 2007-10-20
> **JTPete said:**
> The xubuntu install through wubi seemed to work fine, only no internet connection.
That's not a wubi issue. But it can generally be fixed. Did you try asking in the support forum? That said you might want to try 7.10 once it's ready.

> So after many hours of frustration I gave up and tried to uninstall with the wubi uninstaller. only it won't, or it says it does but it is still there eating up 11gb of needed space on my small 40gb hard drive.

Is the c:\wubi folder removed? Or do you mean that it is still in the add/remove menu? There is a known bug about the second part which has been fixed in 7.10, but for 7.04 it is necessary to remove the entry manually from the registry, I can guide you through in case. The first issue is more "interesting".

---

### Post by JTPete on 2007-10-20
Thanks for the reply,
Yes the c:\wubi folder is gone and yes wubi still appears in the add/remove menu. I would love to get your help getting my disk space back, and I will be glad to give 7.10 a try if you think I have a shot at making it successful 

Thank you very much,
Pete

---

### Post by ago on 2007-10-20
> **JTPete said:**
>  I would love to get your help getting my disk space back
All your disk space should be available. If you chose to backup your files, you can simply delete wubi-save. As for the add/remove menu, run regedit. The find "H-K-Local-Machine\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi" and delete.

When it comes to networking, ask on ubuntuforums in the appropriate forum and you'll get answers...

---

### Post by JTPete on 2007-10-20
Well I deleted the regedit wubi file and it no longer appears in add/remove programs, I have deleted wubi-save and still I am missing about 11gb  I tried running check disk and fix disk also to no avail 

Any more ideas?
Thanks for trying

---

### Post by ago on 2007-10-20
> **JTPete said:**
> Well I deleted the regedit wubi file and it no longer appears in add/remove programs, I have deleted wubi-save and still I am missing about 11gb  I tried running check disk and fix disk also to no avail 

Any more ideas?
Thanks for trying
I strongly doubt that's because of wubi. The files are either in c:/wubi or c:/wubi-save. There is no black magic. You can check that with treesize or similar. If you still cannot account for your disk space, run an antivirus.

---

### Post by JTPete on 2007-10-20
I run norton system works pro and it is auto updated
I ran the speed disk defrager twice before using wubi 
I had 18.3 gigs free before and 6.9 free now, if I had my instal cd I would reinstal windows however I do not... oh well

---

### Post by RandomSkratch on 2007-10-20
Grab the program called Space Monger or WinDirStat.

They tell you where the majority of your files storage is being used and by what files.

This should help you figure out what's eating up your space

---

### Post by JTPete on 2007-10-21
Cool, I used Space Monger and found the hidden folderc:\Recycler\Nprotect  it had files:
03326489.Dis
03326554.Dis
03326555.Iso
I got back 11.3gb!  Thank you very much, this is very cool,

now I still want to install ubuntu and get it working(connected to the internet) I am thinking of using a disk partition program (maybe paragon partition manager) and doing my own install that way as opposed to using wubi, perhaps its time  I moved on over to one of the general support forums...

Thanks ago and RandomSkratch, it is very helpful to to get your support

---

### Post by RandomSkratch on 2007-10-21
Glad that helped!  Those programs sure have saved me a lot of searching in the past.

I notice those files were in the NProtect folder...  Still using Norton?

I know it's unrelated to Linux but I might recommend switching to a more user friendly and significantly lighter virus scanner such as AVG or Antivir.

Goodluck with installing Linux this time around.

---

