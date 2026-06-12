---
title: "[SOLVED] error 15: file not found (Missing boot file)"
date: 2008-06-24
forum: General Help
---

### Post by Fatal Equinox on 2008-06-24
Hello,

My Linux froze after the last update and when i force restarted it it i got an error 15: file not found on "find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

I am running 8.04 hardy heron through wubi. Is this a wubi issue or a Ubuntu issue? How do i fix it? Is there a way to insert a copy of this file in the same directory? Or any idea where to search for a solution works also.

Thank You

---

### Post by tawnos on 2008-06-24
I have this same issue except its from a fresh install of Ubuntu through Wubi onto a separate hard drive.

---

### Post by ago on 2008-06-24
Please use 8.04.1, see the sticky thread
Note that it will require a new ISO (8.04.1)

Please comment whether the new Wubi fixes the issue for you

---

### Post by Fatal Equinox on 2008-06-24
> **ago said:**
> Please use 8.04.1, see the sticky thread
Note that it will require a new ISO (8.04.1)

Please comment whether the new Wubi fixes the issue for you

So i need to wipe off wubi and all my files?

---

### Post by tawnos on 2008-06-24
So I should download the latest Ubuntu and use that with the Wubi install instead of letting Wubi download Ubuntu for me?

---

### Post by ago on 2008-06-24
@Fatal Equinox, in your case it is more likely that the fs got corrupted, run chkdsk /r from windows and see if there are any hidden files in windows C:\ or C:\ubiquity called "found000*"

@tawnos, download wubi 503 then let wubi download the ISO for you. Please let me now if it works.

---

### Post by tawnos on 2008-06-24
Thank you for your help. Will try tonight.

---

### Post by Fatal Equinox on 2008-06-24
> **ago said:**
> @Fatal Equinox, in your case it is more likely that the fs got corrupted, run chkdsk /r from windows and see if there are any hidden files in windows C:\ or C:\ubiquity called "found000*"

@tawnos, download wubi 503 then let wubi download the ISO for you. Please let me now if it works.

Yes I have a hidden folder called found.000>dir0000.chk>boot(folder) , shared(folder), swap.disk(file)

boot>grub> and here is the menu.lst file   only it is named   "menu.lst~"    

what should i do?  take out the tild ~?

---

### Post by ago on 2008-06-24
if there isn't any other menu.lst sure

---

### Post by Fatal Equinox on 2008-06-24
> **ago said:**
> if there isn't any other menu.lst sure

You right, I just noticed there is a another menu.lst  'visualstudio.lst.9.0"   meh,there goes my c++ habit to ignore anything with a visual tag on it. 

Sorry for the stupid mis sight on my part. What should my next step be?

---

### Post by ago on 2008-06-24
Well restore the files from the found000 dir to their original place

---

### Post by Fatal Equinox on 2008-06-24
> **ago said:**
> Well restore the files from the found000 dir to their original place

Thanks that helped fix that issue, however now the actual kernel seems to be missing.

[PHP] Booting 'Ubuntu 8.04, kernel 2.6.24-19-generic'

Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=E6E04487E0445FC3 loop=/ubuntu/disks/root.disk ro quiet splash

Error 15: File not [/PHP]

is there anyway to fix this?  looks like a pretty big problem to my noobish eyes.


*Edit*
Is this also a matter of just simpling taking the files from the found.000 file and placing them where they belong?     

Do they belong in the c:\ubuntu\install\boot directory?  Because i placed all the version of the vmz generic file back into the directory along with all the files found in the corresposnding boot file within the found.000 file in the c:\ directory and it is still missing 'vmlinuz-2.6.24-19-generic'.

However there are two extra files in the ubuntu boot folder. 'initrd.gz' and 'vmlinuz'  are these two needed or can i delete them and check and see if it boots after that?

---

### Post by ago on 2008-06-24
> **Fatal Equinox said:**
> Thanks that helped fix that issue, however now the actual kernel seems to be missing.
However there are two extra files in the ubuntu boot folder. 'initrd.gz' and 'vmlinuz'  are these two needed or can i delete them and check and see if it boots after that?

