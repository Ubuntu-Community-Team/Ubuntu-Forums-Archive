---
title: "Does Document Viewer store temporary files?"
date: 2014-10-06
forum: General Help
---

### Post by LaserHosen on 2014-10-06
Hello all. First post but a long time reader.

I've recently been using [Document Viewer]("https://apps.ubuntu.com/cat/applications/natty/evince/") by evince to print out some .pdf files.

I'm using Lubuntu on my netbook and Ubuntu on my main PC. Both versions are 14.04 and Document Viewer comes as standard in Lubuntu. It's an excellent light weight viewer and printer for PDF files.

The stuff I've been printing out is of a sensitive nature (financial details) and I have used the 'shred -nxx' terminal command before deleting the files once they're printed: to minimise the chance of anyone seeing the financial details (Bitcoin keys, if you are curious).

I've looked at my hidden directories and can't find one called 'document viewer' or 'evince' and I was just wondering if I have completely cleared the sensitive files now that I have printed them out and stashed them.

Is there an equivalent to Windows' local/appdata directory where a copy of my .pdf's could still be hiding?

Thank you.

---

### Post by vasa1 on 2014-10-06
Will /etc/apparmor.d/usr.bin.evince offer any clues?

---

### Post by grahammechanical on 2014-10-06
I use Evince but not for printing. I do not see any evidence of an Evince configuration file (.evince) in /home or any evidence that Evince is making use of /home/username/.cache.

This will give some information about Evince.

[https://wiki.gnome.org/Apps/Evince](https://wiki.gnome.org/Apps/Evince)

Regards.

---

### Post by dragonfly41 on 2014-10-06
Perhaps rare .. but look for unprinted jobs (.ps files) if your printer is disconnected or cannot print

[http://localhost:631/jobs](http://localhost:631/jobs)

---

### Post by The Cog on 2014-10-06
You should also worry about the temporary files the print spooler software uses. They may well be deleted by the spooler after use, but they won't be shredded, just a normal filesystem delete.

---

### Post by LaserHosen on 2014-10-06
Thanks for the replies. I've had a poke about in the areas suggested and the app doesn't appear to cache anywhere once the document is shredded/deleted.

**dragonfly41**, that is a neat trick for accessing the CUPS queue! My queue says all but the most recent job can't be reprinted, due to the files being missing (deleted). The most recent one that appears to exist I have set to reprint and it's waiting for my printer to be connected (I'm using USB). I will have a go at reprinting that one tomorrow as it's late to start printing stuff out now.

I'm not too bothered about my printers cache: the keys themselves are encrypted, so if anyone broke in and stole my printer they'd also need to know the password to decrypt the Bitcoin keys. I assume that most printers with a limited amount of local storage will wipe old jobs when new documents are printed as the onboard cache is a limited resource, so if I print out a few emails and word processing documents over time the printer cache will eventually push out the old data.

Cheers people!

---

### Post by dragonfly41 on 2014-10-07
Just as an exercise in idle curiosity and depending on the risk you could see if **testdisk** (in Ubuntu Software Centre) could forensically recover deleted cache files.

The original printed documents might have been "shredded" (how many passes?) .. but the question is can printer cache files be so recovered by testdisk or photorec?

---

