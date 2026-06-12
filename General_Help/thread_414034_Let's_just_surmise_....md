---
title: "Let's just surmise ..."
date: 2007-04-19
forum: General Help
---

### Post by erugalatha on 2007-04-19
... just say a guy/gal was fed up putting in their password into ubuntu every f**ts-end ... how would that guy/gal set things up so it only needs entering at login and then not have to enter it again?  I'm the only one using the machine and I'm lazy. :)

---

### Post by Matthew Bartram on 2007-04-19
The multiple password-typing-in is only when you want to do an administrative task, and is for security purposes.
The only way I know of to get around that (aside from not doing administrative things!) is to log in as root. But I wouldn't recommend it.

---

### Post by eentonig on 2007-04-19
Let's say that guy is lazy and probably is going to have the honor of being the first to blame Linux for having virusses and/or breaking.

There is a reason for entering your password whenever you want to change system settings.

---

### Post by erugalatha on 2007-04-19
I thought so ... I will have to become un-lazy. :) thanks for reply.

---

### Post by Matthew Bartram on 2007-04-19
No problem :-)

---

### Post by eentonig on 2007-04-19
No problem. My comment might have sounded harsh in retrospect. But it certainly was ment to be.

There's been a lot of thought going in the setup of this mechanism.

---

### Post by pepsi_max2k on 2007-04-19
I'm tired of that in linux too. Only solution seems to be using root as your normal login. Either enter the user settings page and change root to your default user login, or just log out and log in again with username root and the password you set when installing. You'll lose all the security it provides so you'll wanna make sure your firewall's running and possibly have anti-virus installed, but i can't see how it'll be much worse than windows. xp that is, vista is just as bad password wise :(

---

### Post by eentonig on 2007-04-19
I really don't see bother in typing my password.

After the initial week after installing, where I do a lot of tuning and customization, I think I need to type the sudo password maybe.... once a week?

---

### Post by erugalatha on 2007-04-19
harsh is often good for lazy people like me!  

My thoughts on it were that I wondered if there is a way that a user can have the choice to take their chances and forget about security and passwords sometimes.  I also thought it would be useful if I were setting up a machine for a novice user I could set it up so after they log in as their user it allows them to do things but if they try doing any admin type stuff it just tells them "You are not allowed to do that" instead of asking for a password.

---

### Post by eentonig on 2007-04-19
The latter part is easy. Only the install user gets sudo rights by default. So you just have to create the actual user account after you installed the box. 

Btw, there are ways to circumvent the sudo annoyance. You could enable the root account. Or create a script to launch during boot which starts a root-shell. But I'm not going to explain neither of them, as I don't support the idea. :mrgreen:

---

### Post by cmost on 2007-04-19
> **pepsi_max2k said:**
> I'm tired of that in linux too. Only solution seems to be using root as your normal login. Either enter the user settings page and change root to your default user login, or just log out and log in again with username root and the password you set when installing. You'll lose all the security it provides so you'll wanna make sure your firewall's running and possibly have anti-virus installed, but i can't see how it'll be much worse than windows. xp that is, vista is just as bad password wise :(

Are you kidding?  Have we become so lazy as a society that we can no longer be bothered with such basic things at typing a simple password?  Come on people!  This is to ensure YOUR safety and security.  Nobody wants Ubuntu to become overrun with viruses and/or spyware when enough people decide to use the root account as their everyday account.  Since Ubuntu is the leading Linux distribution, and since there have been a rise in individuals (and businesses) switching over to Linux it's only a matter of time before the malware authors start attacking us too.  If you're going to avoid security and circumvent measures intended to protect your data and your computer then you might as well just run Windows and forget about Linux altogether.  I wonder about people.

---

### Post by rbmorse on 2007-04-19
I bought a keyboard wih an internal macro facility and put my password there. Anytime something wants a password I just have to hit a certain key...

---

### Post by erugalatha on 2007-04-20
OK, you've convinced me that password typing is a good thing ... I got away from Windoze on my personal laptop because of spyware etc. and don't ever want to go back. Unfortunately I still have to use Windows in work. :(

I must try get myself one of those keyboards - it sounds like an ideal solution.  Where would I purchase one?

---

### Post by rbmorse on 2007-04-20
The usual places, I imagine.  Mine is a reproduction of the ancient Northgate OmniKey 102+ sold by Creative Vision Technologies.  I bought the keyboard (which is not cheap) because it uses clicky buckling spring mechanical keyswitches just like the original IBM PC and AT keyboards. It is as god (small g -- my god isn't very ambitious) intended. I am simply not comfortable with any of the newer keyboards using membrane switches. The macro thing was sort of a bonus.

One thing to avoid...a lot of "macro" keyboards actually use a windows program to store and execute macros.  Not a good idea for a Linux computer.  You're looking for one with on onboard CMOS for storing macros and a faclity to program it. 

The CVT comes with a Windows' based utility for programming the keys, but it is not necessary.

I have not looked but there must be a Linux keyboard macro generator/controller. This would load at startup and should work with any keyboard.  Might be worth looking for.

---

