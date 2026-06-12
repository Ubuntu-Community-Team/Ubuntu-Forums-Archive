---
title: "Moving documents, music, video to new HDD (Not NTFS)"
date: 2008-05-05
forum: General Help
---

### Post by potatan on 2008-05-05
Hi,

I have a 250gb hdd that I used to use in Windows for My Documents (music, docs, videos etc.).  I have backed up all the data temporarily and reformatted the drive as EXT3.

How can I configure my system so that when I click on "Places - Documents" (or Places - Music, Pictures, Videos) it goes to this drive rather than to the default locations under my Home folder?

I've seen plenty of related questions about re-pointing to an existing NTFS drive, but as this disk has been reformatted to EXT3 and I will be copying all my data there, can I make it a bit more seamless than setting up symbolic links etc?

Many thanks in advance, as usual.

---

### Post by Patb on 2008-05-05
Potatan, perhaps you could use the bind facility in your /etc/fstab file.  My own example may help.  The following lines are exracts from my fstab.  The first line mounts the first partition of my second hard drive at /media/sdb1.  The second line makes the directory /Docs on that partition appear at a directory called /Docs/ in my home directory.  I had to create (an empty) ~/Docs before I set this up.  
```
/dev/sdb1 /media/sdb1     ext3    defaults        0       2
/media/sdb1/Docs   /home/pat/Docs  none  bind

```No symbolic links.  Is that what you are looking for?

Cheers, Pat.

---

### Post by az on 2008-05-05
> **potatan said:**
> 
I've seen plenty of related questions about re-pointing to an existing NTFS drive, but as this disk has been reformatted to EXT3 and I will be copying all my data there, can I make it a bit more seamless than setting up symbolic links etc?


Whether you are using ext3 or NTFS, it doesn't make a difference.

However, if you want to move your entire home drive there, then you would need for it to be ext3.  

I would not recommend you mount your entire home folder onto an external drive, though.

---

### Post by potatan on 2008-05-06
> **Patb said:**
> Potatan, perhaps you could use the bind facility in your /etc/fstab file.  My own example may help.  The following lines are exracts from my fstab.  The first line mounts the first partition of my second hard drive at /media/sdb1.  The second line makes the directory /Docs on that partition appear at a directory called /Docs/ in my home directory.  I had to create (an empty) ~/Docs before I set this up.  
```
/dev/sdb1 /media/sdb1     ext3    defaults        0       2
/media/sdb1/Docs   /home/pat/Docs  none  bind

```No symbolic links.  Is that what you are looking for?

Cheers, Pat.

Pat,
That sounds about right (and my spare drive is indeed /dev/sdb1)

Just to clarify, I already have the default Documents, Music, Pictures, Videos directories under my home directory - these appear under my Places menu on the panel.

So I can make four directories with the same names on my new drive and then add four lines to fstab
```
/media/sdb1/Documents   /home/paul/Documents  none  bind
/media/sdb1/Pictures   /home/paul/Pictures  none  bind
(ditto) /Videos
etc. 
```

Would that work?

I have two other problems at the moment also:

1. The disk is not automatically mounted at startup 
2. I can't create folders or files on the drive - presumably I need to change the permissions so all users can read from and write to this drive


To answer the other post, this is an internal 250gb disk, not external.

Thanks in advance
Paul

---

### Post by Patb on 2008-05-07
> **potatan said:**
> Would that work?
Yes, Paul, you seem to be right on track, subject to the point below.  If you haven't already done so, just make sure your present /home/paul/Documents etc are empty when that 250G disk is not mounted.  This is just to eliminate confusion as to just where all your documents are.  Then try changing your fstab and see.  

By the way, if you wish to mount (almost) everything as stipulated in your new fstab without bothering to reboot:
```
sudo mount -a
```
> 1. The disk is not automatically mounted at startup
Check the first line in my own example.  That mounts the drive.  I think you do not yet have an equivalent line.  Don't forget you might have to first create /media/sdb1.
> 2. I can't create folders or files on the drive
If it is a stand alone machine like mine, I would change the top folder permissions for /media/sdb1/ to rwxrwxrwx.  Probably not a "secure" idea though if that's any issue.  To check details for permissions, "man chmod" (which always puts me to sleep :)).
> presumably I need to change the permissions so all users can read from and write to this drive
With your setup, the directories on that drive will appear at /home/paul/whatever so they will not appear on other users' home folders.  Depending on the permissions, others would be able to access them if they look in /media/sdb1/whatever.  But I'm fairly sure you can use bind twice to have the directory appear at two equivalent locations eg for users paul and fred:
```
/media/sdb1/Documents   /home/paul/Documents  none  bind
/media/sdb1/Documents   /home/fred/Documents  none  bind
```

