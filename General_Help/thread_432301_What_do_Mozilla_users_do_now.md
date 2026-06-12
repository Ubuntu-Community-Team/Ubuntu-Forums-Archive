---
title: "What do Mozilla users do now?"
date: 2007-05-03
forum: General Help
---

### Post by picpak on 2007-05-03
My sister just phoned me telling me that her upgrade to 7.04 uninstalled the Mozilla browser (not Firefox; just Mozilla). I checked Synaptic, and sure enough: Mozilla isn't there. Fair enough...but why couldn't it get replaced with Seamonkey? There doesn't seem to be a .deb for it anywhere. My sister doesn't like Firefox and can't get Seamonkey installed, so now she's left out in the cold.

Is there anything we can do? Why couldn't Seamonkey be packaged and have Mozilla replace itself with it when you install it?

---

### Post by CocoAUS on 2007-05-03
It's been stated officially that Mozilla has been removed from Feisty.  What options do you have?

Well, there's always Epiphany (epiphany-browser).  I tried it after I got fed up with Firefox, and I haven't looked back since.  You could also compile it yourself, or search online for a .deb file.

---

### Post by aysiu on 2007-05-03
You could install Seamonkey from Mozilla instead of through the repositories:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

---

### Post by digital_k on 2007-05-03
Another vote for Epiphany as well!  Its tons faster than Firefox, loading and rendering. It also has an available extensions add on that allows you to block ads, use mouse gestures, etc. It doesn't have as many as Firefox, but it it has enough for me. I like the browser alot, its very solid. :)

---

### Post by aysiu on 2007-05-03
I don't see how Epiphany is a substitute for Mozilla. Mozilla is an email client and web browser combined. Epiphany and Firefox are just web browsers.

Seamonkey is the proper replacement for Mozilla.

---

### Post by CocoAUS on 2007-05-03
Epiphany doesn't have to be a "replacement" for it to be a great alternative.  There are other e-mail clients out there (read: Evolution) that do a fine job.  Having a browser and e-mail combined, as you say, means little other than the two are packaged together.  Epiphany+Evolution, or Epiphany+Thunderbird even would do just fine.

---

### Post by picpak on 2007-05-05
> **aysiu said:**
> You could install Seamonkey from Mozilla instead of through the repositories:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

That didn't work for her. She told me it said it couldn't stat the file (?) and when she went to run it, it said there was no such command.

She likes Epiphany less than Firefox, for obvious reasons that aysiu said.

---

### Post by aysiu on 2007-05-05
> **picpak said:**
> That didn't work for her. She told me it said it couldn't stat the file (?) and when she went to run it, it said there was no such command. Sounds as if she was retyping the commands instead of copying and pasting them.

If she copied and pasted them, could you post the terminal output here? If something is truly wrong with the HowTo (and it's not just user error), I'd like to fix it.

---

### Post by picpak on 2007-05-05
Her computer's an hour and a half away, so you'll have to wait...

---

### Post by Ph0B1uS on 2007-05-05
> **picpak said:**
> Her computer's an hour and a half away, so you'll have to wait...

Sounds like an ssh-server would be nice to install on her computer and use it to help her remotely.
Just a thought.

---

### Post by picpak on 2007-05-05
I've found the problem!

Simply running *gksudo seamonkey-installer* doesn't actually run the installer.

You have to run:

```
gksudo ./seamonkey-installer
``` 

*gksudo seamonkey-installer* simply just hangs. I've edited the wiki with this fix.

---

### Post by aysiu on 2007-05-05
Thanks for fixing that!

---

### Post by picpak on 2007-05-05
You're welcome. That would also explain why she complained that no questions popped up after running that. I just assumed she made a typo.

---

### Post by picpak on 2007-05-09
Just letting you guys know that after a quick email to getdeb.net, they have packaged Seamonkey as a .deb, in the form of [Iceape](http://www.getdeb.net/app.php?name=Iceape).

---

