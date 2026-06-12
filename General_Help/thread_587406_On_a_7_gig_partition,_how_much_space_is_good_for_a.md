---
title: "On a 7 gig partition, how much space is good for a separate home partition?"
date: 2007-10-22
forum: General Help
---

### Post by Starrfoxx on 2007-10-22
This question might sound a little confusing, so I'll help explain it a little.

I'm putting together a computer for my mother for Christmas.  I've already installed a dual boot of Windows 98SE and XP Pro sp2 on it.  Both OS are there for compatibility reasons.  I gave 98SE only 5 gigs.  The remainder of the drive is dedicated to XP Pro except for 7 gigs.

I saved the 7 gigs for Ubuntu.  I wanted to have 7.10 installed for her, so that she has a safe way to browse the internet, watch DVD's, and have something fun to play with.  I've read that it is a good idea to create a separate partition for the /home directory.  How much space would be good?  I doubt she'll do anything more with Linux other than surfing, email, and maybe Office.  I thought about just keeping everything on one partition, but I've read that it's best to have a separate /home partition to keep all of your preferences when upgrading to the next release.

Question #2

How can I change the Grub menu so that it shows the list of operating systems in the following order:  Windows XP, Windows 98, and then Ubuntu?

---

### Post by az on 2007-10-22
> **Starrfoxx said:**
> This question might sound a little confusing, so I'll help explain it a little.

I'm putting together a computer for my mother for Christmas.  I've already installed a dual boot of Windows 98SE and XP Pro sp2 on it.  Both OS are there for compatibility reasons.  I gave 98SE only 5 gigs.  The remainder of the drive is dedicated to XP Pro except for 7 gigs.

I saved the 7 gigs for Ubuntu.  I wanted to have 7.10 installed for her, so that she has a safe way to browse the internet, watch DVD's, and have something fun to play with.  I've read that it is a good idea to create a separate partition for the /home directory.  How much space would be good?  I doubt she'll do anything more with Linux other than surfing, email, and maybe Office.  I thought about just keeping everything on one partition, but I've read that it's best to have a separate /home partition to keep all of your preferences when upgrading to the next release.

Question #2

How can I change the Grub menu so that it shows the list of operating systems in the following order:  Windows XP, Windows 98, and then Ubuntu?

If you are thinking that you are short on space, a separate home is the last thing you want to do.  The best way to save on space is to use the default behaviour - have everything share the same partition.

With external drives being so cheap, there is no longer any good reason to keep a separate home partition.  Just do proper backups the old fasion way - it's a lot easier, simpler ans safer.

As for grub, edit the /boot/grub/menu.list file.  Anything in between the "automagic configuration" lines is ordered by the package manager.  Anything before or after that is your choice.  So edit the file and put the other two stanzas (for your other two OSes) before or after the automagic configuration lines.

---

