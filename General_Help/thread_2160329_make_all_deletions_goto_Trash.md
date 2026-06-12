---
title: "make all deletions goto Trash?"
date: 2013-07-06
forum: General Help
---

### Post by JohnnyC35 on 2013-07-06
I was wondering if there was a way to make any files deleted from any program or function to goto Trash. I was thinking this after accidently deleting my torrent list from Transmission. This is also when I noticed that there is no log file for Transmission but anyways. I couldn't seem to undelete the content of my download folder but I was able to recover the torrents. At any rate. I see there is a program to make the command line delete files to the Trash but is there a way to get Transmission do the same?  Thanks for any info

---

### Post by ohnonot on 2013-07-09
i've had the same problem over and over and have been wondering myself.
i think not, but it would be good.
what is this command line program you mention?
if transmission and other programs use 'rm' shell command, it could be a replacement.
though i doubt. but worth a try.

---

### Post by JohnnyC35 on 2013-07-09
Here's the URL: [http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html](http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html)

It's a couple years old but I think everything still holds true.
Just did a quick search and I am unable to find if Transmission uses rm or not

---

### Post by llamabr on 2013-07-09
How did you delete these files?

---

### Post by ohnonot on 2013-07-10
> **JohnnyC35 said:**
> Here's the URL: [http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html](http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html)
It's a couple years old but I think everything still holds true.
Just did a quick search and I am unable to find if Transmission uses rm or notyes, that's pretty much what i thought.
i really don't know about transmission (and other programs). 
i sent a question to #transmission irc channel...

---

### Post by ohnonot on 2013-07-10
seems we were both barking up a non-existant tree...

transmission irc channel, just now:>  is it pssible to remove torrents and their files to the trash? we're discussing this here: ubuntuforums.org/showthread.php?t=2160329
<Cursarion> I've thought Transmission does that
<Cursarion> though it could be depending on OS
<geirha> the gtk client uses the trash, but not the daemon (obviously)
<mus> yes, how stupid of me. right clicking, remove & delete, i find the file in the trash. but the *.torrent file is gone - could i reconstruct a torrent when i download the same torrent file from the interwebz and point it to the restored file?
<geirha> yes, it will automatically check if the torrent data exist in the download dir, and check that the checksums match the ones in the torrent

---

