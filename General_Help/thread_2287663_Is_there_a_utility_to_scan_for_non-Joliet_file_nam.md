---
title: "Is there a utility to scan for non-Joliet file names?"
date: 2015-07-21
forum: General Help
---

### Post by halfbeing on 2015-07-21
Is there a utility to scan for non-Joliet-compliant file names? I need to copy some files to an NTFS volume so that they can be read by Windows. My experience in the past has been that Ubuntu will tolerate non-Joliet file names on NTFS volumes, which causes problems when you attach those volumes to a machine running windows.

---

### Post by TheFu on 2015-07-21
Not that I know.

I'd use **find** with an **egrep** regex to find any *problem* characters.  If the regex became too long, I'd switch to a scripting language that has powerful regex engine like perl, python, or ruby (pick your poison) and write some *extended syntax regex* (following the best practices).

This might help:
$ mkisofs -input-charset help

There are different standards for allowed lengths too, so any utility will have to be flexible. Some stds say support 103 chars, others 110 chars and the document says up to 64 chars.  With non-standard, standards like that, it will be hard to have a tool.

Are you sure that Joilet is what you want and not NTFS? A colon ':' is the main issue there - or at least it has been for me.

---

### Post by halfbeing on 2015-07-21
It's definitely Joliet I need. I got into trouble once before when I successfully copied files to an NTFS volume, but found that Windows got upset when I mounted the volume in it.

Are there any utilities that make it easy to scan for the characters (and also for paths that are too long), i.e. that are specifically designed for the job? Even if I was familiar with regex syntax I'd have to know all the characters to search for. That's quite a lot of work with scope for missing things out by accident and getting frustrated later on.

---

### Post by TheFu on 2015-07-21
Did you look at that tool? mkisofs?

---

### Post by halfbeing on 2015-07-21
You mean copy the files first to an iso image and then to the ntfs volume from the iso image? That might not be a bad idea if I don't come up with anything else.

---

### Post by ElRick on 2015-07-22
There is an option to mount NTFS volumens in order to check names consistencies
It might help you

---

### Post by halfbeing on 2015-07-22
do you mean in the "mount" command? I can't find anything in the man page about this.

---

### Post by ElRick on 2015-07-22
> **halfbeing said:**
> do you mean in the "mount" command? I can't find anything in the man page about this.


Yes, I don't remenber where I found it, but it works, in fact, I have a mount point in mi FSTAB and it work very well

Te option is "windows_names" without the quotes. Here's an example of how I have set in my FSTAB

UUID=diskUUID /mount/point/  ntfs  uid=1000,windows_names,umask=0002,utf8    0    0

the "uid=1000" option let me use the trash can on the NTFS mounted point (I'm the uid=1000)
the "windows_names" option doesn't let me use "bad" names for windows on the NTFS mounted point

I hope it works for you as it works for me..

---

### Post by halfbeing on 2015-07-22
Ah. I see what you mean. The thing is that I do want to be able mount the volume in Linux with the non-Joliet filenames intact so that I can identify them and change them.

---

### Post by ElRick on 2015-07-22
Using pyRenamer might help you, using it recursively you can replace invalid characters ( " * / : < > ? \ |).

---

### Post by halfbeing on 2015-07-22
Thanks for all your advice.

I realise now that I had been thinking about this too narrowly. I was looking to be able to check the file names once they had been copied to the NTFS volume, but of course if I mount the volume with the windows_names option in the first place, then I should be able to copy the files to the volume and get useful error messages for the ones that won't go. I haven't tried it out yet, but I imagine it should work.

---

### Post by ElRick on 2015-07-22
> **halfbeing said:**
> Thanks for all your advice.

I realise now that I had been thinking about this too narrowly. I was looking to be able to check the file names once they had been copied to the NTFS volume, but of course if I mount the volume with the windows_names option in the first place, then I should be able to copy the files to the volume and get useful error messages for the ones that won't go. I haven't tried it out yet, but I imagine it should work.

Of course you will. That is the same exact situation I have and every time I try to copy, backup, rsync, mv, cp, etc, a non-joliet file in my NTFS volume, I get a message error.

Sorry for my english (spanish is my native language)

have pyRename in mind, as I told you before, It let you replace invalid characters (for good ones like _) and if you use it recursively you can replace all of them in one operation.

---

