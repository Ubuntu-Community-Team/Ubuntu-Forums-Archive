---
title: "Speak English please"
date: 2016-02-04
forum: General Help
---

### Post by Lloydb39 on 2016-02-04
It would be nice if error messages actually told you something helpful. Every time my backup program runs it fails and says "Error splicing file: Input/output error."  What file? How do I splice it? Can anyone translate this for me so I can attempt to fix it? I'm using Ubuntu 14.04.

---

### Post by mcduck on 2016-02-04
"whatever device the backup utility tried to read from or write to has some problems, and the file couldn't be written".

So, either the device the backup utility is trying to read from, or the one it's trying to write to, isn't connected correctly, doesn't have suitable permissions, is out of free space, has a hardware problem, or possibly file system corruption or pretty much anything else that would make it impossible to write to (or read from).

Check the drive you are backing up to is properly connected, and has enough space available. And if that doesn't help, then check the filesystem and SMART status.

---

### Post by Lloydb39 on 2016-02-04
Thanks. I back up to an old hard drive I put in a case and connected by USB. Only 78 gigs of 120 are used, it says. Permissions allow me to read and write. How do I check filesystem and SMART?

---

### Post by dragonfly41 on 2016-02-04
A simple search brings up these suggestions

[http://askubuntu.com/questions/395806/error-splicing-file-input-output-error](http://askubuntu.com/questions/395806/error-splicing-file-input-output-error)

and in another thread ..

"I get this error message (Error Splicing File: Input/Output Error - Cannot Copy) when I try to copy a file that's bigger than 4GB to a FAT32 formatted memory stick."

---

### Post by mcduck on 2016-02-04
The "Disks" tool should allow you to check SMART status of the drive, filesystem check depends on what filesystem the drive is formatted to. "fsck" in command line would work for Linux filesystems, for Windows filesystems I'd recommend checking them on Windows instead. (Also note that using Windows filesystems could cause problems with permissions, or as mentioned in dragonfly41's link, maximum file size)

Since it's an old drive, it could easly be a hardware issue, every hard drive will break, sooner or later... You could also try switching the cable or USB port it's connected to.

---

### Post by matt_symes on 2016-02-04
Hi

Is the drive formatted with extX file system ? If so then run fsck and check for bad blocks at the same time.

There are similar tools for Windows file systems as well but you'll want to run them from within Windows.

As mcduck suggest, run a SMART test on the disk and post the output back here.

Kind regards

---

### Post by Habitual on 2016-02-04
> **Lloydb39 said:**
> It would be nice if error messages actually told you something helpful. Every time my backup program runs it fails ...
Well, we can say the same about this post, now can't we?
What backup program?

---

### Post by Vladlenin5000 on 2016-02-04
> **dragonfly41 said:**
> 
and in another thread ..

"I get this error message (Error Splicing File: Input/Output Error - Cannot Copy) when I try to copy a file that's bigger than 4GB to a FAT32 formatted memory stick."

Exactly as expected. FAT32 has a single file size limit of 4GB.
Probably not relevant to your case as external HDDs are usually NTFS formated.

---

### Post by Lloydb39 on 2016-02-04
Thanks for all the help guys. Turns out I had two programs backing up, Back In Time and Deja Dup, which was the one having the problem. I removed it and now all seems to be working. The disk is NFTS.

---

