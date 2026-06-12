---
title: "mounting a specific folder on a drive to a certain folder"
date: 2008-02-15
forum: General Help
---

### Post by ThndrChckn on 2008-02-15
Maybe im completely off by even thinking this is possible. But i have a problem were i have a lot of small drives. So what i want to do is combine all the folders of the same type of files into one. But i cant just put them all into one drive as i have many smaller drives. 

I want to know if i can take lets say a music folder from drive a and drive b then mount those folders to /home/user/music 

They are ntfs i already got all my drives mounted to just Files1-5 in my home folder but i just thought that if this were possible it would be nice instead of trying to go through each folder to find a certain thing. I have a lot of video clips and things like that that would be nice to have in one place.

---

### Post by lloyd_b on 2008-02-15
I can think of several ways to solve this, but the *easiest* is simply to use "symlinks" (symbolic links).  A symlink is simply a "pointer" to another file or directory somewhere else in the system.

As an example, say you have "/drive_a/mp3" and "/drive_b/mp3".  To connect these to "/home/user/music", in a terminal window:
```
ln -s /drive_a/mp3 /home/user/music/drive_a
ln -s /drive_b/mp3 /home/user/music/drive_b
```
and those "mp3" directories from "drive_a" and "drive_b" now appear to be attached to the "music" directory in your home directory.

If you don't mind the work, you could potentially do this with the actual files, rather than the directories, effectively merging the contents of "/drive_a/mp3" and "/drive_b/mp3" into a single directory:
```
ln -s /drive_a/mp3/some_song.mp3 /home/user/music/some_song.mp3
ln -s /drive_a/mp3/other_song.mp3 /home/user/music/other_song.mp3
ln -s /drive_b/mp3/another_song.mp3 /home/user/music/another_song.mp3
```

This could be automated with a shell script, so that all you'd need to do is tell it which directory, and all of the files in that directory would be linked to "/home/user/music", though there might be issues with duplicate file names.

Lloyd B.

---

### Post by PinkFloyd102489 on 2008-02-15
After re-reading your description, symlinking would be the way to go.

---

### Post by ThndrChckn on 2008-02-16
thank you that really helps now my next question is there a way to get these in fstab? or do i even need to worry about fstab? id like to just be able to everytime i start up have these files be were i want them to be. 

If i can do this through fstab how would i format it. They are ntfs so i dont know if that would cause any problems im using ntfs3g to mount drives now. 

Or if i cant use fstab is there a way to make this like a permanent symlink? or is that what i would be doing already?

ya im new to linux i know some stuff how to get simple stuff setup but not to much more.

---

### Post by ayampanggang on 2008-02-16
when using symlink, the links are permanent, just like the "shortcut" on windows do. after you symlink, it will still be there even after you reboot.

Are the music drives already automatically mounted? or did you manually mount them? if its the later then you'll need to add those drives to the fstab

the /etc/fstab file looks like this:
```

/dev/hda2	/	ext2	defaults	1 1
/dev/hdb1	/home	ext2	defaults	1 2
/dev/cdrom	/media/cdrom	auto	ro,noauto,user,exec	0 0

```

and to add your drives:
```

/dev/hda2        /drive_a          ntfs       defaults       0     0
/dev/hda3        /drive_b          ntfs       defaults       0     0

```
change /dev/hda2 and /dev/hda3 with your own disk drive, and change /drive_a and /drive_b to your mount points.

this might help you understand fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html#what](http://www.tuxfiles.org/linuxhelp/fstab.html#what)

---

### Post by lloyd_b on 2008-02-16
> **ThndrChckn said:**
> thank you that really helps now my next question is there a way to get these in fstab? or do i even need to worry about fstab? id like to just be able to everytime i start up have these files be were i want them to be. 

If i can do this through fstab how would i format it. They are ntfs so i dont know if that would cause any problems im using ntfs3g to mount drives now. 

Or if i cant use fstab is there a way to make this like a permanent symlink? or is that what i would be doing already?

ya im new to linux i know some stuff how to get simple stuff setup but not to much more.

A symlink is nothing but a special type of file, which tells the system "if the user tries to access me, give him this other file instead".  Once created, they are permanent, just like any other file.  You can even delete the file that the symlink points to, and the symlink will remain (though any attempt to access it will, of course, fail).

That's why I suggested symlinks - there are other solutions that involve "binding" one directory to another, but that *would* require some work in fstab to make permanent, and only works for directories, not files.

Lloyd B.

---

### Post by ThndrChckn on 2008-02-16
Alright well i was able to create symlinks for my video files. Now the later option that  lloyd_b posted with a shell script would that make it so when i go into the folder all i see is every file of music/video or would it be like it is now with a link to music1 music2 music3 etc.? I know it would still be a link but what would be cool is if when i went into the folder music it just had all the files listed not just how ever many drives have music on them.

---

### Post by chrisccoulson on 2008-02-16
[UnionFS]("http://en.wikipedia.org/wiki/UnionFS")

I really have no idea how to use it though

---

### Post by chrisccoulson on 2008-02-16
This article gives quite a good demonstration of unionfs: [http://www.linuxjournal.com/article/7714]("http://www.linuxjournal.com/article/7714")

---

### Post by lloyd_b on 2008-02-17
> **ThndrChckn said:**
> Alright well i was able to create symlinks for my video files. Now the later option that  lloyd_b posted with a shell script would that make it so when i go into the folder all i see is every file of music/video or would it be like it is now with a link to music1 music2 music3 etc.? I know it would still be a link but what would be cool is if when i went into the folder music it just had all the files listed not just how ever many drives have music on them.

After thinking about your situation, I don't think a script is really necessary...

Here's something for you to try (in a terminal window):
```
ln -s /drive_a/mp3/*.mp3 /home/user/music
```

This will create links for *all* ".mp3" files in "/drive_a/mp3" in the directory "/home/user/music".  Run it again, with "/drive_b/mp3/*.mp3", and for any other directories where you have mp3 files stored.  This will, with a few commands, create links for all of your mp3 files into that directory.

There may be some glitches.  For instance, if you have duplicate file names in two different directories, the second one will generate an error ("ln" will not overwrite an existing link, unless you specify the "-f" option).  But it should accomplish 99+% of what you want, with very little effort.

Give this a try (substituting the correct directory names and file extensions, of course) and see if that produces what you want.  Remember - worst case, you can just "rm /home/user/music/*" and start over, since deleting the links does not affect the file that's linked to in any way.

Lloyd B.

---

