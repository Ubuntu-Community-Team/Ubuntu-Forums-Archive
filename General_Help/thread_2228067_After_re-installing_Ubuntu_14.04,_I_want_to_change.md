---
title: "After re-installing Ubuntu 14.04, I want to change my default /home directory"
date: 2014-06-05
forum: General Help
---

### Post by ians0mniac on 2014-06-05
Alright, so I've been using Ubuntu for a few years now, and it became my main OS after 12.04 came out. yesterday, I tried updating from 13.04>13.10>14.04, and faced a serious problem: my graphics card and monitor were no longer recognized. I tried every fix I found online in an attempt to remedy this problem, but none of them worked. This morning, I decided to boot up another computer(my mom's), burn the 14.04x64 ISO onto a DVD, boot that up in my PC, and select "Reinstall Ubuntu 14.04". I re-installed it using a different username than my previous account(I used "ians0mniac" instead of "l1f3h4ck") and now have two folders in my /home directory: ians0mniac and l1f3h4ck. My old account, l1f3h4ck is no longer present as an option at the login screen(the only two options are "ians0mniac" and "Guest Session"), but I still possess its /home directory. My question is, how do I make /home/l1f3h4ck my default directory, instead of /home/ians0mniac? I'd try creating a new user named "l1f3h4ck", but I'm scared it'll overwrite my existing directory named "l1f3h4ck" with a new, empty one and I'll lose all my files. I will see about backing up my old /home/l1f3h4ck directory, just in case something bad happens but, assuming I can't, how would I go about fixing this and changing my default /home directory? Thanks.[ATTACH=CONFIG]253752[/ATTACH]

---

### Post by ians0mniac on 2014-06-05
Also, I apologize if I posted this in the wrong sub-forum. I was in a bit of a rush to post this.

---

### Post by ians0mniac on 2014-06-05
I am unable to back-up my /home/l1f3h4ck folder to my secondary HDD, as it is a 500GB drive and my /home/l1f3h4ck folder is larger than that.

EDIT: After deleting almost everything in my SteamApps folder, I have consolidated the size of /home/l1f3h4ck to just under 160GB, and will copy it onto my secondary HDD once I get home from running a few errands.

---

### Post by pauljwells on 2014-06-05
Then you're good. If you have backed up all your visible files and folders then that's great. If you want to keep your configuration tweaks (which launchers in the unity bar, playlists etc.) then you need to turn on the hidden files in Nautilus and copy all the'dot' files to your backup too. Then you can use your new 'iansomniac' account to create a new 'l1f3h4ck3r' account. Login, copy everything back from the backup. At worst you may need to change permissions on the copied files. If you do, post back and we can fix that.
Incidentally, the geek mantra is that unless you have two backups (one offline, disconnected) then your data is already lost...

---

### Post by ians0mniac on 2014-06-05
So you're saying that, once I create a new account named "l1f3h4ck" and copy all of my old /home/l1f3h4ck files to it, all the custom settings, programs, etc. contained therein will be applied and installed to this new installation?

---

### Post by oldfred on 2014-06-05
If moving /home to another partition:
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by ians0mniac on 2014-06-05
Thanks; will check this out.

---

### Post by ians0mniac on 2014-06-05
As useful as this guide is, I don't think I'll be needing it. I had stumbled across it earlier when I was searching for an answer and it didn't really help me, as I am not trying to move my /home/l1f3h4ck folder between partitions rather, I am attempting to re-instate it as my default /home folder and get all of my custom settings and programs contained therein up and running again.

---

