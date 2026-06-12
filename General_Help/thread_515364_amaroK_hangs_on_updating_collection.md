---
title: "amaroK hangs on updating collection"
date: 2007-08-01
forum: General Help
---

### Post by semoff on 2007-08-01
I'm currently using amaroK 1.4.6 on Ubuntu Feisty.  It worked flawlessly for the first few months, until recently when I started adding files to my collection.  Now, every time amaroK goes to update my collection it hangs at 93% and i have to abort to use the program.  I'm aware I can delete my collection.db file as mentioned [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=495349"), but I am wondering if anyone knows another solution to this problem or if there's a way to identify the file causing the problem.

Cheers :guitar:

---

### Post by Shmifty on 2007-08-01
You can always change the setting "auto update collection" and see if manually updating it fixes your problem. If that doesn't help then you may wish to remove amarok entirely and then do a complete reinstall with all the recommended packages.

---

### Post by semoff on 2007-08-01
> **Shmifty said:**
> If that doesn't help then you may wish to remove amarok entirely and then do a complete reinstall with all the recommended packages.

what packages would those be?

---

### Post by semoff on 2007-08-02
as an additional note, everytime i build a playlist and press play, the combination of playing a track with the update causes amaroK to lock up

---

### Post by strabes on 2007-08-02
Maybe there's something wrong with one of the files? That might be why it hangs at the same place every time.

---

### Post by forestpixie on 2007-08-02
I found that it constantly crashed on update collection - it seemed to be a problem with the collection database.

Manual updating seemed to make no difference

So rather than reinstall - and believe me I tried all the combinations I could think of - I  deleted the collection database, which was much less painful.

If you still have problemsd try it - the database is in a hidden folder

/home/kevin/.kde/share/apps/amarok

---

### Post by semoff on 2007-08-02
ahhh, after a lot of frustration i know where the collection file is...i just didnt want to have to resort to rebuilding...oh well though, thanks for the help everyone

---

### Post by billybigrigger on 2008-06-27
I had a hard time figuring out why oh why Amarok would not scan my full mp3 collection.  It continually hung up at 54%.  I tried removing and reinstalling Amarok and all sorts of other things.  Then I figured perhaps its a bad file.  Found out that there is a scan log in ~/.kde/share/apps/amarok/collection_scan.log

In that file I found the name of a single audio file.  I didnt care for the file anyway so I deleted it, and POW, Amarok scanned my entire collection in a matter of seconds.

ubuntu 8.04
amarok 1.4.9.1
mp3 collection on seperate SATA HD

cheers

---

