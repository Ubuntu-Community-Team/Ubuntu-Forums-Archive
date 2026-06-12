---
title: "Recovering from a disk crash."
date: 2006-08-10
forum: General Help
---

### Post by xmastree on 2006-08-10
So,the other day my PC wouldn't boot. After the brown ubuntu logo appeared, the second event would fail. I think it's mounting something.
Anyway, the filesystem just didn't seem to be there. :-({|= 

I booted from a Puppy CD and fdisked it back to life again, but a couple of things aren't quite right.

Firstly, the login screen. I use the 'select your name from the list' one, it still works but the background image is gone.
Secondly, and more importantly, my firefox is broken. Not seriously, but the search engine thing at the top right is broken. None of the options are there, and I can't add anything from [here]("https://addons.mozilla.org/search-engines.php") either.

I tried to completely remove it, and reinstall, but by bookmarks and history were still there, so it didn't really *completely* remove it, did it?

The only other problem I saw was with some gnome games. Reinstalling the package fixed that.

How can I fix my firefox search engines?

---

### Post by Paerez on 2006-08-10
I would boot your puppy cd and run fsck on your main partition. It sounds like your hard disk had some corruption which broke the boot process, and corrupted a few applications. Hopefully fsck will find and fix some errors. Then I would re-install firefox.

Also, BACK UP YOUR DATA. If you think your hard drive may be failing, save what is important to you.  If this continues to happen, I would get a new hard drive.

---

### Post by xmastree on 2006-08-10
> **Paerez said:**
> I would boot your puppy cd and run fsck on your main partition.I did that, that's what I meant when I said "I booted from a Puppy CD and fdisked it back to life again"
It found a lot of errors, and I just let it fix them all.

It now comes up clean, but some files have been changed or lost in the process. Ubuntu boots and runs ok, apart from the firefox thing and the login screen. There may be other problems, but I haven't noticed yet.

---

### Post by Paerez on 2006-08-10
fdisk is a partitioning tool, fsck is a file system checking tool. Which do you mean? I thought you meant you used fdisk to fix the mbr. I am suggesting checking the file system.

I would remove and then install firefox.

---

### Post by xmastree on 2006-08-11
> **Paerez said:**
> fdisk is a partitioning tool, fsck is a file system checking tool.
D'OH... My mistake. Of course I mean fsck.

I used fsck from puppy to repair the disk, but presumably some areas were damaged during the process.

Sorry for the confusion.

---

### Post by Paerez on 2006-08-11
OK cool. Did you try removing firefox then reinstalling it?

---

### Post by xmastree on 2006-08-11
> **Paerez said:**
> OK cool. Did you try removing firefox then reinstalling it?

Yes, I tried a complete removal, including config files. Although when I reinstalled it the MRU list was intact, as were my cookies. :confused: 

I suspect it's a hidden directory thing in my home directory.

---

### Post by Paerez on 2006-08-11
yeah the cookies and stuff is in your home under .mozilla. If you remove that folder all your settings will be gone.

---

### Post by xmastree on 2006-08-11
Yep. that fixed it. Thanks.

Now, about that login screen...

---

### Post by Paerez on 2006-08-11
that is the package GDM, try reinstalling that.

---

