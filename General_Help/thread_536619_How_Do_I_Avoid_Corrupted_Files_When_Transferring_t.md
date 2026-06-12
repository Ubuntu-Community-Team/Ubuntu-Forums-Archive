---
title: "How Do I Avoid Corrupted Files When Transferring to Windows?"
date: 2007-08-27
forum: General Help
---

### Post by Eliasj123 on 2007-08-27
Hey,

I'm not really a newbie to Linux, but you could say that I was vacation from it for awhile.  

I really want to use Ubuntu full time (especially after the validation issue they had), but there are still a few apps that I need to use on windows.  The last time I used a Linux machine full time, I had to switch back to windows, but a lot of my data files became corrupted when I transferred them back to windows.  I dual booted from a Dell laptop, then transferred using an external fat32 usb hard drive.  

I REALLY want to avoid losing files again because I need/want to use some files on both OS's.  

So, how can I eliminate or reduce the chances of corrupting files when I need to switch to windows and linux??

I would like to dual boot, then use and external drive for data storage.  I would probably keep a few gigs on a shared fat32  partition.

Thanks,
Elias

---

### Post by apetresc on 2007-08-27
The easiest way would be to take quick CRC or MD5 hashes of the contents, do a copy, check to make sure the hashes are the same, and only then delete the data from the Linux- or Windows-only drive.

But it's really strange that this happened in the first place, it shouldn't have. You should check to make sure the USB card was not in some way broken.

---

### Post by Eliasj123 on 2007-08-28
Thanks Adrian.

I'll definitely do that next time.  Since I've never used CRC or MD5 hashes before, would there be a way to tell which file didn't copy correctly since I might be transferring gigs at a time??

BTW - since the last time, I have a new external hard drive..

Thanks,
Elias

---

### Post by bodhi.zazen on 2007-08-28
Hmmm .... what type of corruption and how did you transfer the files ?

In general transferring files is not a problem. Are you having problems converting files ?

My caution would be that you need to scan any file you transfer from ubutnu -> windows for viruses as this is otherwise a sure fire way to circumvent your windows anti-virus software ...

md5 sums are very easy to check, although I doubt this is a source of problems. md5sums and such are usually used to check the integrity of a downloaded file for example.

Here is how to check md5sums : [http://ubuntuforums.org/showthread.php?t=290339](http://ubuntuforums.org/showthread.php?t=290339)

---

### Post by cwaldbieser on 2007-08-28
> **Eliasj123 said:**
> Thanks Adrian.

I'll definitely do that next time.  Since I've never used CRC or MD5 hashes before, would there be a way to tell which file didn't copy correctly since I might be transferring gigs at a time??

BTW - since the last time, I have a new external hard drive..

Thanks,
Elias

You just run md5sum against the original file and then the copy and compare the output strings.  If the files are identical, they should generate identical hashes.

---

### Post by Eliasj123 on 2007-08-28
> **bodhi.zazen said:**
> Hmmm .... what type of corruption and how did you transfer the files ?

In general transferring files is not a problem. Are you having problems converting files ?

: [http://ubuntuforums.org/showthread.php?t=290339](http://ubuntuforums.org/showthread.php?t=290339)


I forgot the exact errors messages.  But it was something like "invalid format" or "file is unreadable or corrupted".   I just drag'd & drop'd from Linux to the external hard drive, then to windows.  

So, from all the responses, it just like a fluke or was the old hard drive.

Thanks,
Elias

---

