---
title: "not booting after AMD watermark removal"
date: 2013-07-03
forum: General Help
---

### Post by Kymus on 2013-07-03
After waiting a *while* to update my HTPC to Ubuntu 13.04 *just incase*, I got bit anyway. I got the "unsupported hardware" watermark that others have had.

So, I used the script mentioned [here]("http://ubuntuforums.org/showthread.php?t=2076381"), reboot, and yippie for me: Ubuntu isn't loading.

Upon boot, I get the usual message, then a blank Ubuntu-purple screen, then the screen basically goes black and it just hangs there.

I'm using an [AMD A8-3850 Llano]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103942")

Since the HTPC is my entertainment hub, I'm always really cautious about everything to try to keep it from going down. No such luck this time.

---

### Post by Kymus on 2013-07-04
bump.

---

### Post by Kymus on 2013-07-05
Bump.

---

### Post by Kymus on 2013-07-08
Bump.

---

### Post by su:bhatta on 2013-07-08
Have u tried the 'nomodeset' option from the purple screen...

---

### Post by Kymus on 2013-07-08
Hi Bhatta,

My purple screen is completely blank. I assume that GRUB isn't installed since Ubuntu is the only installation I'm using on this particular box.

---

### Post by su:bhatta on 2013-07-09
Really not my domain, but would you get the 'purple screen' if grub was not installed... 
i had a same kind of problem when i had installed Solaris on top of Windows8 and ElementaryOS...

Solaris cannot detect any other Linux OS...  eventually got rid of Solaris was left with a blank screen,plain black screen...
Only solution i found was to reinstall ElementaryOS again, as toyin with grub didn't do nothing..

---

### Post by CatKiller on 2013-07-09
GRUB is installed and running, even if you're only using Ubuntu.

You should be able to work out what the script did and undo it. The author of the script may even have given you an undo option.

---

### Post by Kymus on 2013-07-09
> **bhattabhishek said:**
> Really not my domain, but would you get the 'purple screen' if grub was not installed... 
i had a same kind of problem when i had installed Solaris on top of Windows8 and ElementaryOS...

Solaris cannot detect any other Linux OS...  eventually got rid of Solaris was left with a blank screen,plain black screen...
Only solution i found was to reinstall ElementaryOS again, as toyin with grub didn't do nothing..

Well, the blank purple screen has always been there. It's just that this time, after it's done with that and goes black, it just stays there. >_<

---

### Post by Kymus on 2013-07-09
> **CatKiller said:**
> GRUB is installed and running, even if you're only using Ubuntu.

You should be able to work out what the script did and undo it. The author of the script may even have given you an undo option.

Yeah, I assume that the work around (at least to get Ubuntu loading) is to boot in to Ubuntu (maybe using a cd) and then editing the changes manually. I just have no clue in hell how to do the latter.

I'll try contacting the author of the script though, thanks!

---

### Post by Kymus on 2013-08-05
Well, I contacted the script's creator 2+ weeks ago, and no response. This issue is still unresolved >_<

---

### Post by Kymus on 2013-08-11
bump

---

### Post by Kymus on 2013-08-14
Bump

---

### Post by Kymus on 2013-08-19
bump

---

### Post by QIII on 2013-08-19
Hello!

On my cell phone right now, so it would be a bit tough to help with details.

Just posting so I can review my posts and get back to this when I can.  Hopefully in 10 hours or so.

This can be sorted out.  Please hang tight.  I'll try to get back to you when I get home from work.

Cheers!

---

### Post by Kymus on 2013-08-19
Wonderful, thank you!

---

### Post by QIII on 2013-08-19
You can get to the GRUB menu by holding the SHIFT key as the computer boots up.  Once at the GRUB screen, do you know how to get to recovery mode?

---

### Post by Kymus on 2013-08-20
Hi QIII thanks for your response!

A bit of an oddity here. I held SHIFT at boot, and it did its usual thing (a dark purple screen followed by a solid black screen) and then I saw an Ubuntu splash screen come up, in the upper left hand corner was my username and computer name, then it - I assume - ran a few checks and then it just went to black and stayed there.

Repeated attempts have been unsuccessful in reproducing this. Now when I hold shift at boot, nothing happens (as in, I just get a blank purple screen and then a black screen and it sits there).

Probably not important in the least, but I noticed just now that the screen is not actually solid black, there is a blinking cursor (underscore) in the top left. On boot the resolution isn't perfect, so it cut off about half of it so I never noticed until now.

---

### Post by QIII on 2013-08-21
Does this also happen now if you *don't *hold the shift key down?

(I see that there is a time-zone consideration here...  I'll try to remember that!)

Does this machine dual boot or is Ubuntu all that is on it?

---

### Post by Kymus on 2013-08-21
Hi QIII,
 
Booting without holding shift produces the same results: purple screen, then s black screen with a blinking cursor.

My HTPC runs just Ubuntu; I have never had anything else on there.

---

### Post by QIII on 2013-08-21
Passing strange.  Did you do any updates after you updated the version?

If the very first thing you were getting after the BIOS/EFI splash were a black screen with a blinking cursor, I'd say there was a problem with your MBR.   Hmmm.

Just to eliminate the obvious, can you double check all of your drive cables and run an fsck on your drive from a LiveCD?

---

### Post by Kymus on 2013-08-21
Well, after POST, I get a purple screen, which tells me that Ubuntu is starting to load (or at least doing *something*.. From what I recall - as it has been over a month now since I've been unable to get in to Ubuntu - usually it would POST, go to a blank purple screen, got to a black screen for a few seconds, and then Ubuntu would load).

The only update I did was to Ubuntu 13.04 (and of course whatever packages were updated along with it). It was right after I used the script to remove AMD's watermark that this problem started. 

Tomorrow (11pm here) I'll run a fsk.

---

### Post by QIII on 2013-08-21
I just looked over that script again, and I don't see anything that would have caused it to run amok and turn your Ubuntu into Fedora or something.  ;)

However, I'm not going to take the time to review it to see what it is actually replacing.

Go ahead and do the cable check and fsck as a "rule out".  I don't think that's the problem, but diagnosis sometimes requires ruling things out for sure.

My guess is that the script is either malformed or not intended for the driver you actually had installed.

---

### Post by Yellow Pasque on 2013-08-22
It edits a string in fglrx_drv.so, and I've seen it bork a few systems. I'm not sure of the best fix if you can't boot in safe graphics mode. Maybe you can run a LiveCD, mount your filesystem and blacklist fglrx.

---

### Post by Kymus on 2013-08-22
> **Temüjin said:**
> It edits a string in fglrx_drv.so, and I've seen it bork a few systems. I'm not sure of the best fix if you can't boot in safe graphics mode. Maybe you can run a LiveCD, mount your filesystem and blacklist fglrx.

yeah, I kinda figured that the solution may be to boot with a live disk and then manually undo the changes. Of course, I obviously have no idea how that's done (:P) but considering I can't access a terminal on boot or the recovery module, I can only assume that this is quite possibly the *only* solution :\

---

