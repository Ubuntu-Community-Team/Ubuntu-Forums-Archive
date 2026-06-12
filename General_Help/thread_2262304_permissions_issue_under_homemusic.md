---
title: "permissions issue under /home/music"
date: 2015-01-24
forum: General Help
---

### Post by nechen on 2015-01-24
Greetings!

I'm new to the 'Buntu scene and recently turned my old Intel Core2Quad (4GB RAM) into a nice little server/HTPC (Gotta love STEAM in-home streaming)

Anyway I've figured out all the problems I had as a first time user but something is still nagging at me.

I CANNOT for the LIFE of me open ANY of the music I backed up to my 1TB RAID1 array. I can open anything else from docs to videos and so on, but in order to play anything in MUSIC I have to do $ sudo thunar.

It strikes me as that I need su rights to play my own music? I've tried other file managers like Nautilus (I'm using Xubuntu atm) but the same problem still persists. This wouldn't be such an issue if it weren't for the fact I can't listen to my music remotely unless I'm on the server. I double checked the permissions and everything else I can think of but needing su rights to view .mp3's seems rather strange since I did everything else right.

Any help I could get on this would be greatly appreciated. I'm hoping it's something as silly as "are you sure you plugged it in?"

Thanks!
_nechen

---

### Post by TheFu on 2015-01-24
What userid is being used?
What are the permissions - exactly.

**ls -al** please.

Sound output is limited to userids on the console. At login, additional groups/gids are added to the console userid. You can manually add these groups for any userid you like.  A basic understanding of file/directory permissions is all that is needed.  Check the group ownership for the audio devices.

If you are running any GUI as root, there is something wrong.  Doing so can leave behind settings with the incorrect permissions and ownership, among other issues.

If you want to remotely listen to music, there are many ways to stream it or just allow a remote mount to other devices. What is the client device where you want to hear it? Perhaps we can recommend streaming servers?

---

### Post by Lars Noodén on 2015-01-24
Are you looking in the right directory?  What about in /home/nechen/Music instead?  Unless you manually created /home/music, it does not exist.  However, /home/nechen/Music or something like that based on your user name will exist having been created automatically.  And it is there that most programs will store and look for your music files.

---

### Post by nechen on 2015-01-24
Oh sorry still getting used to the file system.

yeah I mean /home/ghost/music

When I right click on an MP3 and go to properties --> Permissions It says "Access: NONE" for ghost but "root" has read and write ... what the heck did I do wrong?

here's my ls -al

and I was mistaken, the backups are on my 1TB mount point in /media/ghost


```
ghost@ghostnix:/media/ghost/c31e4e15-19b6-4bc9-a533-70278973061d$ ls -al
total 32
drwxr-xr-x   5 root  root        4096 Dec 24 05:33 .
drwxr-x---+  5 root  root        4096 Jan 24 03:39 ..
drwxrwxrwx  16 ghost sambashare  4096 Jan 21 19:27 1tb_storage
drwx------   2 root  root       16384 Oct 26  2012 lost+found
drwx------   4 root  root        4096 Dec 24 05:33 .Trash-0
```

---

### Post by Morbius1 on 2015-01-24
> drwxr-x---+  5 root  root        4096 Jan 24 03:39 ..
See that little "+" at the end? That signifies an extended attribute in this case an Access Control List. This folder is automatically created by the system and imposes that ACL.
Run this command to find the "real" permissions:
```
getfacl /media/ghost
```
You should see that aside from root the only user getting past the /media/ghost folder is "ghost" regardless of the permissions of anything past it. This is by design.

---

### Post by TheFu on 2015-01-24
How in the world did you get those permissions? That's some crazy **** there.  Too much abuse of root/sudo methinks.

Is this a Linux file system?

The root problem could be caused by mount options or by not understanding user/group and file/directory permissions.
Or the machine could have been hacked. Those permissions are the type I use on Capture The Flag competitions to weed out Unix/Linux noobs.

---

### Post by nechen on 2015-01-24
LOL I swear I'm not that dumb! And I never use "su" I only ever use sudo when doing apt-get install/update/remove/etc... OH and the 1TB RAID is Ext4 it's not NTFS or anything else bizarre. They were two totally fresh 1TBs that I mirrored and formatted. The weird thing is the the ONLY folder with this problem. I really wish I knew what the hell I did...

I actually did do that once by mistake and kept wondering why every I had installed was under "root" instead of /home/ghost but thats another funny story for another time. 

Thanks for the help Morbius, I'll add an addendum here in a sec when I can get to the server

---

### Post by nechen on 2015-01-24
Morbius, is this what you needed?

> 
getfacl: Removing leading '/' from absolute path names# file: media/ghost
# owner: root
# group: root
user::rwx
user:ghost:r-x
group::---
mask::r-x
other::---



**EDIT**

