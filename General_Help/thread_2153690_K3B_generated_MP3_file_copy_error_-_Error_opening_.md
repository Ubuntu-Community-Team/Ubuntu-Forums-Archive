---
title: "K3B generated MP3 file copy error - Error opening file 'FileName': Not a directory"
date: 2013-06-12
forum: General Help
---

### Post by Sn3akyP3t3 on 2013-06-12
I'm encountering a very strange error that I cannot determine how to workaround or diagnose the actual cause.  I'm using K3B to create MP3s from a CD that I own so that I can play it back without need for the CD.  The rip process is being completed by K3B and output file format is .MP3 using LAME.  This particular CD, number 2 of 2, does have CDDB information that populated the metadata tags.  Note that disk 1 of 2 didn't have any metadata tags pulled from the CDDB and did not encounter failure to copy/move as the 2nd cd is encountering.

This is the error I'm encountering:
```
Error while copying "02 - The Four Seasons: "Spring" Pastoral Dance.mp3".
There was an error copying the file into /media/Music/Ripped/Classic Baby/Various - Classic Baby.
Error opening file '/media/Music/Ripped/Classic Baby/Various - Classic Baby/02 - The Four Seasons: "Spring" Pastoral Dance.mp3': Not a directory
```

Output of directory listing all files that failed to move with similar error messages as above:
```
username@hostname:~/Rips/Various - Classic Baby$ ls -l
total 36468
-rw-rw-r-- 1 username username 4111038 Jun 11 22:14 02 - The Four Seasons: "Spring" Pastoral Dance.mp3
-rw-rw-r-- 1 username username 2142874 Jun 11 22:14 03 - Water Music Suite No. 1 in F major: Overture.mp3
-rw-rw-r-- 1 username username 2014139 Jun 11 22:14 04 - Water Music Suite No. 1 in F major: Minuet.mp3
-rw-rw-r-- 1 username username 3023912 Jun 11 22:14 05 - The Four Seasons: "Spring" Allegro.mp3
-rw-rw-r-- 1 username username 2212682 Jun 11 22:14 06 - Concerto for Two Horns in D major: Allegro Assai.mp3
-rw-rw-r-- 1 username username 1632964 Jun 11 22:15 07 - Come Ye Sons of Art, Away: Sound the Trumpet.mp3
-rw-rw-r-- 1 username username  958766 Jun 11 22:15 08 - Royal Fireworks: Minuet No. 1.mp3
-rw-rw-r-- 1 username username 1637532 Jun 11 22:15 09 - Royal Fireworks: Minuet No. 2.mp3
-rw-rw-r-- 1 username username 2318415 Jun 11 22:15 10 - Water Music Suite No. 1 in F major: Bourrée.mp3
-rw-rw-r-- 1 username username 3261689 Jun 11 22:15 11 - Xerxes: Largo.mp3
-rw-rw-r-- 1 username username 2280355 Jun 11 22:16 12 - Suite in A minor: Rejouissance.mp3
-rw-rw-r-- 1 username username 3229546 Jun 11 22:16 13 - Hexachordum Apollinis: Aria Prima.mp3
-rw-rw-r-- 1 username username 1675152 Jun 11 22:16 14 - La changeante: Les Scaramouches.mp3
-rw-rw-r-- 1 username username 1788875 Jun 11 22:16 16 - Tafelmusik Part 3, Suite in B flat major: Bergerie.mp3
-rw-rw-r-- 1 username username 1329070 Jun 11 22:17 17 - Suite in D major: Gavotte.mp3
-rw-rw-r-- 1 username username 3562258 Jun 11 22:17 18 - Flute Concerto in D major, No. 3: Allegro.mp3
```

Source directory is local to the workstation.  Destination directory is a CIFS mounted directory running off UNRAID.

---

### Post by SeijiSensei on 2013-06-12
If you are using Kubuntu or some other KDE-based distribution you can rip a CD simply by opening the disc in Dolphin.  Using its "kio-slaves" KDE will present you with multiple virtual representations of the CD in different formats like FLAC, ogg, and MP3.  Then you just copy the items from the representation you prefer to the target location.

---

### Post by Sn3akyP3t3 on 2013-06-13
I'm sorry I didn't post my PC rig specs.

Ubuntu: Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-45-generic
RAM: 7.8 GiB
CPU: AMD Phenom(tm) II X4 940 Processor × 4 

@[[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195") I didn't know about KIO until you mentioned it.  Many thanks and I'll be sure to utilize it if I run KDE anywhere :)  If anyone is looking for this particular reference made for music conversion use "audiocd:/".  Also, check out the brief introduction to KIO-slaves here: [http://everydaylht.com/howtos/desktop/kio-slavery/http://everydaylht.com/howtos/desktop/kio-slavery/](http://everydaylht.com/howtos/desktop/kio-slavery/http://everydaylht.com/howtos/desktop/kio-slavery/)

---

### Post by Sn3akyP3t3 on 2013-06-20
I did fail to mention that 2 files of the 18, numbers 1 and 15, did move just fine without fail.  These were the file names:
[I]-rwxrwxrwx 0 username username 5380330 Jun 11 22:18 01 - Canon in D major.mp3
-rwxrwxrwx 0 username username 2178347 Jun 11 22:18 15 - Trumpet Voluntary.mp3[/I]
I do immediately notice a lack of colon in the filename, but if I simply remove it and attempt to move the file the same behaviour is witnessed.

I would like to focus on first trying to find out what would cause the error received for copy/move operations, "not a directory".  What would cause that error?  Is there something wrong with the file names such as a character that flags it?  When I get an opportunity I'll look at the file with a hex editor to share the file signatures... perhaps that is the problem?

---

### Post by EchoTech on 2013-06-23
I notice that the word "Spring" is the only word with quote marks.  Something to check?

---

### Post by Sn3akyP3t3 on 2013-06-27
Removed the double quotes and still no joy to move.  I noticed that my first post failed to note that all in the second code block were files that failed to move with similar errors as in the first code block provided.  I'll update my post.  I think the problem is beyond the file name.  What steps does the OS go through to validate a file before moving it.  I would like to check there to see if the validation is failing.  I haven't looked at the file's digital signature, but if nobody has any guiding suggestions I'll start with looking at it with a hex editor.

---

### Post by claracc on 2013-06-27
Could it be a question of permissions?

I observe that the two correct moved files have: -rwxrwxrwx permissions while that with errors only have: -rw-rw-r--

---