Hope this helps.  Cheers, Pat.

---

### Post by vanadium on 2008-05-07
> can I make it a bit more seamless than setting up symbolic links etc?

What makes you think that symbolic links are not "seamless"? It is not only the easiest, but also the only correct way to go.

* As root, create a directory Music on your new HDD (gksudo nautilus)
* As root, change the owner of that directory to you as user
* As root, right-click "Music", select "Create Link".
* As root, move that link to your own home directory. Quit nautilus now.
* In your home directory, rename "Link to Music" to "Music"

Now, you can access your music from within your home directory and you have all access rights.

---

### Post by Patb on 2008-05-07
> **vanadium said:**
> What makes you think that symbolic links are not "seamless"? It is not only the easiest, but also the only correct way to go...
Vanadium, just as a matter of interest, why are symlinks the "only correct" way to go?  What is 'less correct' about using the bind function in fstab?  

Cheers, Pat.

---

### Post by potatan on 2008-05-08
Interesting points - I'll hold off for a bit to see the outcome of this discussion.  I'm in the middle of revision at the moment anyway so am in no rush to get bogged down in self-support issues, at least until next week when my exams are over.

Vanadium, you said:
> In your home directory, rename "Link to Music" to "Music"

Will this have the effect (as originally posted) of making Places/Music go to the correct folder?  I.E. do the items in the Places menu always go to /home/Music etc. (and then through sym links to my "real" music folder on my bigger HDD)?

Another way of explaining it is to compare it to the Windows "My Documents" functionality.  If I decide to move My Documents and its contents to another drive, then whenever I click on My Documents (e.g. on the desktop, through the start menu, in file select dialogs), it will go directly to the new location.

Paul

---

### Post by vanadium on 2008-05-08
> 
Vanadium, just as a matter of interest, why are symlinks the "only correct" way to go? 


In principle, I exaggerated: Linux/unix is a very flexible system, and technically, you are perfectly free to do it your way. You can indeed mount storage wherever you want, and even multiple times. You can make the system as chaotic as you want and still technically have it perfectly OK. You could even mimic the Windows "Documents and Settings" approach ;)

It is more a matter of organization and convention. Traditionally, all mounting happened in /mnt. With Ubuntu, non-permanent storage is mounted in /media.

Once the storage is mounted, symlinks in Linux give you the flexibility to let the user access it in any possible way, e.g. as a "music folder" in their home directory.

In a single user system where you are the only admin, it will not matter really how you do it, as long as you find your way back in your system. In a multi-user system, it would be much more practical and neat to just mount the storage as root in some predefined places, then create links (for multiple users) to the same storage media, and typically to different directories on it, in any way that is needed. 

Feel free to do as you like. I am only trying to convince you about the ease and flexibility of the symbolic links, so that mounting can be done just once by the root, and then organizing the system can be done and changed (even by the user, do not need to be root) using symlinks whenever the need arises.

---

### Post by Patb on 2008-05-08
> **potatan said:**
> Interesting points - I'll hold off for a bit to see the outcome of this discussion.I don't think there will be any particular outcome, Paul, rather two alternative views.  Vanadium has pointed out the traditional view and one which may well make particular sense for a multi-user system.  I am a single user and I suspect you are.  The fstab bind approach works okay for me but I have no discord with Vanadium's comments.  In either case, you should make the four directories on your second hard drive as per your own post, and then either use Vanadium's symlinks approach or mine to get your documents to appear in the relevant directories under /home/paul/.

(Vanadium, please post if I have in any way misrepresented your viewpoint.)

Cheers and good luck, Pat.

---

### Post by vanadium on 2008-05-08
No problem, Pat. I agree with your summary: both approaches will work: it is the flexibility of unix/linux.

---

### Post by potatan on 2008-05-09
Thanks, both of you.

This is a multi user system (kinda) - I encourage my 18yo daughter and 16yo son to appreciate the security and usability of having separate logins, but it's by no means a military level concern!

I think I'll go with the symlinks solution.  I can create three separate home areas (with pictures, videos etc.) on the big disk and symlink them back to each user.  That way they all get to see just their own data directories, whilst I can still retain overall access.

Thanks again for an interesting and useful discussion which, incidentally, is very relevant to my avatar...


Paul

---

### Post by potatan on 2008-05-09
Okay,

That hasn't quite worked as planned.  I have renamed my existing /home/paul/Music to /home/paul/old Music, then created a new /Music folder on sdb1 (the 250gb disk).  I have then created a link as advised and moved this back to my default /home folder, renaming it to "Music".  I have done the same for /Pictures.

Screenshot attached.

