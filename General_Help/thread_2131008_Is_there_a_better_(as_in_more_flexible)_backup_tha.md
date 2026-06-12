---
title: "Is there a better (as in more flexible) backup than Deja Dup?"
date: 2013-03-31
forum: General Help
---

### Post by 777funk on 2013-03-31
I'm having [some trouble]("http://ubuntuforums.org/showthread.php?t=2130920&p=12581697#post12581697") with the Deja Dup program and would like to see if there's anything out there that will give a little more flexibility.

---

### Post by CaptainMark on 2013-03-31
What did you have in mind when you say flexible, what do you need to do? To be honest when it comes to back ups I personally think you're better off just jotting yourself a cron script or anacron script, and you can backup exactly what you want, when you want

---

### Post by 777funk on 2013-03-31
Thanks for that Mark,
I like the scheduling and folder selection that Deja Dup ha. That part is nice and it also knows when I plug the removable drive in. So it's smart in many ways. I'm just not getting the functionality I need out of it in that I can't easily just get one old version of a file etc. I think it's because it's on a Mounted (windows) location that I'm backing up. 

Other than that it's been good. I've also seen some complaints of not being able to un-encrypt the saved data after a crash. So that worries me a little. Saved data that I won't be able to access later isn't exactly saved data. I want to make sure I have a good system for backup that I can be sure will work when I need it.

---

### Post by rewyllys on 2013-03-31
I've had a very good experience with Lucky Backup.  It's easy to use and has been flawlessly reliable for me during nearly two years of use.

---

### Post by memilanuk on 2013-03-31
> **rewyllys said:**
> I've had a very good experience with Lucky Backup.  It's easy to use and has been flawlessly reliable for me during nearly two years of use.

How many times have you actually had to restore from it during that time?  

I'm not poking fun at you; I'm serious.  This always seems to be the acid test of a backup system... every program out there makes backing up 'seem' easy; restoring is where it gets ugly.  For me, the problem with deja-dup is that its pretty much all-or-nothing, have to restore an entire file-set... I believe there are ways around that using the underlying command-line utils (duplicity, etc.) but the convenience quotient goes out the window at that point.

---

### Post by rewyllys on 2013-03-31
> **memilanuk said:**
> How many times have you actually had to restore from it during that time?  

I'm not poking fun at you; I'm serious.  This always seems to be the acid test of a backup system... every program out there makes backing up 'seem' easy; restoring is where it gets ugly.  For me, the problem with deja-dup is that its pretty much all-or-nothing, have to restore an entire file-set... I believe there are ways around that using the underlying command-line utils (duplicity, etc.) but the convenience quotient goes out the window at that point.
I assume the "it" in your question refers to Lucky Backup, although the thrust of your second paragraph makes me wonder which of the backup programs mentioned in this thread is the one about which you actually intended to question me.

The answer to the question, "how many times have I actually had to restore from Lucky Backup in nearly two years?", is that for obvious reasons, I lack an exact count.  However, I can assure you that I've had occasion to restore from Lucky Backup several times, at least.  In fact, as it happens, the most recent such occasion was just yesterday. And, to make my point more strongly, my attempt to restore yesterday was successful. Also, it was convenient and easy; indeed, it took me perhaps all of 30 seconds to get the earlier version of the file I needed.

Since you clearly intended to question my honesty, I will add that I would certainly not have called my experience with Lucky Backup "flawlessly reliable" if that were not, in fact, the case.

Please reflect a little more carefully on the implications of your questions.

---

### Post by memilanuk on 2013-03-31
> [COLOR=#000000]Since you clearly intended to question my honesty[/COLOR]
Nobody was questioning anyone's honesty, simmer down.  I was simply asking whether you'd actually used it to restore in a less-than-trivial situation (like more than a couple files).  Seeing as you have, thanks for the information.


> [COLOR=#000000]Please reflect a little more carefully on the implications of your questions.[/COLOR]
Please read a little less implication into my questions...  I'll call a spade a spade if it comes down to it.  There will be no 'implication' involved.

---

### Post by CaptainMark on 2013-04-01
You may want to look into rsync, its a cli tool that can be used to make incremental backup of any folders, its more useful for writing into bash scripts, but i have a script which uses it to back up to a usb drive and when i need to get some files back its as easy as  grabbing the files i want back off the usb drive and plonking them where i wanted them

---

### Post by Lars Noodén on 2013-04-01
+1 for [rsync](https://help.ubuntu.com/community/rsync)

That will give you maximum flexibility and your other backup packages are probably just a fancy front end for it anyway.  Ass mentioned, it is also possible to incremental backup with it.

It works over SSH, too.

---

