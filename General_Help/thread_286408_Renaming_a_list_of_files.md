---
title: "Renaming a list of files"
date: 2006-10-27
forum: General Help
---

### Post by Ted_Smith on 2006-10-27
Sometimes, I lose the will to live with Linux! 

OK, I have a list of hundreds of camera photos all in a single folder (so no recurrsion is necessary)that are all named like this : 

img_1234.jpg.
img_1235.jpg
img_1236.jpg...etc

I want to rename all of them to something like 

ConferencePhoto1.jpg
ConferencePhoto2.jpg
ConferencePhoto3.jpg...etc etc

So simple in Windows, so bloody hard in Linux. 

I've tried mv. Cannot seem to work out how to get it to rename multiple files the same with the exception of an incremented numeric digit on the end before the extension. 

I've tried rename using the syntax of 

```

rename img_ ConferencePhoto img_*



```

but I get the error :

"Bareword "img" not allowed while "strict subs" in use at (eval 1) line 1." I have no clue what that means? Google does not seem to help either. It's to do with Perl I think. 

And before anyone suggests writing a script if if's and while loops, I'm sorry, I'm not that good enough. 

I use Gnome and so cannot use Krename either. 

Can anyone tell me (or paste a script for me to use) how on earth I can do this task? Surely people need to do this all the time? Cannot be that tricky? And if it is, it really shouldn't be in this day and age. 

Any help would be very much appreciated. 

Cheers

Ted

---

### Post by lazyart on 2006-10-27
Go to Synaptic package manager and look up mrename ... it might do what you're looking to do.

---

### Post by Ted_Smith on 2006-10-27
Yes, indeed it is! Excellent. Just what I was after. Thanks a lot my friend. 

Ted

---

### Post by lazyart on 2006-10-27
Cool... I never used it but stumbled across it looking for something else. :)

---

### Post by avantgardaclue on 2006-11-08
> **Ted_Smith said:**
> Yes, indeed it is! Excellent. Just what I was after. Thanks a lot my friend. 

Ted
Hi Ted, this sounds exactly what i am looking for, followed the instructions, downloaded mrename using synaptic, but where the hell did it go from there! How on earth do you use it!

Cheeeers

---

### Post by lazyart on 2006-11-08
did you try
mrename --help 
or 
man mrename

---

### Post by avantgardaclue on 2006-11-08
Hmmmm, nope! really am not into all this black art of command line, terminal stuff. If Linux/Ubuntu is going to succeed then all these things really do have to be mouse driven. Anyhow thanks for the pointer, i did read elsewhere that gThumb has batch renaming, which i have now got to work beautifully.

Cheeeers

---

### Post by lazyart on 2006-11-08
Glad you found a solution.  But don't be afraid of the command line.  It's your friend. :)

---

