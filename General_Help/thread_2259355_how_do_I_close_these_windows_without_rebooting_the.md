---
title: "how do I close these windows without rebooting the machine?"
date: 2015-01-03
forum: General Help
---

### Post by tcll5850 on 2015-01-03
so I was trying to copy a few videos to my FAT32 flash drives, and what ended up happening was a bunch of copy processes that failed...
so I clicked "Cancel" 1.5 hours ago and the dialog is still up now:

[img]http://lh4.ggpht.com/-8bKrpNM6TJw/VKiNYKtTndI/AAAAAAAAIME/-PIdevSkDA0/s452/copy%2520issue.jpg[/img]

I have other various issues where FAT32 volumes are EASILY corrupted by simply creating folders.

FAT32 is important because the device I have uses software that only reads FAT32 format (32/64bit cluster-size for max load performance)


EDIT:
I should mention that first action has been cancelled as well... the dialog is still open and the actions still won't cancel.
I don't want to restart because I have other programs open, 1 in particular on Wine which will take a day and a half to load my template.

---

### Post by Bucky Ball on 2015-01-03
Have you got a support question? Is it 'how do I close these windows without rebooting the machine?'? If so, I'll change the title of your thread to reflect this.

---

### Post by aysiu on 2015-01-03
Does it take that long even if you copy from the command line?

---

### Post by tcll5850 on 2015-01-03
> **Bucky Ball said:**
> Have you got a support question? Is it 'how do I close these windows without rebooting the machine?'? If so, I'll change the title of your thread to reflect this.

sorry, I kinda did, but didn't want it to be a support Q... heh
I was a little hot-headed, rushed, and stressed while posting, so I was rather confused about what exactly I was posting... /autism

but I guess it's a support Q, so I may as well ask, why does this only happen on FAT32 volumes??

I havn't tried the command line, but I'd assume it'd be the same >.>


in any case, I'd gotten a failed copy error after going out for some pizza due to a lost stream...
so after ejecting the drives, after cancelling the operations, windows (my laptop) now wants me to format the drives, but still manages the data on them.
(the copy window in the first post never changed while doing this)

my SD cards (all FAT32) are also "corrupt" and now have a blank file named after the folder it used to have.


so yea, idk where to begin to describe my issue... heh
but I've been dealing with it for a while, hoping it was a known bug that would get fixed in a short update...


EDIT:
yep, the process is still going...
I'd previously closed the window before getting a mount error (quite a while after removing the drives)...
so yea, I just did a random copy just to copy something, and the same stuff is still going 9_9
is it actually cancelling the processes, or are they already cancelled??

---

### Post by tcll5850 on 2015-01-04
well, I ended up losing control over my mouse, and the thing froze when I tried to hibernate...
ended up having to hard shut-down.

however, that doesn't fix the FAT32 issue...

why does linux and FAT32 not get along?? :/

how can I prevent this very issue from happening in the future??

---

### Post by coldraven on 2015-01-04
I have been using the same 1GB SD card for years to install various Linux distributions. It has also been formatted to NTFS and back to FAT32 with no problems, it still works.
Your problem could be that you accidentally tried to copy a file over 4GB to the device. FAT32 cannot save files that big and you have probably corrupted it.
Try re-formatting, I use gparted but you could use Windows if that is easier

From Wikipedia:
> The maximum possible size for a file on a FAT32 volume is 4 GiB minus 1 byte or 4,294,967,295 (2[SUP]32[/SUP] &#8722; 1)  bytes. This limit is a consequence of the file length entry in the  directory table and would also affect huge FAT16 partitions with a  sufficient sector size.[SUP][[1]]("http://en.wikipedia.org/wiki/FAT_32#cite_note-GB4-1")[/SUP] Large video files, DVD images, and databases easily exceed this limit.

---

### Post by tcll5850 on 2015-01-04
nah, that's known... and the reason I hate FAT32, though I'm forced to use it... heh
that 2GB file you see in the image was actually the largest of the files

I've just recently found out the reason the folders turn into plain files...
I have to hit Eject after I finish copying or working with the partition.

another issue I've had (on my brother's flash drive) is deleting the file doesn't delete the data...
the file system would report there was 8GB free on the drive, but when copying a 2GB file over, I'd get an error saying there wasn't enough space.

