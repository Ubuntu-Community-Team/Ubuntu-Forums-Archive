---
title: "Has this happened to anybody else?"
date: 2006-11-18
forum: General Help
---

### Post by daz4126 on 2006-11-18
Hi everybody,

I have sorted out all of my issues with upgrading to Edgy and there is just one that is completely bugging me!!](*,) 

Nautilus doesn't show any previews for images, movies or sound files, even though I have selected this in the options. This makes finding a relevant image very difficult.

Would just like to know if this has affected anybody else or is it just me? If it has happened to you, have you fixed it or is it a known bug?
If it hasn't happened to you, do you have any ideas on fixing it?

cheers,

DAZ

---

### Post by ciscosurfer on 2006-11-18
Something I pulled in from the repos solved this problem for me.  After an Automatix install, I can always see my pictures and movies, etc.  I'm trying to recall which package(s) it was, but I can't atm.  I also remember once (before using Automatix and on a prior install), that I downloaded a KDE package, which pulled many other packages over as well.  Try installing Konqueror and see if that helps.

---

### Post by strabes on 2006-11-18
a cool feature in nautilus is if you install the packages mpg123 and vorbis-tools, you can preview music and sound files just by hovering your mouse cursor over them in nautilus. Icon mode has to be enabled though, so this isn't really useful for me since I use icon view mode.... just thought I'd point out this useful tip....

---

### Post by jimbob on 2006-11-18
I have found that you really need all the various codecs (w32codecs, etc...) to get all these previews, thumbnails to work.

The easiest way is to install Automatix and select all of the multimedia-related stuff for installation.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by ciscosurfer on 2006-11-18
> **jimbob said:**
> I have found that you really need all the various codecs (w32codecs, etc...) to get all these previews, thumbnails to work.

The easiest way is to install Automatix and select all of the multimedia-related stuff for installation.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR=Red][SIZE=2]*Registered Linux User #400396*[/SIZE][/COLOR]I second that. 8)

---

### Post by daz4126 on 2006-11-19
Thanks for the advice people, is there a version of Automatix for Edgy that I can use? I had it installed for Dapper but it won't work after updating to edgy.

DAZ

---

### Post by xfile087 on 2006-11-19
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")

---

### Post by daz4126 on 2006-11-19
Okay, I have installed all the multimedia stuff from Automatix and still no luck.

I guess that other people CAN see their thumbnails in nautilus, so it is just a problem with my setup?

I could see thumbanils in Dapper, but as soon as I updated in Edgy I couldn't see them.

I should add that I can see thumbnails on files on my external HD, just not anything on the root partition, so the problem does not seem to be with nautilus, maybe just a setting on the disk??

thanks again for the suggestions,

DAZ

---

### Post by seanUSXIII on 2006-11-19
I had this problem. Try renaming the folder and the rename it back if you would like. This got my thumbnails to come back. 8)

---

### Post by daz4126 on 2006-11-19
> **seanUSXIII said:**
> I had this problem. Try renaming the folder and the rename it back if you would like. This got my thumbnails to come back. 8)

Thanks for this help seanUSXIII, but it still doesn't work!

Any other suggestions....anybody!?!

DAZ

---

### Post by jimbob on 2006-11-19
If you have thumbnails that have failed in the past they will be in the ./.thumbnails/fail directory in your user account and as long as they are there they will never work again even if you have fixed your problem.

Go ahead and delete this entire directory (not to worry, the system will recreate it) and try your thumbs again.

   $sudo rm -rf .thumbnails

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by daz4126 on 2006-11-19
> **jimbob said:**
> If you have thumbnails that have failed in the past they will be in the ./.thumbnails/fail directory in your user account and as long as they are there they will never work again even if you have fixed your problem.

Go ahead and delete this entire directory (not to worry, the system will recreate it) and try your thumbs again.

   $sudo rm -rf .thumbnails

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

I have deleted this file but they are still not working.

I think that the problem is with some setting for my root partition - previews work on my external HD, but not on any files stored on the root partition. Has anybody any ideas which setting this might be???

I have set Nautilus to show previews, so that is not the problem.

thanks for the suggestion.

DAZ

---

### Post by jimbob on 2006-11-19
Take a look in the .thumbnails/fail/gnome-thumbnail-factory directory I talked about above and see if there are any *.png files there.  Count them (or delete them and start from scratch if you want).

Now go into Nautilus and select a directory that has a few .wmv video files.  Watch it closely for a minute or two.

Do you see the icons flicker or blink as they are examined by Nautilus in turn?  You can actually watch the process going on (at least on my system).

Now go back to .thumbnails/fail/gnome-thumbnail-factory and see if you have some new *.png entries.  That might tell us where to look next.

I don't want to read this whole thread again but have you tried creating a new user account to see if it works?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by daz4126 on 2006-11-20
Thanks for the continued suggestions jimbob.

I don't have anything in the .thumbnails/fail directory

I have tried creating a new account and this doesn't work either.

