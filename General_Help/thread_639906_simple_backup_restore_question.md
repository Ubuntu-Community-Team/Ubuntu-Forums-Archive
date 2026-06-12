---
title: "simple backup restore question"
date: 2007-12-13
forum: General Help
---

### Post by lakelovers on 2007-12-13
I've searched sbackup threads and have not found a solution. Here's my problem: I have my files backed up on a second, internal HD. I replaced my primary drive after the old one dropped dead. I can access the files on the second disk, but when I open any one of them they seem to be empty. However, I can see the contents on Nautilus and have verified that those files have content, and I've changed permissions in Nautilus so I can access them. I set the destination in SBackup that I see on Nautilus, and when I go to the restore screen they show up but with no content. What's going on and how do I solve the problem.

Jerry

---

### Post by Pumalite on 2007-12-13
[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

---

### Post by lakelovers on 2007-12-13
Thanks for your response but it doesn't solve my problem. I've read though those instruction several times. My problem is when I set up the path to my second, internal drive where my backups are stored, I get the backup files list but when I select any directory/file to restore it is empty. However, when I bring up the files in Nautilus the have content. So, I can only surmise that the path is wrong even though I'm inputting the same path as shown in Nautilus. I've tried every variation of the path I can think of and nothing works. It's very frustrating, but I'll keep plugging away at that path.

---

### Post by Rocket2DMn on 2007-12-13
Perhaps you could show us an image from nautilus and some terminal output?

---

### Post by lakelovers on 2007-12-14
Okay. . . now I feel like an idiot. Yesterday, somehow I got the backup hard drive mounted on the desktop and from there I was able with Nautilus to examine the drive, see the backup files and change permissions. This morning, I can't find the drive to access it. I see it when I do a fdisk -l, but it doesn't show up under "media." So, now I'm barking up a blind alley. I'll appreciate show-the-dummy some guidance. 

Jerry

---

### Post by Rocket2DMn on 2007-12-14
It sounds like the drive is plugged in but not mounted.  Here are two guides and explanations:
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) (don't use scripts)
You can either add the drive under /etc/fstab or mount it manually using the mount command.

---

### Post by lakelovers on 2007-12-14
Here are the files in Nautilus. When I open a file. I get this. When I go to SBackup Restore, I get the list of backups but when I load any of them I get no content.  I don't know how to show these in this thread, but here's a stab. I took screen shots of two and copied one directly to this thread.
Do these indicate what's wrong? And are there other views I can add to this thread that will help?

[HTML] /home/jerry/Desktop/Screenshot-2007-11-26_10.16.56.737964.jerry-desktop.ful - File Browser.png   [/HTML]

[HTML]  /home/jerry/Desktop/Screenshot-2007-11-27_17.17.23.545880.jerry-desktop.inc Properties.png[/HTML]

[HTML]  /mnt/lost+found[/HTML]

Well, I don't know how to get these screen to show. And I don't know how to delete this reply so I can try again.

---

### Post by Rocket2DMn on 2007-12-14
To post images you need to hit the quick reply then go to the button at the bottom that says Go Advanced.  From there you can add attachments.

---

### Post by lakelovers on 2007-12-14
Here's a copy of the file of backups in Nautilus. I'll post more if this works

[IMG]  /home/jerry/Desktop/Screenshot-1.png[/IMG]

Well, that didn't work. I'm understanding how to make these responses. If you have the patience walk me through posting attachments. Also, how is a post deleted?

---

### Post by Rocket2DMn on 2007-12-14
LOL, ok, here we go.  Click the quick response button at the bottom right of a post, then click Go Advanced button below where you type your response.  At the bottom of the new page, scroll down and click Manage Attachments - a popup window will appear.  Here you can Upload File from your Computer.  Browse to the file you want to upload, then click Upload after you have selected the file.  Depending on the file size, it may take a few moments to upload.  After you have uploaded, scroll to the bottom of the popup window and click Close this window.  You will now see the files at the bottom of the response page under Additional Options.
Finish typing your reply and click Submit Reply.

---

### Post by lakelovers on 2007-12-14
I must be blind as well as out-to-lunch. I followed your instruction, up loaded a file, but I don't see any files at the bottom of "additional options." I looked at the preview. Still no file. I can't imagine why I can't get this right.

---

### Post by Rocket2DMn on 2007-12-14
All I can think of is that your filenames aren't compatible to upload.  Try shortening them to something like simplename.png
Otherwise you may need to uploda them to a 3rd party image site and link us there.

---

### Post by lakelovers on 2007-12-15
Finally! Success. Here are screen shots of /media/sb1/lost+found/ and one backup file expanded. I use the same path on SBackup restore. All the backup files show in the restore screen but when I open any of the files, nothing shows. I suppose this could be a permissions situation. You can see the permissions in screenshot-3. What do you suggest?

---

### Post by Rocket2DMn on 2007-12-15
When you say you open them and they appear to be empty, where are you looking?  In sbackup restore you should be able to select the directory then see the different backups.  When you select one you should see the folders.
Can you post a screenshot of the part where you can't see anything inside?
Also, I don't know what the group "admin" is, but I think the backups should be owned by root:root, not root:admin

---

### Post by lakelovers on 2007-12-15
Here's a couple of shots. of the permissions on one file which I set for root access and the other of the screen on SBackup restore in which the list of backup files appear. I have the file up for which I changed permission to "root." as you see there are no directories or sub files listed.

By the way, I really appreciate you hanging in with me and enduring my foibles.

I imagine the problem, will turn out to be a simple fix -- at least I hope so.

Jerry

I just remembered that after I downloaded SBackup, and then opened the restore window, a screen appeared saying that the files had an old "file type" or something of that nature, and asked weather I wanted to update the files. I clicked, "yes" and the screen seemed to hang, so I eventually closed it. I'm wondering if I just didn't wait long enough for that action to take place. I'm thinking I may reinstall SBackup to see if the updating screen reappears on the restore screen. I guess it's worth a try.

Just reinstalled sbackup and the file update window did not appear, and the restore filed did not appear. Think it would make any difference if I uninstalled sbackup and then installed it again?
I may try that. . . It didn't work. I did a complete uninstall, then reinstalled sbackup. Same thing: no file content shows.

---

### Post by Rocket2DMn on 2007-12-15
> **lakelovers said:**
> I just remembered that after I downloaded SBackup, and then opened the restore window, a screen appeared saying that the files had an old "file type" or something of that nature, and asked weather I wanted to update the files. I clicked, "yes" and the screen seemed to hang, so I eventually closed it. I'm wondering if I just didn't wait long enough for that action to take place. I'm thinking I may reinstall SBackup to see if the updating screen reappears on the restore screen. I guess it's worth a try.

Now that's a useful piece of information :)
You can try the reinstall, or if you know what version you had before, you can download and install that.  I'm willing to bet you didn't wait long enough, esp. since backups can be huge files + they are compressed.  
If all else fails (like the archives are partially corrupted), you might be forced to manually restore files by opening the archives in nautilus.
Go ahead and try to reinstall and let me know what happens.  I'll check back tomorrow.

---

### Post by lakelovers on 2007-12-15
I uninstalled than reinstalled sbackup and it didn't change. Still no access.

---

### Post by Rocket2DMn on 2007-12-16
I would have to suggest now that you try and find the version you had before.  If you know approximately when you installed sbackup when you started making backups, you can look at their changelog and figur out what version was the most recent at that time.  You can then download that version and attempt to restore with it.

---

### Post by lakelovers on 2007-12-16
Thanks, I'll give it a try.

I tried each of three version back and none worked. So, I went back to the latest version (10.04). When I did a "restore," the window came up saying there seemed to be old file types and did I want to update them (same as I mentioned earlier). I clicked "yes." Then I clicked on one of the restore files and nothing. I'm back where I started. I guess that means I'm just out of luck. I seems that since I can see the file contents of Nautilus, there should be a way to capture the files from Nautilus. If you have any more suggestion let me know.

Thanks, again.
Jerry

---

### Post by Rocket2DMn on 2007-12-16
What would happen if you declined to update the files?
Also, although this may sound stupid, you do have write permissions to the second disk that holds the backups, yes?
Again, if you really can't get it to work through the program, you can open the archives yourself in Nautilus and extract what you need.  It will certainly take awhile, but if you have data you need, then that's how you could recover it.  If this becomes the case, you may just want to go straight for the specifics you need like backed up music, videos, photos, and not bother trying to restore backed up configurations and programs since these can be redone.
SInce you couldn't get any help from the guys at sbackup, that's really all I can offer for suggestions.  The most important thing is that you get back the data you need, not that you get the program to work.  If you do a manual recovery, remember to start with the most recent FULL backup and work your way towards the present with INCREMENTAL backups.  Any backups from before your newest full backup are pretty much useless unless the newest archive is corrupted.

---

### Post by lakelovers on 2007-12-16
That's what I'll try, if I can muddle my way through the process. Except for a few photos, I don't think there's anything that's of crushing importance. . . though I hate to lose the phots.

---

### Post by Rocket2DMn on 2007-12-16
They're in there somewhere, don't let them go.  The directory structure is preserved, so you just navigate to where you normally store them.

---