only way to fix that is to format the drive...

yea, there's quite alot that goes wrong, and it's only with FAT32
NTFS and any other file system I've tried have no issues (except my brother's exfat HDD which for some reason installing the utilities doesn't work)

perhapse it's just Xubuntu//XFCE

in any case... something's glitching out and being stupid...


so yea... for the things that break FAT32 drives or the interface:
- deleting a file doesn't delete the data (only formatting deletes it)
- removing a drive (w/o ejecting) after managing a folder turns that folder into a file
- after a failed stream error, the dialog chokes and continues to try until you hit 'cancel', and doesn't ever stop cancelling (you can still use the clipboard for other things while this is frozen)
- more that I'm forgetting about (too much has been delt with)

---

### Post by buzzingrobot on 2015-01-04
Use gparted to remove exisiting partitions on the stick, then create a new partition table and format it to fat32. Any time a drive is removed without proper unmounting the filesystem on it can be damaged.

Try the copy from the command line to determine if the problem is specifically with the GUI tool or is more fundamental.

Of course, be sure the drive is mounted before beginning the copy.

---

### Post by Bucky Ball on 2015-01-04
> **buzzingrobot said:**
> Use gparted to ... format it to fat32. 

Sorry for the paraphrasing buzzingrobot, but do that. Reformat the USB/flash/dongle prior to proceeding, preferably with Gparted and not Win machine. You could boot from the Live insall media and launch Gparted, then format the USB dongle to FAT32. Check the drop down menu in the top right of the window. The USB is probably sde or something like it.

---

### Post by tcll5850 on 2015-01-04
alright, next time I need to copy something large, I will

> **buzzingrobot said:**
> Any time a drive is removed without proper unmounting the filesystem on it can be damaged.

I just have to comment, this looks like a -1 on linux's part considering my experience with this stuff.
(I have no problem on windows simply removing a flash drive after all operations are finished, and am rather quite used to it)
^ that's saying something considering linux corrupts it every time if I don't eject... heh

