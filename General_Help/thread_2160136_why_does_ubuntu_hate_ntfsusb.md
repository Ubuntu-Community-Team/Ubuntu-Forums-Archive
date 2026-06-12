---
title: "why does ubuntu hate ntfs/usb ?"
date: 2013-07-05
forum: General Help
---

### Post by Shadowstripe on 2013-07-05
I wanted a filesystem for my external removable devices that supported large files so I figured NTFS was the way to go because it has support for both windows and linux out ofthe box.

I occasionally run into the same problems on the ubuntu side of things the windows side seems for the most part fine.

1/ sometimes I just get "device it is currently in use" when nothing is writing, any programs using it have been closed, I sometimes just tell ubuntu to reboot (assuming this finishes off anything that is open in a safe manner) (also sync)

2/I press "eject" the device dismounts. I get no other notification, testing with a low capacity stick that has a LED activity indicator shows that sometimes after the device vanishes from the mounted drives list the activity indicator will continue to write for several seconds. my main stick has no LED indicator meaning sometimes I have removed the stick and the last file that was being copied ends up corrupt or lost entirely.

3/folders in Thunar sometimes show up as files, clicking them just brings up a "open this file with" possibly related to #2 although I had it happen random sometimes when I know the device has been scanned and should be fine

I was thinking maybe using ext but it means installing a 3rd party fs driver on windows. Im not sure if any are good / free ones and it also means the driver would have to be installed everywhere I wanted to use the drive making it well not very portable and there's no guarantee that windows will deal with the drive any better that way around.

a quick search did turn up some info on exfat or fat32+ are those supported? would they be any better? (and work out the box on both platforms? I believe ntfs/fat32 are the only format options I get)

anyway ntfs constantly breaking losing files or just not even being able to get into folders unless I eject / insert a drive is getting tiresome, I have had similar issues with 2 different large capacity drives.

I read people saying to stay clear of ntfs on linux is this still the case? (if so it may explain some of my problems)

does ubuntu just hate ntfs? (or usb) would I see similar problems if I  switch to fat32? (4gb limit is borderline deal breaker)

thanks

---

### Post by pqwoerituytrueiwoq on 2013-07-05
i don't recall having issues accessing ntfs partitions in the past 3-4 years ago on ubuntu, i quit using windows
i did find this , if you want a fat32 system it may help
[http://www.techrepublic.com/blog/window-on-windows/format-fat32-drives-beyond-32gb-limit/5693](http://www.techrepublic.com/blog/window-on-windows/format-fat32-drives-beyond-32gb-limit/5693)

also there is this if you are up for kernel compiling
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NTQ)

---

### Post by CharlesA on 2013-07-05
I haven't used NTFS on *nix lately, but the last time I did everthing was fine. Now-a-days I use EXT4 for my external hard drives and FAT32 for USB sticks.

---

### Post by Shadowstripe on 2013-07-05
I have not recompiled a kernel in a long time :P its probably sometime I don't have the time and patience for now.

the other link exfat seems a typical microsoft invention, design something portable that should be open and corss platform and then tie it in enough paitents no one wants to officially touch the thing.

I will probably try fat32 and see if it gives me any problems and probably use a file splitter for the occasional file that exceeds 4gb

thanks

---

### Post by Hylas de Niall on 2013-07-05
No problems at all with ntfs here.

---

### Post by ajgreeny on 2013-07-05
Do you always remove the ntfs drive properly from windows to make sure it is not flagged as "in use" and therefore not mouintable in linux?

---

### Post by Nixarter on 2013-07-05
you can force mount it still, overwriting the naughty byte.  but i have one drive that is NTFS and ubuntu REFUSES to mount it, and I haven't figured out a way around it yet.  I hav rebooted into windows a number of times to make sure t was correctly detached and everything.  Windows has no problems with it at all.  sigh

---

### Post by CharlesA on 2013-07-05
> **Nixarter said:**
> you can force mount it still, overwriting the naughty byte.  but i have one drive that is NTFS and ubuntu REFUSES to mount it, and I haven't figured out a way around it yet.  I hav rebooted into windows a number of times to make sure t was correctly detached and everything.  Windows has no problems with it at all.  sigh

Running chkdsk on the drive usually fixes those type of things.

---

### Post by Shadowstripe on 2013-07-06
never had ubuntu refuse to mount it but often refuses to eject, I converted one of the drives to fat32 will see how it goes.

---

### Post by Shadowstripe on 2013-07-07
did some more testing and it seems to be how ubuntu interacts with either ntfs or removable drives (or just drives ?)

the other day I tried to write a large amount of data (around 10gig) to the drive with the LED that is still using ntfs.

I right click the drive in thunar and press Eject.

the drive icon goes semi transparent, terminal command shows it is also dismounted but ...

the LED on the driver continues to blink for over 2 minutes, after the first several seconds of the LED blinking I did a sudo sync this didn't complete until the drive LED stopped blinking.

shouldn't the UI give me some kind of 'safe to eject device' notification? why is it having to write so much after it is supposed to be dismounted ?

---

### Post by Mark Phelps on 2013-07-07
You talk about the "windows side" of things -- so are Windows and Ubuntu on the same PC?

IF so, are you hibernating Windows when you then boot over into Ubuntu?

On the Windows side, are you running XP, or Win7, or Win8 (which one)?

---

### Post by Shadowstripe on 2013-07-13
sorry I missed that post, didn't realise it was on page 2

2 pcs running nothing but xubuntu, 1 dual boot between win 7 and xubuntu

I have hibernation disabled on windows

something I have noticed, I think removable hard drives always change to a semitransparent icon and stay that way even after sync has finished while flash drives go semitransparent and then vanish entirely after a sync

I have maanged to avoid the problem so far by just being careful when ejecting and running sync to make sure everything is written before removing.

---

