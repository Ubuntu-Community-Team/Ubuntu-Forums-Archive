---
title: "No sound?"
date: 2008-02-17
forum: General Help
---

### Post by 500sd on 2008-02-17
My sound just stopped working about 20 minutes ago...I don't know what happened?
I removed Icedtea java if that has anything to do with it

---

### Post by 500sd on 2008-02-17
Any help?

---

### Post by Crafty Kisses on 2008-02-17
> **500sd said:**
> My sound just stopped working about 20 minutes ago...I don't know what happened?
I removed Icedtea java if that has anything to do with it

Is this on websites only, or like even mp3's wont play?

---

### Post by 500sd on 2008-02-17
No its everything...not even system noises work.

---

### Post by 500sd on 2008-02-17
Oh my gosh can someone help?

---

### Post by 500sd on 2008-02-17
Anyone...

---

### Post by RippDrive on 2008-02-17
Ok, oddly enough I had the same thing happen to me not too long ago.

I am by no means an experienced linux user so bare with me.

I have been using Ubuntu 7.10 for about 3 weeks now with not many problems. Sound worked fine out of the box. Today I was watching a video in MPlayer, everything was going great. As soon as the video ended I lost all sound.

I have tried a few different things and played around a little. Neither my headphones or speakers work so I assume it's not the peripherals. I still have mic support so I am thinking the hardware is being detected/works correctly.

I have checked for conflicts but there appear to be none, The sound device is free. I have also tried running sound applications as root but that doesn't help either. Fiddled with everything in the sound preferences, didn't help.

I really have no idea what else to try/look at.

If there is any other information that would help I will be glad to supply it. I'll keep searching for a fix and let you know if I find anything.



EDIT:
Alright, that's interesting. Popped in my live CD, sound worked fine.
So I figure it must be some kind of a driver issue? At least something software related. Any way I can just repair my current install. Maybe just write over all the sound configuration/folder etc? Anyone able to point me in the right direction?

---

### Post by 500sd on 2008-02-17
Hmm. I think my case is slightly different. I tried to play system sounds under the sounds panel, but it says some error about my sound no being free.

---

### Post by 500sd on 2008-02-17
Is there like a volume mixer anywhere on ubuntu? Maybe somehow mine got messed up and the volume got turned down...idunno

---

### Post by Crafty Kisses on 2008-02-17
> **500sd said:**
> Is there like a volume mixer anywhere on ubuntu? Maybe somehow mine got messed up and the volume got turned down...idunno

You can download a sound mixer from the repositorys, it's called "kmix".

---

### Post by 500sd on 2008-02-17
Would that fix it?

---

### Post by RippDrive on 2008-02-17
> **500sd said:**
> Is there like a volume mixer anywhere on ubuntu? Maybe somehow mine got messed up and the volume got turned down...idunno

Got it for ya, Fixed my problem. Not sure if it will help you.

Add Volume control to a bar
Right click > Add to Panel > Search for "volume" > Toss that up somewhere

From there you should be able to double click/right click to open the control panel. 
My problem was my PCM was muted. Whatever PCM is :P


Alternatively, If you want to check for a sound conflict enter "cat /dev/urandom >> /dev/dsp" into the terminal. If your sound device is free you will hear static, otherwise you will get an error. Not sure where you would go from there but at least you will be able to see if that's the problem or not... =/

---

### Post by 500sd on 2008-02-17
Ill try that soon.
( im on xp atm )

---

### Post by Crafty Kisses on 2008-02-17
> **500sd said:**
> Would that fix it?

Yeah, possibly.

---

### Post by LorisMaria on 2008-02-18
Don't know if the problem is similar, but I've been having this intermitently for a while. Sometimes, after an system update (I don't bother to check what it's doing, I approve any updates available), the sound is gone, completely. Last two times, it was fixed solely by doing the next upgrade. This time it wouldn't work.

But looking at the answers here, I went to the volume controls to check possible muted PCM. Wasn't muted, but the second tab "switches" showed that the external amplifier box was checked. I unchecked it, as I'm not using the external amplifier, should that make any difference. Bingo. 

So: volume controls, second tab, "external amplifier" option, uncheck. See if that works for you.

---

### Post by 500sd on 2008-02-18
Well i just restarted my comp...and my sound is back lol

---

