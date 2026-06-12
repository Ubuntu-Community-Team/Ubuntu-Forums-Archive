---
title: "Purging config files from home folder"
date: 2008-03-16
forum: General Help
---

### Post by nvteighen on 2008-03-16
Hi there!
I'm concerning about the lots of dot-folders and dot-files in my home folder. Of course, most of them are being used by applications, but I see much of that config data is referred to applications I've deleted. This includes obsolete gconf entries, scattered folders inside .gnome, etc.

I've been removing some of these, but obviously I can't manage anything by hand. As I use a separate /home partition and always do a clean install, I fear this "Dot" Hell may grow into an unstable configuration in a near future. On the other hand, I always tell Synaptic/Apt-get to purge config files when removing packages, so my root partition is absolutely clean of uneeded data. 

So, is there any method that may help me? I know there will be no "magical" way that will wipe all uneeded files and leave the needed ones with no errors... I just want something that tells me what files should eventually be reviewed and then decide by myself what to do.

Thanks!

---

### Post by jimbren on 2008-03-16
Personally, I think you're pretty safe just browsing through your hidden files and folders inside /home and deleting what you know you don't need any longer.  Most of the time, these folders and files are very small, and don't make much of a difference when it comes to space management, though sometimes there are some large files.  

For my own purposes, I do regular backups, and make sure that I have a good back up before I get into any major housekeeping. From the fact that you have your own /home partition, and the fact that you say you always do a clean install, I'm just guessing that you also do backups.  If so, you're pretty safe to delete whatever.  

Hope this helps. 

jimbo

---

### Post by cmnorton on 2008-03-16
This is not a answer but a question of philosphy. Dot files are there so you cannot see them on a regular directory search (ls -l). Are they taking up that much room? Is it really necessary to remove them all? You could probably get to the bottom of each application's installed dot file directory, and then remove them. 

One thing you could do is remove everything to a save place /home/your-dir/do_save, and then bring back things one by one. Either determine what the directory is through examiniation or just let the application fail and bring its directory back.

As is true with most things I have encountered in Linux, you can be forgiven a lot with an approach like this, when you just move the stuff to a safe place, instead of obliterating it for all time.

---

### Post by nvteighen on 2008-03-16
Well, not only I do backups, but also when I say "removing", what I actually do is first renaming the folder to something else, see if nothing has crashed and only then remove it.

But maybe it would be interesting to write a little script to help in this task, given the fact that regularly these folders are named the same as the package installed. So, if there's a way to list all not-installed packages (apt-cache?), then the program should only compare whether there's a folder with a not-installed package's name and dump the results into a text file that I can afterwards review.

Thoughts?

---