if my avatar doesn't say enough (and I may as well put my foot out because of that),
I do hack my wii, and use DIOS MIOS for GCN (that's the software that specifically requires FAT32).
(no I'm not into the very depths of wii hacking as I don't develop wii software... yet)

but I only wanted to note I do have alot of experience, and considering I'm having problems on linux, yea, something's wrong... :/
(I should mention NTFS and Ext4 work like I'm used to, it's only FAT32 that gives me issues)


but yea, next thing I'll try is the command line :)

---

### Post by buzzingrobot on 2015-01-04
> **tcll5850 said:**
> 

I just have to comment, this looks like a -1 on linux's part considering my experience with this stuff.
(I have no problem on windows simply removing a flash drive after all operations are finished, and am rather quite used to it)


  

Don't forget that Windows and Linux are two different operating systems.  What works in one won't work in the other. I haven't used Windows in more than 10 years, so I'd be rather clueless with a Windows machine.

Drives in Unix/Linux need to be mounted before they can be used, and unmounted before they are physically detached.  Most desktop environments in Linux are configured to automount a drive when it is physically attached, but few, if any, that I've used will automatically unmount when a drive is physically detached, for obvious reasons. Whether or not detaching a drive without unmounting it damages the filesystem on the drive depends on the state the system is in when the drive is detached. Sometimes you're lucky, sometime you're not. 

This mounting/unmounting requirement dates to the beginnings of Unix decades ago, well before DOS/Windows arrived. Obviously, the notion of people carrying drives around in their pockets, plugging and unplugging them randomly, wasn't conceived of then.  Automounting works in Linux.  Whether yanking a drive out before the system (as opposed to the user) is finished is of debatable value, on any OS.

I've generally found USB sticks to be fragile and annoying little things, even shuffling them back and forth among Linux systems. But, zapping the existing partitions and creating new ones with new formatting usually sets things right.

---

### Post by tcll5850 on 2015-01-04
XFCE auto-unmounts them (Gnome too), I can tell you that much... heh

I think I may have crossed the line a small tad there...
it DOES auto-unmount with no issues... just not with FAT32


and from my experience, Sandisk is the indestructable king of removable media (excluding SDs)
I havn't had a single issue abusing sandisk flash drives like I do... lol
SD cards however, that's another story as I have about 5 dead ones by them.

in any case though, what you mentioned about the state is exactly what I'm talking about...
if linux is still busy with the drive after all pending file I/O operations have completed, then that's an issue that shouldn't be discarded.

all I'm saying is FAT32 needs to be either fixed or updated in Xubuntu 14.04


and no, it's not just this compy... I've installed the same setup for my brother to get him off windows... and I'm still getting the same FAT32 issues.
(I got him off windows because MS wants to control people and XP is still dying (developers aren't supporting it anymore and playing MS's game))
^ I say dying rather than dead due to the large number of people who are like me, but havn't moved to linux

Google cracked MS's RAT in Win8 btw, so now google can control any Vista/7/8 (not XP) compy out there, if they ever want to.
(I've taken a delve into windows hacking and did some pretty awesome customizations to XP before hearing about the MS-RAT)

so yea... because windows developers are ignorant, I've switched to linux.

I just wasn't expecting linux to still be a not so user-friendly interface... heh


EDIT:
btw, you might know, a RAT is a black-hat hacking program used to control a host's compy...
I personally hate them and have friends who love using them...
(I slap them around for that over skype... lol)

---

### Post by buzzingrobot on 2015-01-04
> **tcll5850 said:**
> XFCE auto-unmounts them (Gnome too), I can tell you that much... heh



Wouldn't know. I am careful to unmount.  Why, though, automatically unmount a drive that's no longer there? If cached filesystem data hasn't been written to the drive at the moment it's removed, automagically unmounting it informs the system the drive is no longer mounted, but it can't do the impossible: Write filesystem changes back to a drive that's not there. 

Similar example: One of the surprises people often have using dd to write images a to usb stick is forgetting the data is cached.  If I burn a 2-gig image to a USB stick with "dd if=blob.iso of=/dev/sdd bs=4M" the prompt returns in a second or two, which can be seen as meaning the image is successfully burned on the stick.  It isn't.  'Sync' needs to be used to flush the data to the drive, and that can take several minutes.

---

### Post by ajgreeny on 2015-01-04
> **tcll5850 said:**
> I just have to comment, this looks like a -1 on linux's part considering my experience with this stuff.
(I have no problem on windows simply removing a flash drive after all operations are finished, and am rather quite used to it)
^ that's saying something considering linux corrupts it every time if I don't eject... heh
If that is really true I think you have been lucky.  In the past I have corrupted a flash drive in Windows XP by simply pulling it out without using the Remove icon in the panel; I think it also gave an on-screen display saying an "item was not removed properly" or similar; it's so long ago now that I can't remember.

Whatever OS you use you **must unmount or "remove properly"** to be sure not to cause problems.  If you have an NTFS flash drive and do not unmount it properly ity will not mount again in Linux as the filesystem will still flag up that it is mounted and in use.

Remember, Linux is not Windows; they work differently.

---

### Post by Impavidus on 2015-01-04
The difference between Ubuntu and Windows is how quickly it syncs the output the the usb drive. Both systems buffer output to the usb drive, so when the please-wait-while-we-copy-the-data window disappears, the data haven't been written to the usb drive yet. When writing hasn't completed and the drive is unplugged, there will be data corruption, no matter what file system. Windows usually finishes writing only seconds after that window disappears (or much later if it was a large write), but Ubuntu (and I think most Linuxes) do it whenever they think is the right time, at the latest when the user issues the sync command or orders to unmount the file system. This reduces the number of write cycles to the drive, making it last longer (and consume less energy). There is also synchronous IO, which syncs always at once, but this is quite slow and dramatically increases the number of write cycles. These are different mount options. I think that both in Windows and Ubuntu (and Xubuntu etc.) this can be configured, but Windows and Ubuntu use different defaults. The advantage of the Windows way is that improperly removing a drive is less likely to cause file system corruption, but it may still happen.

---

