---
title: "Firefox Browser History"
date: 2008-06-26
forum: General Help
---

### Post by GabrielWolff on 2008-06-26
I'm using my browser together with my brother, whom I don't want to know about all the sites I visit. 

However, I want to have my own browser history saved. 

Is there any way of creating a browser history list that is NOT affected by deleting parts of the "regular" browser history?

---

### Post by DJ_Peng on 2008-06-26
The only way to do this would be by setting up a different [Firefox profile]("http://kb.mozillazine.org/Profile_Manager") for your brother. You could set up a launcher for him to use that specifies his profile (instructions are on the page I linked to) and make another location tucked out of the way so you'll know where it is to use it but your brother won't, helping make sure he doesn't use your profile by mistake.

---

### Post by GabrielWolff on 2008-06-26
> **DJ_Peng said:**
> The only way to do this would be by setting up a different [Firefox profile]("http://kb.mozillazine.org/Profile_Manager") for your brother. You could set up a launcher for him to use that specifies his profile (instructions are on the page I linked to) and make another location tucked out of the way so you'll know where it is to use it but your brother won't, helping make sure he doesn't use your profile by mistake.

Yeah, you don't know my brother...

Any way I can do that *without *him having the strong urge to go through all my files and look for that darn pass to my user? And I don't really wanna confront him with this. Any way I can do this *silently*?

---

### Post by niyonk on 2008-06-26
I was just about to tell you to visit the link

But...take a look at the shortcut part. Make a shortcut somewhere he wont know...then in properties(just read the part) :)
The shortcut allows you to be the one to choose what profile you want to load. This is your only option (til'  your brother finds out the trick, lol)
And make sure you also change the folder (where config files and extensions are stored)
and do not delete the default one lol (it's his :biggrin:)

If you know what i mean :D

---

### Post by DJ_Peng on 2008-06-27
> **GabrielWolff said:**
> Yeah, you don't know my brother...

Any way I can do that *without *him having the strong urge to go through all my files and look for that darn pass to my user? And I don't really wanna confront him with this. Any way I can do this *silently*?
lol I may know him better than you think. ;) You could actually hide the launcher for your profile in a really obscure place and then just drill down to it in Nautilus. To my knowledge there's no app history for him to check. Don't know of a better way though. Hopefully someone will chime in with a sure fire solution for you. (I won't say idiot proof because the moment someone makes something idiot proof someone else will just come along and invent a better idiot. :D)

---

### Post by lukjad on 2008-06-27
Just a thought, why not create a new user account on the PC? All you need do then is surf to your heart's content. Also if you are afraid he will start poking around, encript your section.

Cheers

---

### Post by GabrielWolff on 2008-06-27
Yeah, but still I know one thing for sure: if the solution will be anything he'll be aware of - it'll fail. The guy is a darn pain in the *** when it's about not wanting him all over the place, so the minute I'll openly do something like that - he'll put weeks of effort into breaking it. 

Wait - should I maybe just move out?! :)

... 

Any other ideas?

---

### Post by crossedout on 2008-06-27
Wow, your brother must be a real nosey somebody :).

If you want to get extreme, you could install truecrypt, create an encrypted container and store your profile inside the container.  Each time you wanted to use FF though you would have to mount and decrypt the container then run FF.  The upside is, he would never get in unless you left the container available when you step away.

-Xout

---

### Post by GabrielWolff on 2008-06-27
> **crossedout said:**
> Wow, your brother must be a real nosey somebody :).
You got NO CLUE!!!

Yeah, I think that should work for me, thx :)

---

### Post by Archmage on 2008-06-27
IMHO you can set a password for your profile or password.

---

### Post by lukjad on 2008-06-28
> **GabrielWolff said:**
> Yeah, but still I know one thing for sure: if the solution will be anything he'll be aware of - it'll fail. The guy is a darn pain in the *** when it's about not wanting him all over the place, so the minute I'll openly do something like that - he'll put weeks of effort into breaking it. 

Wait - should I maybe just move out?! :)

... 

Any other ideas?

If this is your PC you should do a few things. 
[INDENT][/INDENT]1) Create a BIOS password.
Then

[INDENT][/INDENT]A) Disable the computer form booting from a CD.
or

[INDENT][/INDENT]B) Create a boot password. (this may be too obvious though.)

The idea is this: If he does find out that you are hiding something from him he won't be able to boot into a SLAX (or other live) CD and hack away at your system until he gets through all the encryption or guesses your password. 
If you don't want him using your PC at all the boot password will keep him off your PC, unless he rips out your hard drive and plops it into another PC. If this is even a slight possibility encrypt your drive. In this case Nbuntu might be worth a look at. Then again, maybe not.

---