But now, when I click the Places menu, it says, from the top:
Home folder
Desktop
Documents
**old Music**
**old Pictures**
Videos

(I can't provide a screenshot of this as it seems to be disabled while the Places menu is showing).

This is also showing in the quick access section at the bottom left of the Nautilus, in the screenshot.

Obiovusly what I'd like is for the places menu to go directly to where I have chosen to store my Music, Pictures etc.

Thanks
Paul

---

### Post by Gina on 2008-05-09
> **Patb said:**
> Potatan, perhaps you could use the bind facility in your /etc/fstab file.  My own example may help.  The following lines are exracts from my fstab.  The first line mounts the first partition of my second hard drive at /media/sdb1.  The second line makes the directory /Docs on that partition appear at a directory called /Docs/ in my home directory.  I had to create (an empty) ~/Docs before I set this up.  
```
/dev/sdb1 /media/sdb1     ext3    defaults        0       2
/media/sdb1/Docs   /home/pat/Docs  none  bind

```No symbolic links.  Is that what you are looking for?

Cheers, Pat.That's just what I've been looking for too - thank you :)

---

### Post by Gina on 2008-05-09
> **vanadium said:**
> What makes you think that symbolic links are not "seamless"? It is not only the easiest, but also the only correct way to go.

* As root, create a directory Music on your new HDD (gksudo nautilus)
* As root, change the owner of that directory to you as user
* As root, right-click "Music", select "Create Link".
* As root, move that link to your own home directory. Quit nautilus now.
* In your home directory, rename "Link to Music" to "Music"

Now, you can access your music from within your home directory and you have all access rights.Very useful - just what I'd like to do - thank you :)

---

### Post by vanadium on 2008-05-09
Hey, potatan, what you see now is an effect of gnome, which keeps pointing (consistently, if you ask me) to the directory you renamed. The easiest way to get that the way you want is probably to edit .config/user-dirs.dirs (I looked in vain for a gui way to change this). 
Just update the name of the Music dir you will find there.

This probably would not have happened if you had deleted the Music dir and created a Music symlink instead, but of that I am not sure.

---

### Post by Patb on 2008-05-09
> **potatan said:**
> But now, when I click the Places menu, it says, from the top:
Home folder
Desktop
Documents
**old Music**
**old Pictures**
Videos

Paul, I think you are right on track.  If you now go into "Old music" and move all that's in there to "Music", it should actually be on your second hard drive but accessible under your "Home folder".  Then you can delete the empty directory "Old music" and it will not appear under "Places".

Ditto for pictures of course.  

Cheers, Pat.

PS Edit: Sorry, I didn't notice Vanadium's last post.  I think this is right: if you want "Music" to appear under your Places menu, follow Vanadium's advice;  otherwise follow my advice which will mean that you can open your Home directory to find a subdirectory called "Music".  Sorry I can't test this for you because I don't use Gnome.  Cheers, Pat.

---

### Post by potatan on 2008-05-11
This was a tricky one!

I played around with user-dirs.dir and couldn't get the results I wanted, as well as getting some "odd" results - basically I couldn't get my Places menu to point to the new locations, via the sym links I had created earlier.

Then I came across a blog saying this:
> I’m sure it is a good idea to keep user-dirs.dirs in sync with the actual directories I use, but it turns out that what I had really been trying to do was figure out was how the Places menu worked. (Or at least one part of the Places menu.) For that, I discovered the ~/.gtk-bookmarks file

So I went ahead and edited ~/.gtk-bookmarks and found that it was pointing to my "old Pictures", "old Videos" etc.

I changed it to
```
file:///home/paul/Documents
file:///home/paul/Music
file:///home/paul/Pictures
file:///home/paul/Videos
```

and all is well!  

The places menu points to my new disk locations (via the symlinks), as do the quick links in the sidebar of the Nautilus window, and file-save dialogs etc.

I haven't tried this, but I imagine I could change them to "/media/sdb1/Music" etc. and they would work without the symlinks, but it's probably easier to leave the symlinks in as they make navigation easier from my default /home folder.

It looks like the default folder locations from Ubuntu 7.10 forwards are still "bedding in" a little due to a couple of projects - the article mentions for instance, that OpenOffice uses its own folder config, but for now, I'm happy with the way it is working.

Original article  here:
[http://www.movingtofreedom.org/2007/10/23/new-dirs-in-gutsy-documents-music-pictures-video/](http://www.movingtofreedom.org/2007/10/23/new-dirs-in-gutsy-documents-music-pictures-video/)

Thanks once again for all your help

Paul

---

### Post by vanadium on 2008-05-12
Thanks also to you for sharing the part of the solution you discovered yourself!

---

