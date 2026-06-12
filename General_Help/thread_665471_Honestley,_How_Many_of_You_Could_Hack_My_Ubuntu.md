---
title: "Honestley, How Many of You Could Hack My Ubuntu"
date: 2008-01-12
forum: General Help
---

### Post by Nimaran on 2008-01-12
Okay, could some of you all really good linux pros hack my Ubuntu installation if you really wanted to?

---

### Post by skymera on 2008-01-12
well in my opinion.
pretty tricky.

if they WERE to get in the could do damage.

unless you change the sudo password from your login.
then all threy could do is delete your music. oo chilling?

well thats coming from me, i cant even break into a biscuit tin let alone a computer

---

### Post by Nimaran on 2008-01-12
I guess I was just a little bit concerned that although everyone says the security is great. The source cods is out there for anyone, and dosen't that make it easier to hack?

---

### Post by earobinson on 2008-01-12
hacking has a very wide range of things, even social engenering is considered hacking by some

so in order to fix your problem please type ... could by some be considered a hack

---

### Post by Nimaran on 2008-01-12
I guess my definition is just accessing my computer, and personal files without my permission via an internet connection or something of the like.

---

### Post by matthew on 2008-01-12
Anyone educated in certain aspects of operating system security, who also has physical access to any computer, get in. It's only a matter of time.

If you are asking who among us might be able to access your computer remotely, probably none of us. Unless, of course, you have chosen a really simple password and manually opened ports from the default configuration...or start running random commands and/or programs people give you without knowing what they are or why.

---

### Post by Nimaran on 2008-01-12
Okay, thank you that makes me feel better. I guess I was just a bit concerned knowing that the source code is out there. So my Linux box is safe?

---

### Post by Steveway on 2008-01-12
Security through obscurity is never safer than the open-source way.
If a hacker finds a hole, bug etc in an open-source program then he most propably is gonna fix it and sends the fix to the author.
Hackers that find bugs in Closed-source programs can't do this so they do what most of them do, they use the bugs to break into the systems etc. (Many do this so that the authors recognize that bug as critical and close them.)
Open-source software is more secure than Close-source. -my statement

---

### Post by bwhite82 on 2008-01-12
Gaining remote access to your machine: difficult
Bringing your system down: easy (nessus)

In my case, I audited my machine remotely from another machine and found that nessus simply brought down my satellite modem before it even reached my internal network.

---

### Post by matthew on 2008-01-12
> **Nimaran said:**
> Okay, thank you that makes me feel better. I guess I was just a bit concerned knowing that the source code is out there. So my Linux box is safe?It's quite safe. 

The fact that the source code is available actually [contributes to security]("http://catb.org/%7Eesr/writings/cathedral-bazaar/cathedral-bazaar/ar01s05.html") ([from here]("http://catb.org/%7Eesr/writings/cathedral-bazaar/cathedral-bazaar/")) because as soon as security issues are noticed, word spreads and they are fixed quickly, generally within hours or days of the developers hearing about them.

---

### Post by Nimaran on 2008-01-12
> **Soldierboy said:**
> 
Bringing your system down: easy (nessus)

Bring down as in stop my internet connection for a while or bring down as in break it and destroy all my files.

---

### Post by bwhite82 on 2008-01-12
> **Nimaran said:**
> Bring down as in stop my internet connection for a while or bring down as in break it and destroy all my files.

Thus far, testing on my system, only brings it down for a while. The plugins are numerous for nessus, however, and many of them warn of irreversable damage. For obvious reasons, I do not test those. :)
To be quite honest, Nessus is a very powerful tool designed for sys-admins to check for vulnerabilities. I wouldn't mess with it unless you know what you are doing.

---

### Post by Nimaran on 2008-01-12
Oh, okay. 

Thank you very much all of you guys, it means a lot to have such helpful people always ready to answer whatever questions may be thrown at them. I've said it before in other threads, but I think the support is truly the best aspect of Linux and open source stuff in general. Again thank you very much.

---

### Post by Mud.Knee.Havoc on 2008-01-18
> **Nimaran said:**
> I guess I was just a little bit concerned that although everyone says the security is great. The source cods is out there for anyone, and dosen't that make it easier to hack?

Security is great in terms of spyware/viruses/etc.  You don't have to worry about these things if you're using Ubuntu.  I'm sure the day will come when people start putting together malicious .debs, but as long as you stick to the repos, you'll be fine.

Security is also great in terms of vulnerabilities... Ubuntu's easy to keep up to date with the latest security patches.  If you're browsing sites and doing normal day to day stuff, you present a far smaller target than the gazillions of Windows users out there.

If somebody really wanted to get into your computer, though, and by "you" I mean Nimaran in particular (not just somebody at random), he will - sooner or later - if he's absolutely dedicated to taking your machine down.  If you have any services running on open ports, sooner or later there will be a 0 day vulnerability that this crazy hacker stalker will be able to take advantage of before you get it fixed.  Or maybe he'll sniff your laptop's passwords that you're sending in the clear in Starbucks - and maybe you use the same passwords for your MSN as you do for your Gmail as you do for your router. :D

Hackers can get into systems running any OS.  They just need the right tools, planning, patience and be ready to jump at a moment's notice.  That's why you see government sites get defaced every so often.  Their admins have to try to keep up and patch vulnerabilities ASAP, but hackers will always have a head start.

Having said that, as long as you're doing your job to keep your machine secure, you don't do silly things that will make your computer vulnerable, and if you stick with the pack and don't go out there daring people to break into your system, you'll most likely be fine. :D

---

