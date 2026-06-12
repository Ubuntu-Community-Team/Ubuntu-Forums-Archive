---
title: "General PRoblems I can't Fix"
date: 2006-12-13
forum: General Help
---

### Post by demonbro on 2006-12-13
I recently switched to Ubuntu Edgy from Windows XP, and i love it.  Im useing the Edgy distro desktop 64-bit version.  I have fixed numerous issues except for these, I would love some help.

1.  I get this random beeping sound.  The system runs fine but it just continous to make this annoying beeping sound.(Not in response to anything!)

2. Cannot get the flash plugin to work!  Have tried numerous tutorials and all the described methods, still no dice (Easy ubuntu wouldn't work, so i DO have automatix installed)

3. Cannot burn cds.  I have read about the issue with this on the forumns, but there has to be a fix!  Doesnt matter which program i try to use eithier!

4. Is there a way to network a Ubuntu desktop and a windows xp desktop? So you can transfer files back and forth?  Just curious on this one, not too important!

Any help would be greatly appreciated!!!

erik;)

---

### Post by igknighted on 2006-12-13
> **demonbro said:**
> I recently switched to Ubuntu Edgy from Windows XP, and i love it.  Im useing the Edgy distro desktop 64-bit version.  I have fixed numerous issues except for these, I would love some help.

1.  I get this random beeping sound.  The system runs fine but it just continous to make this annoying beeping sound.(Not in response to anything!)

2. Cannot get the flash plugin to work!  Have tried numerous tutorials and all the described methods, still no dice (Easy ubuntu wouldn't work, so i DO have automatix installed)

3. Cannot burn cds.  I have read about the issue with this on the forumns, but there has to be a fix!  Doesnt matter which program i try to use eithier!

4. Is there a way to network a Ubuntu desktop and a windows xp desktop? So you can transfer files back and forth?  Just curious on this one, not too important!

Any help would be greatly appreciated!!!

erik;)

1) sounds like something is going on in the background, not sure what would cause that though.

2) Ok, are you using AMD64bit or standard x86 Ubuntu?  If you have x86, then download the flash file from the labs.adobe.com (thats flash nine update beta for linux).  Extract it, and then it will tell you a folder to paste it in.  You will need root privleges, but once you paste it there it should work fine (for firefox... other browers need it pasted in their /plugins folder).  For AMD64 it is more complex, im not entirely sure how to do it.

3) Have you tried k3b?  I have never had an issue with it.  Also, what burner are you using?  I wonder if it is not supported hardware, there should be a section on the ubuntu wiki to check.

4) Yup, search fo instructions on Samba... it is /very/ easy from what I hear, but I don't really do anything with windows so I can't tell you for sure.

---

### Post by MadTxn on 2007-01-19
> **demonbro said:**
> ...I get this random beeping sound.  The system runs fine but it just continous to make this annoying beeping sound.(Not in response to anything!)...

I'm also getting a random beeping.  (Running Edgy on an HP dv8000).  About every couple of minutes the laptop beeps 10 times (I have my headphones on), then there is a faint clicking for 25 seconds.  I closed all of my visible programs (i.e. ones with windows) and it still happens.  Any ideas as to what I can look for?  Like is there a way to tell what program is using the sound card at any given time?  Thanks in advance.:confused:

---

### Post by Johnsie on 2007-01-19
Your laptop might be overheating... Make sure the vents aren't blocked by anything.

Maybe you could try chnaging your power manager:

> sudo apt-get install powersaved

That helped on my HP laptop. I also found that Dapper appears to work a wee bit better on it than Edgy does.

---

### Post by MadTxn on 2007-01-19
Laptop is cool as a cucumber.  Well, a cucumber with a dual-core processor...  And the sound is quiet enough that i can only hear it with headphones plugged in.

---

### Post by Johnsie on 2007-01-19
Try the powesaved thing... it might help. If it doesn't then just do 

> sudo apt-get install powernowd

and that will put it back to the old settings.

---

### Post by Mithrilhall on 2007-01-19
Networking with Windows....try installing Smb4k.

Can't burn a CD...what kind of errors are you getting.

Flash doesn't work...what tutorials have you tried (provide links).

---

### Post by Johnsie on 2007-01-19
Firefox 2 automatically installs the Flash pugin on demand now. It did it for me yesterday.

---

### Post by blackened on 2007-01-19
For your cd burning problem:
try starting the program with sudo from the terminal a la *sudo gnomebaker*.
If it properly burns that way, then you could have some permissions jacked up (likely not your fault). This happened to me under Breezy, but was resolved when I upgraded to Dapper.

---

