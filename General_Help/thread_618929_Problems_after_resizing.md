---
title: "Problems after resizing"
date: 2007-11-20
forum: General Help
---

### Post by Onay on 2007-11-20
In a nutcase, here's what happened...

I had 2 ubuntu installations on my disk simultaneously since I was shifting from Fiesty Fawn to Gutsy Gibbon. I am now fully satisfied with my 7.10 install, so I went into the ubuntu install CD to delete the partition containing my 7.04 install. It deleted, but when adding space to the existing Gutsy installation, the whole filesystem had to move.

Now when I boot up into my Gutsy installation, I run into 2 problems...
[LIST=1]
[*]fsck.ext3: Unable to Resolve error message is shown during start up and puts me into a terminal interface with no GUI. When I try to restart using Ctrl+Alt+Del, it starts loading up the kernel modules and ubuntu boots fine. The message also says "File System check failed" and that a certain root UUID was faulty. What could I do to fix this?

[*]The Keyring Manager now comes up and asks me each time I boot what the password is so that it can log into my wireless network, but Gutsy never made me do this before. How can I make it automatic again?
[/LIST]

---

### Post by Onay on 2007-11-20
Okay I resolved the second problem, I just had to change my main password to the same as the default keyring password, but the second one still doesn't make any sense, seeing that I can still boot up the computer fine (although it's quite annoying)

---

### Post by Herman on 2007-11-23
Okay, here's how to fix your first problem,
> fsck.ext3: Unable to Resolve error message is shown during start up and puts me into a terminal interface with no GUI. When I try to restart using Ctrl+Alt+Del, it starts loading up the kernel modules and ubuntu boots fine. The message also says "File System check failed" and that a certain root UUID was faulty. What could I do to fix this?When you installed Gutsy Gibbon the installer automatically detected all the partitions in your disk and added them to the /etc/ftab file that was automatically made during installation.

Now that you have deleted your old Feisty partition, your operating system looks for it at file system check time during boot-up and doesn't find it, so drops you into a shell, complaining of the missing file system, (partition).
To stop that from happening any more, you just need to edit your /etc/fstab file in Gutsy Gibbon. You can 'comment out' the lines referring to the old partition or delete them completely.
'Commenting them out' would be safer in case you make a mistake and delete the wrong lines.
To 'comment out' a line, you just place a '#' mark at teh beginning of the line.

Here is a link that might be of some help to you, [                                Mount a different Linux filesystem (ext3) in Ubuntu]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu") (do the opposite of what this link says, since you want to quit mounting a file system which no longer exists).

If you need more help, I can explain in more detail if needed. Maybe posting a copy of your /etc/fstab file here will help.

Regards, Herman :)

---

