---
title: "apt keeps asking me to insert the cd"
date: 2008-06-07
forum: General Help
---

### Post by pedrotuga on 2008-06-07
I unchecked the  cd repository in the synaptic sources proprieties, I checked my sources.list and it only has a the usual http repos. I made an apt-get update.
But still when i try to install build-essential, it keeps asking me to insert the cd.
What the heck am i missing?

---

### Post by wolfen69 on 2008-06-07
i think it *needs* the cd for build essential. does it ask for a cd for anything else?

---

### Post by drs305 on 2008-06-07
Nevermind - you did it already. 

I've never been asked to insert my cd when I've added build-essential via synaptic - unless I'm misunderstanding.

---

### Post by wt8008 on 2008-06-07
Nevermind - I shouldn't post when I am a little sleepy.

---

### Post by Sinkingships7 on 2008-06-07
It's in the Hardy repos. I'm guessing you're using Gutsy? Then yeah, you'll need the CD. Or get it from [here]("http://http.us.debian.org/debian/pool/main/b/build-essential/build-essential_11.3_i386.deb").

---

### Post by Oldsoldier2003 on 2008-06-07
> **pedrotuga said:**
> I unchecked the  cd repository in the synaptic sources proprieties, I checked my sources.list and it only has a the usual http repos. I made an apt-get update.
But still when i try to install build-essential, it keeps asking me to insert the cd.
What the heck am i missing?

comment out the cd in your /etc/apt/sources.list

---

### Post by Oldsoldier2003 on 2008-06-07
> **drs305 said:**
> Nevermind - you did it already. 

I've never been asked to insert my cd when I've added build-essential via synaptic - unless I'm misunderstanding.

build essential is on the cd even though it is not installed to a default ubuntu system. Most people remove the cd from their sources list so it doesnt ask...

---

### Post by pedrotuga on 2008-06-08
Yes, it's a gutsy instalation.

Come on guys, read my message with a bit more atention. **I made sure that the CD repository was not set to be used.**

Anyway, I'll just use the deb ackage that Sinkingships7 linked.
Thank you.

I won't bother find out why this happens, i guess it's a bug or so. I'll just update to Hoary afterwards, I just hope I have enough hard drive for that.

---

### Post by Sef on 2008-06-08
> I won't bother find out why this happens, i guess it's a bug or so. I'll just update to Hoary afterwards, I just hope I have enough hard drive for that.

Update to Hoary?  Is that a mistake or a bit of geek humor?

---

### Post by pedrotuga on 2008-06-08
Lol, I meant Hardy. I still got mixed up with the naming. What's with using the same Initials than an old release :confused: :confused:

---

