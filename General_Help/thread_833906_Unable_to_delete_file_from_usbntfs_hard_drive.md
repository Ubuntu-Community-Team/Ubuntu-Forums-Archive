---
title: "Unable to delete file from usb/ntfs hard drive"
date: 2008-06-19
forum: General Help
---

### Post by TempestSA on 2008-06-19
Hi

I have a Seagate 500Mg usb drive, it is ntfs. I have a file in the .Trash folder that I can't delete. if I ls -al I can see it:

-rwxrwxrwx   1 root    root    4253554 Jun 13 23:59 Crap Yoga Song That Wont Be Deleted.mp3

If I rm Crap\ Yoga\ Song\ That\ Wont\ Be\ Deleted.mp3 it says the file doesn't exist! 

I've sudo'd, used rm -f, had quotes around it, tried deleting the directory, all to no avail. I don't have Windows to run scandisk. I can move the file around. It's not a serious problem, I'm more dissapointed "sudo rm -f" didn't work and why ls says it exists and rm says it doesn't :confused:

Do I need to start thinking about getting the drive checked/replaced?

Thanks

---

### Post by iaculallad on 2008-06-19
Try doing this instead:

```
sudo rm -rf /media/Your_USB_NTFS_Drive/.Trash/*
```

Or you could directly change directory to that drive and issue:

```
sudo rm -rf .Trash/*
```

---

### Post by cariboo on 2008-06-19
If you really just want to delete the one song, remember linux hates spaces in file names, try:

```
rm "Crap Yoga Song That Wont Be Deleted.mp3"

```

in your trash directory. those are quote marks around the file name.

Jim

---

### Post by TempestSA on 2008-06-19
Hi

I don't have my ubuntu machine with me, I'm sure I've tried this before, and it said it can't delete the file because "it can't find it"...

I will try this tonight and get back to you, thanks

---

### Post by TempestSA on 2008-06-19
> **cariboo907 said:**
> If you really just want to delete the one song, remember linux hates spaces in file names, try:

```
rm "Crap Yoga Song That Wont Be Deleted.mp3"

```

in your trash directory. those are quote marks around the file name.

Jim
Tried that, no go...

---

### Post by TempestSA on 2008-06-21
Hi

Unfortunately nothing worked, I used scandisk (luckily it was a usb hard drive) which picked up the orphaned file and I deleted it. 

I guess this is more of an ntfs (or the ntfs-3g) issue than a filesystem issue.

Thanks in any case

---

