---
title: "iPod Backup Script"
date: 2007-06-13
forum: General Help
---

### Post by alex-desktop79 on 2007-06-13
I need a script to backup my iPod.
Unfortunatley, all backup programs, in Windows and in Linux, fail to back it up.
The only way to back it up that I have found is to search the ipod for files containing "." and copy all the .mp3, .m4a, and .aac files to a backup folder.

Unfortunatley again, iPod music files are named XXXX.mp3 where X is a random letter. Often two have the same name in a diffirent directory (.../F00/AAAA.mp3 and .../F01/AAAA.mp3)

So I have to manually copy the file and overwrite when backuping.

I'm looking for a script that will be able to do this for me, if possible, or another solution.

Thank You.
Alex

---

### Post by alex-desktop79 on 2007-06-13
bump.

Basically a script to scan for audio files and copy them to a dir, autorenaming duplicates.
I have no language experiance but I am quite sure it is fairly simple to make. It would also be good for a lot of people.

---

### Post by safeness on 2008-02-13
The easiest way to do the backup (minus renaming) would be to just use tar like this from inside your music directory:

tar -cvf * | tar -xv -C /backup_goes_here

This way of copying is really fast and I've used it a lot for backups. If you wanna do renaming, etc. I'd suggest looking into sed or maybe perl. It'll be a bit of reading, but you'll learn a ton.

---

### Post by iPaulo on 2008-07-11
I use a software named [Aniosoft iPod to computer Pro](http://www.aniosoft.com) to do this. Its cool!

---

