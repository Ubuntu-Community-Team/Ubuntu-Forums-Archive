---
title: "Desktop shortcuts getting corrupted in Ubuntu 14.04 LTS (with Windows 7 dual boot)"
date: 2015-05-04
forum: General Help
---

### Post by Paneesh on 2015-05-04
If I create a desktop shortcut in Ubuntu, for my folder(s) off my local drive, and when I login the next time, <b>the shortcut link will be EXPIRED!</b> If I try clicking that link, I get a message that the source file doesn't exist anymore even though it does.
I'm running Windows 7 and Ubuntu on dual boot.


HOW TO CAUSE THIS ERROR (on my computer, step-by-step):
Step 1: Log in to Ubuntu,
Step 2: Go to a folder on a local disk, and create a shortcut of that and send that shortcut to Desktop,
[ATTACH=CONFIG]261766[/ATTACH]
Step 3: Restart the computer...


Step 4: Select Windows and log in to it,
Step 5: Go to my source folder form which a shortcut was created,
Close the window (just to close the window and nothing else)
Step 6: Restart the computer...


Step 7: Select Ubuntu from the boot menu,
Step 8: Log in,
Step 9: Shortcut has now been corrupted,
[ATTACH=CONFIG]261767[/ATTACH]




When I try to click the corrupted file, I get a message as:
[ATTACH=CONFIG]261768[/ATTACH]
I'm running Ubuntu alongside with Windows 7.
Have I committed any mistakes while installing?
Or I'm ready to install both of these OS's from the start if that could help solve my issue.




  [1]: [http://i.stack.imgur.com/9K0Ag.png](http://i.stack.imgur.com/9K0Ag.png)
  [2]: [http://i.stack.imgur.com/DGsnD.png](http://i.stack.imgur.com/DGsnD.png)
  [3]: [http://i.stack.imgur.com/rEjEJ.png](http://i.stack.imgur.com/rEjEJ.png)

---

### Post by ajgreeny on 2015-05-04
Are the files that shortcut is linking to actually sitting on your Windows partition and not in your Ubuntu /home folder?

If this is the case it is probably because the windows partition is not automounted at boot, and therefore the files are not available to Ubuntu.

This is easily remedied with an edit of the /etc/fstab file, but to do so we need to know where the files are, and all the partitions in existence.

Show us the output of **sudo blkid -c /dev/null** in terminal and we can tell you what line or lines to add to the fstab file to solve this.

---

### Post by Paneesh on 2015-05-05
Thanks for your reply. 

The source file of that now-broken shortcut is on my Windows partition and not on my Ubuntu /home folder.

And could you please tell me how to fix this by examining the file that I have attached, if that helps? :(
Have I caused any error while installing or while partitioning Ubuntu?
Is it possible to solve this issue?
I've not been able to create any shortcut file though.


And here is the output:
[ATTACH]261786[/ATTACH]

---

### Post by Mark Phelps on 2015-05-05
How are you exiting Windows to reboot into Ubuntu? If you're choosing Restart, that could be problematic; instead, you should choose Shut Down and do a cold boot into Ubuntu.

Also, you didn't say, but if the folders you are linking to are on the Win7 OS partition, and you intend to Write to them -- that is asking for trouble as NTFS doesn't behave well when tampered with from outside -- not juts from Linux distros, but from other Windows OS versions, as well.

If you need to write to files/folders on NTFS partition, it is safer to create a shared DATA partition.  That is less likely to encounter filesystem corruption, and even if it does, that will not prevent Win7 from rebooting -- from where you can then do partition repairs.

---

### Post by ajgreeny on 2015-05-05
We also need the output of that **sudo blkid -c /dev/null** command in order to tell what is the problem here, and on which partition your pictures are sitting.

---

### Post by Paneesh on 2015-05-06
I'm restarting to switch to Windows after my work on Ubuntu, yes.
If that's problematic, I'll shut down and then switch to another OS from the next time.

The folders that I'm linking to, is on Windows 7 partition.
And could you please tell me how to create a shared data partition?
That'd really help me A LOT.

---

### Post by Paneesh on 2015-05-06
My music files are on "XY" drive.
And here's file.
[ATTACH]261799[/ATTACH]

---

### Post by ajgreeny on 2015-05-06
Sorry, but "XY" drive is meaningless to me, so I still don't really know where your files are.

Which of the partitions shown in your blkid output is the "XY" drive?

---

### Post by Paneesh on 2015-05-09
[ATTACH]261842[/ATTACH]

My files are in "PHANEESH" drive. I tried following another thread where they instructed to mount a disk automatically on startup, with the help of "Disks" utility and as it was already ticked, I pressed "ok" and tried to cause the same error but it did not happen! I was surprised that it has been solved, but it rather showed a new issue: Now I couldn't add a program to the Ubuntu desktop, say "Terminal", I get this error whenever I try dragging a file to desktop: But this was not happening in the beginning when I had installed Ubuntu, and it's unknown for me that what action might've caused this.
[ATTACH=CONFIG]261843[/ATTACH]
I don't now what else to do to solve these issues.

---