I am now convinced the problem lies with a setting somewhere on the root partition since all previews work fine on my external HD. Hopefully somebody out there knows what the preview facility has to do with the drive it is running on and can suggest something...

DAZ

---

### Post by krlsn on 2006-11-21
Hi DAZ,

I have the same problem. I had it working but then I started touching my partitions in order to get more room for Ubuntu. I moved the contents to a bigger partition with GParted and then changed a couple of things in fstab to get everything back working. No problem with that.

But... since then I've lost thumbnailing on Nautilus. If I choose to show thumbnails for any source (not only local disks) it shows them, but I don't know where does it store which are "local drives" and which not.

Any clue?

Thanks.

---

### Post by daz4126 on 2006-11-21
> **krlsn said:**
> Hi DAZ,

I have the same problem. I had it working but then I started touching my partitions in order to get more room for Ubuntu. I moved the contents to a bigger partition with GParted and then changed a couple of things in fstab to get everything back working. No problem with that.

But... since then I've lost thumbnailing on Nautilus. If I choose to show thumbnails for any source (not only local disks) it shows them, but I don't know where does it store which are "local drives" and which not.

Any clue?

Thanks.

Hi Krisn,

Well, I tried what you said and ... wow ... after all the suggestions on this forum, it worked! With the preview setting as 'all' rather than 'local files only' all the thumbnails appeared. We seem to have had the same problem, I wonder what causes it (I have no idea...)???

The best bit is that when I changed the setting back to 'local files only' the thumbnails were still there, have you tried this?

Fingers crossed they will still be there after a reboot, if they are then maybe I should edit this to be 'resolved'....finally!!!:D 

DAZ

---

### Post by Tobster on 2006-11-21
People are going to say 'Tobster your crazy'  But I always think it best to do a fresh install right form the start.  I mean get you hand on a disk, backup your files and do a complete install.

I would recommend doing this every so often with Windows with Ubuntu you might as well do it with every update (once a CD been released) because you will know that all the rubbish on your computer will be deleted including any unwonted  sensitive data and sometimes you might have software on your computer that may affect the up grade or how it works if you do not do a complete fresh install - if you just up grade viva the package manager

---

### Post by Henry Rayker on 2006-11-21
I do the same, Tobster. I always just make a reasonable partition, install the new version and migrate my files over...then just resize the new partition to cover the other old one.

---

### Post by daz4126 on 2006-11-22
Okay, maybe the problem isn't completely solved.

Thumbnail previews will only work if preview setting is 'all files' rather than 'local files only'. This is only on my root partition. I moved my home directory to a new partition and all the previews worked fine with the setting as 'local files only'.

So my question is, why does Ubuntu think that my root partition is not a local file? Is there a way of changing this? Practically, I don't think there will be too many issues with leaving the setting to 'all files' but I'd still like to know why this happened.

Thanks for spotting this krisn!!

DAZ

---

### Post by daz4126 on 2006-11-22
@Tobster and Henry Rayker:

I can see your point about a fresh install each time, but what about all the settings, themes and programs that have been installed since. Would you have to reinstall any programs the don't come as default?

One of my major problems is with Aptana, this was a real struggle to get working and I really don't want to go through that all over again.

DAZ

---

### Post by krlsn on 2006-11-26
The problem was that the / mount point was not correctly mounted. I discovered that by executing 'mount'. It was nout mounted!

The problem then is that after the repartitioning, the changed partitions changed their uuids in /dev/disk/by-uuid.
The solution is to make an 'ls -l /dev/disk/by-uuid', then you will see the UUID of the root parition.

Output:
d984db9a-6c57-455e-b155-8ed7859da1b9 -> ../../sdb6

Then, 'sudo gedit /etc/fstab' and change the old uuid of the / mount point to the new uuid.

Example fstab:
UUID=d984db9a-6c57-455e-b155-8ed7859da1b9 / ext3 defaults,errors=remount-ro 0 1

Then reboot and you will have / properly mounted!

Good luck!

---

### Post by daz4126 on 2006-11-26
> **krlsn said:**
> The problem was that the / mount point was not correctly mounted. I discovered that by executing 'mount'. It was nout mounted!

The problem then is that after the repartitioning, the changed partitions changed their uuids in /dev/disk/by-uuid.
The solution is to make an 'ls -l /dev/disk/by-uuid', then you will see the UUID of the root parition.

Output:
d984db9a-6c57-455e-b155-8ed7859da1b9 -> ../../sdb6

Then, 'sudo gedit /etc/fstab' and change the old uuid of the / mount point to the new uuid.

Example fstab:
UUID=d984db9a-6c57-455e-b155-8ed7859da1b9 / ext3 defaults,errors=remount-ro 0 1

Then reboot and you will have / properly mounted!

Good luck!

Thanks for that krisn - the uuid was indeed wrong in fstab, but correcting is doesn't bring back the previews. I guess I'll just have to keep my setting on 'always' for now....

DAZ

---

