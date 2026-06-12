---
title: "Dell D400 using Ub 9.04 as o/s question"
date: 2017-03-07
forum: General Help
---

### Post by ra7411 on 2017-03-07
I messed with an old laptop I had laying around to see if I could get it to a usable state.
The highest Ub version I could get installed was Ub 9.04 - later ones wouldn't go.
The main problems I've run into are that I can't find any chrome that will install, and the Firefox that comes w/ it has the update option grayed out apparently as a no go.

Youtube on the Firefox v 3.0.8 won't come up - the vids are just black screen.

Any ideas on how to make the thing useful, or should I just toss it?

CPU:  Intel Pentium M Processor 1.40GHz (1MB cache)
500 MiB ram

Thanks

---

### Post by Tadaen_Sylvermane on 2017-03-07
I'm assuming the problem is gui related. Try ubuntu server and add openbox to it. Might work. No sense trying to use a release that old. Won't find help or software.

---

### Post by oldrocker99 on 2017-03-07
Ubuntu 9.04 has no support at all. Are you sure you can't install 14.04 or later? What do you mean, "they wouldn't go"?

---

### Post by ra7411 on 2017-03-07
> **oldrocker99 said:**
> Ubuntu 9.04 has no support at all. Are you sure you can't install 14.04 or later? What do you mean, "they wouldn't go"?

Ub 16 and 14 gave messages to the effect "not bootable".
Ub 10.04 install went black screen for over 30 mins. 
Ub 9.04 went in fine.

---

### Post by oldos2er on 2017-03-07
For such a low spec machine you should try [Lubuntu]("http://lubuntu.net/").

---

### Post by mörgæs on 2017-03-08
If you have 1 MB of L2 cache you have a Pentium M of the first generation which demands a special treatment in order to overcome the [PAE]("https://help.ubuntu.com/community/PAE") problem.

Begin with the minimal Ubuntu 16.04.2 ISO.

---

### Post by amanchesterman on 2017-03-08
I have a Dell D420 notebook which currently runs happily with Lubuntu 16.10 installed; previously I had Xubuntu 14.10 on it and that had no problems either. I keep it as a backup machine because the screen is small but it's perfectly usable and I've taken it with me when travelling. Personally I prefer the lighter distros because the desktop is more familiar to an oldie like myself but I guess they help to get the best out of the hardware as well.

---

### Post by ra7411 on 2017-03-08
I gave lubuntu-16.10 i386  a try, it failed due to no pae. I tried forcepae--forcepae method a few times w/ no success.
The machine remains a brick - no big loss.

---

### Post by mörgæs on 2017-03-09
It's not a brick if you get a picture on the screen which you obviously do. 

Did you use the minimal ISO?

Did you enter the command exactly as posted in the wiki, that is with two spaces like in ```
forcepae -- forcepae
```?

---

