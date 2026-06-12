---
title: "Nautilus hangs when copying multiple files from computer to Android phone"
date: 2014-01-23
forum: General Help
---

### Post by Paddy Landau on 2014-01-23
I plug my Android phone into my computer using a USB cord. The connection takes place over MTP, for which I had to install [FONT=lucida console]libmtp-runtime[/FONT] from PPA [FONT=lucida console]langdalepl/gvfs-mtp[/FONT].

On my computer, I can use Nautilus for the phone just fine… with one important exception.

[LIST]
[*]I can create or delete files on the phone. 
[*]I can copy or move files from the phone to my computer. 
[*]I can copy or move one file at a time from my computer to the phone. 
[*]But, if I copy two or more files at a time from my computer to the phone, no file is copied, and Nautilus's copy dialogue hangs during transfer of the very first file. I have to force a reboot ([FONT=lucida console]sudo reboot now[/FONT]) in order to cancel the command. 
[/LIST]
 I can copy multiple files using the command line. I get errors, but the copy proceeds fine anyway:
```
$ [COLOR=#0000ff]cp --no-clobber --recursive ABBA/ '/home/paddy/.gvfs/mtp/Internal storage/Music/'[/COLOR]
cp: preserving permissions for `/home/paddy/.gvfs/mtp/Internal storage/Music/ABBA/Arrival': Operation not supported
          :          :          :
```(I have no idea what the error means. I tried adding [FONT=lucida console]--no-preserve=all[/FONT] and [FONT=lucida console]--one-file-system[/FONT], but they make no difference. However, as the copy works anyway, I'm not concerned about this — although I'd love to understand the error message; Google has not helped me here.)

The important thing is: Do you have any idea what I can do to resolve the problem about Nautilus hanging? I'd rather use Nautilus than the command-line.

Ubuntu 12.04 64-bit fully updated.

Thanks

---

### Post by stierwascher2 on 2014-02-09
Hi,
Want to join Paddy. I have pretty the same issue running Ubuntu 12.04 64bit fully updated on my MacBookAir. Only difference is, that copying multiple files, on my side 2 files are being copied to my Samsung Galaxy Note 2 and then Nautilus hangs. (folders are sucessfully created)
Didn't find a solution till now except dismounting the SDcard from the phone and plug it directly into my computer.
Looking forward to any hint!
many thanks

---

### Post by Paddy Landau on 2014-02-10
Unfortunately for me, my phone is a model that doesn't allow a removable SSD. So, I have to use USB to the phone.

I wonder if this problem has anything to do with the version of Android? I have version 4.4.2. What version do you have?

---

### Post by eagleton on 2014-02-10
For me, MTP started to work reliably under Ubuntu 12.10, for which the above mentioned PPA has a more recent version of libmtp. With 12.04, I've had similar problems that were resolved when I upgraded to 12.10. I have a Nexus 4, but I'm not sure if the problems I faced only appeared on the most recent version of Android.

---

### Post by Paddy Landau on 2014-02-10
I decided to test this on the latest version of Ubuntu, 13.10 64-bit fully updated.

This works.

Therefore, the fault lies with 12.04 or the version of Nautilus ("Files") on 12.04. I shan't raise a fault report, because 14.04 comes in just a couple of months.

---

### Post by reloweb on 2014-11-08
> **Paddy Landau said:**
> I decided to test this on the latest version of Ubuntu, 13.10 64-bit fully updated.

This works.

Therefore, the fault lies with 12.04 or the version of Nautilus ("Files") on 12.04. I shan't raise a fault report, because 14.04 comes in just a couple of months.

Hi, sorry for opening an old post but I've got Ubuntu 14.04 and I'm able to reproduce your problem. Anyone knows how to fix it?

---

### Post by Paddy Landau on 2014-11-08
> **reloweb said:**
> Hi, sorry for opening an old post but I've got Ubuntu 14.04 and I'm able to reproduce your problem. Anyone knows how to fix it?
I always use the command line as a workaround. I don't think that I even tested this on 14.04.

---