You can use those 2 to boot, but you will have to append an entry to menu.lst that points to those 2 files. Then you can reinstall the kernel once in ubuntu to get the latest version. The most important file though is /ubuntu/disks/root.disk. Hope it's in there somewhere.

---

### Post by Fatal Equinox on 2008-06-24
> **ago said:**
> You can use those 2 to boot, but you will have to append an entry to menu.lst that points to those 2 files. Then you can reinstall the kernel once in ubuntu to get the latest version. The most important file though is /ubuntu/disks/root.disk. Hope it's in there somewhere.

oh,  that sucks... I have no disks folder at all.  Where could have the c:\ubuntu\disks  folder gone?   is there a way for me to copy these files from some where and create this folder?

Is there anyway to boot into ubuntu through a live cd?

Because all i really want to do is get some of my files off and then i can either re-install via wubi or do a straight partition install.

---

### Post by ago on 2008-06-24
provided you can find a big root.disk file somewhere that does not matter. You can manually create a /ubuntu/disks folder and put there all *.disk files you find as wells as boot/grub/menu.lst boot/vmlinuz boot/initrd.gz

---

### Post by Fatal Equinox on 2008-06-24
> **ago said:**
> provided you can find a big root.disk file somewhere that does not matter. You can manually create a /ubuntu/disks folder and put there all *.disk files you find as wells as boot/grub/menu.lst boot/vmlinuz boot/initrd.gz


Ok i created the ubuntu\disks folder and added the three (boot/grub/menu.lst boot/vmlinuz boot/initrd.gz) files.  I found a 'swap.disk'  but thats all i found in 'found.000'

on the live disk there is a  .disk folder with  .disk\casper-uuid-generic  and lesser files (info, release_notes_url)  however thats not a .disk like you suggest. 

Its a 8.04-desktop-i386.iso live CD by the way. 

Do i still have to go into menu.lst to direct it to boot from vmlinuz and initrd.gz. Not necessarily sure how to do that.

Thanks for all the help by the way.

*edit*
I am also curious as, the fact that my Ubuntu folder is only about 1.8 gigs when  I had at least 10-15 gigs worth of content on it.  Does that mean i lost everything? and should just start over?

---

### Post by ago on 2008-06-24
yes all the interesting stuff is in root.disk, that is the one you need.

---

### Post by Fatal Equinox on 2008-06-27
just ended up re-installing wubi

---

### Post by digitalggs on 2008-07-08
Maybe too late for this but I use a remarkable tool to recover files from NTFS after they have been lost/deleted. I have it up on my site but you will have to pay for a lic to actually recover the files, If I remember you can browse for files but not recover them w/o lic. there are ways around paying for it though if you are clever enough. The bad news is that if you wrote over those sectors the data is lost forever. 

[http://digitalggs.com/DGGS/filez/utility/RecoverMyFiles-Setup.exe](http://digitalggs.com/DGGS/filez/utility/RecoverMyFiles-Setup.exe)
(I used this once to recover 60GB of MP3s and movie files for a client).

---

### Post by ohCanada on 2008-08-23
I have this problem running Xbuntu from a wubi install inside Vista home basic.
Found all files (even the root.disk) in dir000.chk and moved them back to where I thought they should be in the /ubuntu directory within Vista as per above posts. But when I tried to restart I get past intial grub then get "warning unrecognized partition table for drive 81. please rebuild using fdisk tool (err=1) current C/H/S = 6471/255/63
starting cmain ().."

and then the next few restarts only "starting cmain"
both flicker and nothing happens...

any clever ideas?
Thanks in advance,
-A

---

### Post by ohCanada on 2008-08-24
nevermind! Figured it out. Had to put the /boot file inside the /disks directory that I created not alongside it. After that everything worked like a charm again. To open the found.000 file had to just type in the location into explorer as it doesnt show up normally even with show/hide hidden folders selected in vista.

---

