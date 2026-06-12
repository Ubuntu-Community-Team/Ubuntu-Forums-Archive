---
title: "New to Ubuntu (7.10) backing up; updates; software; partition methods."
date: 2007-12-29
forum: General Help
---

### Post by CJCorcoran on 2007-12-29
Hello:

I am installing Ubuntu 7.10.  I have some questions about the partitioning schemes as well as backing up.  When using XP, I use Acronis True Image Backup to make backups right after initial instalatlion, after installing updates, and then finally after installing programs and tweaking.  Then I'll make backups every so often as new software is installed, etc.  Acronis is useful because if the OS is being buggy, I can do a restore from the Acronis bootdisk.  Is there a similar way of employing this backup/restore method in Ubuntu?  So far the backup programs only back up while using Ubuntu.  I'm looking to make images of the HD's.  As for partitioning, I am using a 160 GB SATA drive partioned the following way: 15 GB dedicated to root, 2 GB for swap, and the last partition is mounted just for /home.  Is this a good set up or should I change it?  I was planning on storing all my files -- including backups -- in /home that aren't OS related.  Also, what are some good Ubuntu books, or should I just stick with the forums and internet?

Finally, what are the equivalents of ctl+alt+del?  I believe from viewing the forms there's alt+shft+f1.  Any other useful commands I should know as I've already experienced a freeze during the first set of updates.

Many thanks ahead of time.
--Chris

---

### Post by kyphi on 2007-12-29
Here are some answers to your many questions:

For backing up I use a 60 GB USB external hard drive - after all, there is no point in backing up anything to the main hard drive.  If your main hard drive fails then all information on that drive is lost.

You really only need to duplicate your home directory where all your personal files are.  The Ubuntu installation is on your installation disc and any programmes that you have installed are available again from their original repositories.

Acronis True Image works fine in Windows, however, there is no need to back up your entire operating system.  Read this article about backups using Mondo/Mindi:  [http://www.linuxjournal.com/article/5449](http://www.linuxjournal.com/article/5449)

Your partitions look fine as you have made them.

As to books, there are many.  One that I would recommend is published by O'Reilly, Ubuntu Hacks.  Also, I would recommend that you learn to use the command line.  An excellent tutorial is found here: [http://linuxcommand.org/](http://linuxcommand.org/)

Place these links into your bookmarks in Firefox for future reference.

To restart X (the X Windows System), which is your user interface use Ctrl+Alt+Backspace.

Enjoy Linux, enjoy Ubuntu.

---