Sorry I forgot to mention, checking [PERMISSIONS] on the /media/ghost/[mounteddevice]/Music folder has Ghost under permissions and everything looks good. It's only until I right-click properties INSIDE an MP3 in the /music folder that I see this...

> 
Owner: root (root)
Access: R&W

Group: ghost
Acces: NONE

Others: NONE

And everything is grayed out.

What in the happy hell?

---

### Post by The Cog on 2015-01-24
I don't think we have seen the permissions of the folder where these music files are yet, or the permissions of the files in there. 
Can we see the output of these two commands, please (assuming your music files are in /home/ghost/music):
```
ls -ld /home/ghost/music
ls -l /home/ghost/music
```

---

### Post by TheFu on 2015-01-24
Exactly @Cog.  Personally, I'd just clear all the ACL stuff and setup the owner/group to be 
nechen.nechen (or whatever the userid is on the box).

ACLs have a place, but there isn't any need on a single-user system or most of the time in corporate environments.  Sure, 1 in 10,000 times there's a need for ACLs, but this isn't it.  IMHO.

---

### Post by nechen on 2015-01-24
They're actually on my 1TB under /media/ghost but there you go. I'm only including a snippet of ls-l beause of how many files I have

ls -ld

> ls -lddrwxrwxrwx 4 ghost ghost 12288 Jul  8  2014 .




ls -l

> 
ls -l
total 977740
-rw------- 1 root ghost 13727801 Jul  3  2009 03 Boom! Shake the Room [Ultramix].wma
-rw------- 1 root ghost  7247647 Jan 13  2010 03_-_Dragula.mp3
-rw------- 1 root ghost  8671361 Jan  9  2010 04 Discipline.mp3
-rw------- 1 root ghost  6561358 Jan  9  2010 04_-_Living_Dead_Girl.mp3
-rw------- 1 root ghost 11700815 Jul  3  2009 04 Slam [Ultimix].wma
-rw------- 1 root ghost  9376285 Jul  3  2009 05 Informer [Ultimix].wma
-rw------- 1 root ghost 11474243 Jul  3  2009 07 Come Baby Come [Ultimix].wma
-rw------- 1 root ghost 10270305 Jul  3  2009 08 Whoomp! (There It Is) [WPGC Remix].wma
-rw------- 1 root ghost 16790913 Jan 13  2010 10 What Is Love- [12' Mix].wma


---

### Post by nechen on 2015-01-24
How do I kill off the ACL? This is the first I've even heard of the bloody thing...

---

### Post by The Cog on 2015-01-24
I don't think you should be worrying about the ACL on /media/ghost. I think that's normal. Something to do with the way removable media gets mounted. My own media folder also has an ACL:```
steve@StevesPC:~$ cd /media/steve/
steve@StevesPC:/media/steve$ ls -al
total 4
drwxr-x---+ 2 root root 1 Jan  3 13:18 .
drwxr-xr-x  3 root root 8 Oct 29 20:12 ..
steve@StevesPC:/media/steve$ getfacl /media/steve
getfacl: Removing leading '/' from absolute path names
# file: media/steve
# owner: root
# group: root
user::rwx
user:steve:r-x
group::---
mask::r-x
other::---

steve@StevesPC:/media/steve$ 

```
I think the ACL keeps everyone except the console user (even root) out of the removable media.

---

### Post by TheFu on 2015-01-24
Probably correct.  I don't allow automatic mounting of unknown media.  For known stuff, I use automount with known settings.

So the next thing is to set the owner/group recursively to be whatever you require based on the userids accessing the media.  If both a login userid and a media server need access, then it is best to put both userids into the same group and make certain that the group can at least read the directories and files.  Or, you can just allow "other" to have read and then none of this stuff matters for a media server.  Sorry - I don't recall the initial issue anymore. Been trying to help a number of other folks with permissions issues the last few days.

---

### Post by nechen on 2015-01-24
Not a problem! Thanks again everyone for the prompt response and help!

I'll tinker around (I need the learning experience anyway) and I'll post an update if I get it to [FIXED]

Thanks!
_nechen

---

### Post by nechen on 2015-01-24
Well gents I gave up and just did a sudo thunar, highlighted EVERY bloody file under /media/ghost/mounteddevice/music and went to PERMISSIONS and just got rid of root, set it to ghost, and gave it R/W rights.

Now everything is working fine and I can access it remotely thru SAMBA.

Still have no idea how I fudged this up the first time around though.

How do I mark this as [SOLVED] so it doesn't stay alive? This is my first time on the forums...

---

### Post by The Cog on 2015-01-24
Glad it's sorted. I don't know how they got owned by root in the first place. Oh well.

At the top of this page, on the right is a pull-down menu Thread Tools which has an option to mark the thread solved.

---

### Post by TheFu on 2015-01-24
Be very careful running GUI programs using sudo, including thunar. GUI programs are more likely to leave behind files (including settings) in your $HOME that aren't owned by your userid.

Time for this? [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

