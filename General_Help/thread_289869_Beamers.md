---
title: "Beamers?"
date: 2006-10-31
forum: General Help
---

### Post by Architeuthis on 2006-10-31
How well do beamers work under Linux? Are they supported, can i easily switch one on? Will i need special drivers, do i need to reconfigure xorg evertime i want to use one or do they just work out of the box?

---

### Post by reclusivemonkey on 2006-11-01
> **Architeuthis said:**
> How well do beamers work under Linux? Are they supported, can i easily switch one on? Will i need special drivers, do i need to reconfigure xorg evertime i want to use one or do they just work out of the box?

wtf are beamers???

In the UK, "beamers" is slang for BMW cars...

---

### Post by Architeuthis on 2006-11-01
Oh sorry in belgium we call [projectors]("http://www.dell.com/downloads/global/corporate/imagebank/projectors/3400mp_300.jpg") beamers, i thought it was a normal english word! :p

---

### Post by ~LoKe on 2006-11-01
> **reclusivemonkey said:**
> wtf are beamers???

In the UK, "beamers" is slang for BMW cars...

Uhm, nope.  "Beamers" is a slang word for BMW motorcycles.  The cars are "Bimmers".

---

### Post by reclusivemonkey on 2006-11-01
> **~LoKe said:**
> slang work

> **~LoKe said:**
> The cards are "Bimmers".

Dude, you can't even type english so what would you know.

---

### Post by reclusivemonkey on 2006-11-01
> **Architeuthis said:**
> Oh sorry in belgium we call [projectors]("http://www.dell.com/downloads/global/corporate/imagebank/projectors/3400mp_300.jpg") beamers, i thought it was a normal english word! :p

Is this a laptop you are using it with? Do you have a function key anywhere on the laptop that will switch to the output you have for the "beamer"?

---

### Post by ~LoKe on 2006-11-01
> **reclusivemonkey said:**
> Dude, you can't even type english so what would you know.

Wasn't paying attention, and "English" has a capital e.

And yeah, what would I know, I only worked at BMW. :-?

---

### Post by reclusivemonkey on 2006-11-01
> This message is hidden because ~LoKe is on your ignore list.

[-(

---

### Post by ehird on 2006-11-01
Petty arguments are totally inplace on a support forum, I agree.

---

### Post by Architeuthis on 2006-11-02
> Is this a laptop you are using it with? Do you have a function key anywhere on the laptop that will switch to the output you have for the "beamer"?

I'm asking this because my school has interest in migrating to Linux. One of my teachers asked me if Beamers/Projectors would work with Linux. 
Our school computers are all normal computers with standard keyboards, no special buttons for Projectors/Beamers etc.

---

### Post by Ramses de Norre on 2006-11-02
As far as I know a beamer looks like a normal screen to your pc, so the question simplifies itself to whether you'll manage to get dualheads set up on the pc's..

When there are no other screens but the projector connected, it will certainly work, when you've got a normal screen too you'll have to search a bit to get a properly configured xorg.conf.

What video cards are the machines using? 

And I'm from Belgium too and I also thought "beamer" was an english word:D Guess I learned something today :p

---

### Post by Lord Illidan on 2006-11-02
Let's dispense with the petty comments. I think this should go to Hardware Help. Have you got a specific problem with your hardware or are you just fishing around to see if there is a problem with projectors under Ubuntu? In that case, the post above should help.

---

### Post by Architeuthis on 2006-11-02
> As far as I know a beamer looks like a normal screen to your pc, so the questions simplifies itself to whether you'll manage to get dualheads set up on the pc's..

When there are no other screens but the projector connected, it will certainly work, when you've got a normal screen too you'll have to search a bit to get a properly configured xorg.conf.

This is what i wanted to know. Hmmm i was hoping it would work with a few clicks. I'm afraid most people on school don't want to configure xorg.conf everytime they want to use a beamer. I wish there was a easy solution to configure xorg.conf (is there one maybe?). 
But you can control dual heads with the ati and nvidia drivers and for intel with a program called intelswitch (or something like that), can anyone confirm this? 
Most of the computers use onboard intel cards i think.

@Lord Illidan: i'm just fishing around if there are problems with projectors under ubuntu.

---

### Post by Lord Illidan on 2006-11-02
> **Architeuthis said:**
> This is what i wanted to know. Hmmm i was hoping it would work with a few clicks. I'm afraid most people on school don't want to configure xorg.conf everytime they want to use a beamer. I wish there was a easy solution to configure xorg.conf (is there one maybe?). 
But you can control dual heads with the ati and nvidia drivers and for intel with a program called intelswitch (or something like that), can anyone confirm this? 
Most of the computers use onboard intel cards i think.

@Lord Illidan: i'm just fishing around if there are problems with projectors under ubuntu.

I don't think Ubuntu has that solution to graphically configure xorg.conf, at least not yet. :-k

Unless I am mistaken, SUSE has that functionality with Yast, give it a go.

---

### Post by Ramses de Norre on 2006-11-02
You wont need to configure it every time, if you do it once it's ok.
I guess you'll want the projector to be a clone of the primary screen so you wont notice any problems when there is no projector connected.

---

### Post by Architeuthis on 2006-11-02
> You wont need to configure it every time, if you do it once it's ok.
I guess you'll want the projector to be a clone of the primary screen so you wont notice any problems when there is no projector connected.
Reply With Quote

Ah, thats good! If it has to be configured once it won't be a real problem, windows refuges to recognize the projector only half the time, so a little work with the commandline wont make them (my school) say no to Linux. Thanks for the help all!

---

