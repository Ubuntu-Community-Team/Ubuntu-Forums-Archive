---
title: "rm -rf /*, today was the day..."
date: 2007-12-29
forum: General Help
---

### Post by Aualin on 2007-12-29
Ok, today was the day when i accidently run rm -rf /*, accidently being root...
I cant seem to find another thread about this. If you find one please link it :)
Anyway, i run the command for about a second. It deleted the /bin directory thats all i know.
I am downloading a ubuntu cd so i can check what more got deleted. I didn't have any backup's, but running ext3 maybe helps. Any tips on what i can do?

---

### Post by TidusBlade on 2007-12-29
Even the slightest will probably damage the computer, especially hr /bin directory I guess. 
And I dont think the CD will have the same files you used to have, so I would actually recommend a reinstall :( Unless copying them from the CD works.
Hope it works and Good luck ;)
EDIT: IF you followed this on the forums, I would go and report that user.

---

### Post by mellowd on 2007-12-29
How did you run it by mistake?

---

### Post by Aualin on 2007-12-29
easy...
i got a directory full of files starting with -
running rm -rf * wouldn't work
since it thought it was arguments
so i thought trying to run with rm -rf \* with a backslash would work
but accidently i used / instead of \
> **TidusBlade said:**
> 
EDIT: IF you followed this on the forums, I would go and report that user.
what do you mean if i followed this on the forums?

---

### Post by daou on 2007-12-29
> **Aualin said:**
> 
what do you mean if i followed this on the forums?

Probably meant if you were told by a user on these forums to run that command... which was not the case.

---

### Post by Aualin on 2007-12-29
ah, ok :)

---

### Post by mellowd on 2007-12-29
Ouch. Is it still running?

---

### Post by Aualin on 2007-12-29
hell, no! it was running for a second!

---

### Post by mellowd on 2007-12-29
I meant the pc :)

---

### Post by Aualin on 2007-12-29
ah, no it is not. Turned it off after a few seconds. (turned the power switch off so it wont do more damage than needed when shutting down)

---

### Post by mellowd on 2007-12-29
An interesting read:

[http://www.justpasha.org/folk/rm.html](http://www.justpasha.org/folk/rm.html)

---

### Post by Aualin on 2007-12-29
yep my easier way is the way i do it now :D

---

### Post by oldos2er on 2007-12-29
> **Aualin said:**
> ah, no it is not. Turned it off after a few seconds. (turned the power switch off so it wont do more damage than needed when shutting down)

 A better way would be to hit Ctrl-C. This will kill the current process running in a terminal.

---

### Post by t3hi3x on 2007-12-29
this is what id do:

throw you hd is another comp. if its a windows box you put in use these: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) (they do support ext3)

then save all the files you need. most of the should be there. dont write anything to the drive!!! in fact i think you can mount it as read only with those drivers.

copy all the crap you need off it. then if you want try to find software to recover anything still on the drive, but not in the allocating table. (shouldnt have lost much if you didnt run it long)

then do a reinstall of ubuntu. (i know this sux, but it would probably be best for the stability of the os)

lol and i know i dont have to tell you this, and sometimes you have to learn the hard way (i have too!), just be careful what you run as r00t.

good luck my friend! data loss is the worst for comp geek.

---

### Post by maybeway36 on 2007-12-29
I always use rm -rfv instead of rm -rf. That way, it tells me exactly what it's doing.

---

### Post by t3hi3x on 2007-12-29
very nice. never though of that. good rule of thumb.

---

### Post by ~LoKe on 2007-12-29
It's toast.  Time for a re-install.

---

### Post by Princegiri on 2007-12-29
i dont know how to help you get back the files you lost but since you didnt shred them, you should be able to retrieve them......search for software that can do that....

you can go into windows if you have it, and use software like SMART UNDELETE .. which you will have to C888K to get working ..... this worked me long ago... but it was for files on ntfs/fat..
dont know about ext3.... 
the main thing to do is to stop using/installing anything... that will overwrite and make the files unrecoverable...

---

### Post by geirha on 2007-12-29
> **Aualin said:**
> easy...
i got a directory full of files starting with -
running rm -rf * wouldn't work
since it thought it was arguments
so i thought trying to run with rm -rf \* with a backslash would work
but accidently i used / instead of \

what do you mean if i followed this on the forums?

For the record, this would make the files starting with - be treated as files instead of options. ```
rm -rf -- *
```

btw, if it was only files, why use -r?

---

### Post by schauerlich on 2007-12-29
```
alias rm='rm -i'
``` Put that in your /.bash_aliases to avoid future potential mishaps. :)

---

### Post by nick_h on 2007-12-30
Yes, -i is a good option.

It is sometimes easy to insert an extra space by mistake. For example, if the user intends to delete all files ending with txt then:
```
rm * txt
```
instead of:
```
rm *txt
```
would be rather unfortunate.

It is best to read the rm command before hitting the return key. :)

---

