---
title: "do I have a virus or did my laptop enter the twilight zone?"
date: 2007-02-08
forum: General Help
---

### Post by lyceum on 2007-02-08
okay, I have been using Ubuntu since Dapper came out, and now that I am feeling comfortable, some uncomfortable things happened. 

1. I used Crossover to run MS Office and while testing I wrote a Word doc for school. I saved it to my flash stick and took tried to open it on one of the PC in the school's computer lab. It would not open. I took it to a different PC in the lab with the same problem. Put the stick back in my laptop and Word would not open the file there either. 

So, I opened the file with OOo, as it will open anything, and it was fine. I copied the whole document and pasted it on MS Word and the text changed to what looked like puked up html code. So I pasted the text to a new OOo doc and saved it as a .doc file and everything was fine. Welcome to the twilight zone! I was then able to print on the school's PC. Though that was odd, but was just thankful that OOo saved my homework!

2. I have been puzzling over this for a week, and I go up this morning and Ubuntu would not take my password. So I manually turned my laptop off and restarted, the password took, so I thought it must be something weird, maybe I typed it in wrong, I don't know. So I went to update, and the update would not take my password! 

I wiped the machine and re-installed an new OS. I just didn't feel like dealing with the password issue and bla bla, but anyhow, any reasons why these things would happen?

thanks!

---

### Post by Crayoneater on 2007-02-08
it could be possible that you had caps lock on by mistake...that would cause your password to be incorrect, unless your password is all uppercase letters...

---

### Post by lyceum on 2007-02-08
Yeah, I checked that. The cap locks were not on either time. :(

---

### Post by nereid on 2007-02-08
A virus on a Linux machine is very unlikely and belive it or not, Wine/Crossover Office are very poorly at executing virii (somewhere around the web is a little article where somebody tried that just for fun).

The password thing is indeed very strange. Maybe some first signs of a hardware problem?

---

### Post by jimhaddon on 2007-02-08
you said you saved it on a pen drive? Did you make sure you ejected it first before removing it?

---

### Post by lyceum on 2007-02-08
> **nereid said:**
> A virus on a Linux machine is very unlikely and belive it or not, Wine/Crossover Office are very poorly at executing virii (somewhere around the web is a little article where somebody tried that just for fun).

The password thing is indeed very strange. Maybe some first signs of a hardware problem?

I hope not! I just bought the thing less than 6 months ago! But you could be right...
I was worried that Crossover was the problem, but I cannot see how. I do not use root for anything. 

> **jimhaddon said:**
> you said you saved it on a pen drive? Did you make sure you ejected it first before removing it?

Yes. Right click, eject. Also, none of the other things I had there effected.

---

### Post by houstonbofh on 2007-02-08
Run the built in memtest at your next boot just to be sure.  Leave it up overnight perhaps.
Also, if you print to a pdf, you can always print that at school.  Just another handy way to cover yourself.

---

### Post by lyceum on 2007-02-08
> **houstonbofh said:**
> Run the built in memtest at your next boot just to be sure.  Leave it up overnight perhaps.
Also, if you print to a pdf, you can always print that at school.  Just another handy way to cover yourself.

Well, I already reformated the hard drive and re-installed the OS, so I shouldn't have any more problems. I jsut thought is was odd and wanted to see if anyone had ideas as to what was going on.  Good advice though, thanks!

---

### Post by az on 2007-02-08
> **lyceum said:**
> Well, I already reformated the hard drive and re-installed the OS, so I shouldn't have any more problems. I jsut thought is was odd and wanted to see if anyone had ideas as to what was going on.  Good advice though, thanks!

It is not unlikely that your problems are hardware-related.  I suggest you do the memtest.  Run badblocks as well to look for hard disk errors.



sudo badblocks -s /dev/sda1 (or whatever your partition is)

---

### Post by lyceum on 2007-02-09
> **az said:**
> It is not unlikely that your problems are hardware-related.  I suggest you do the memtest.  Run badblocks as well to look for hard disk errors.



sudo badblocks -s /dev/sda1 (or whatever your partition is)

okay, will do this evening. Thanks everyone for posting.

---

### Post by lyceum on 2007-02-10
Well, I ran the test, no problems, so I guess I must have just messed things up somehow... Thanks again everyone!

---

