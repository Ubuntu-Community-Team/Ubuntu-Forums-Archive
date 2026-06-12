---
title: "urgently need help with unique situation"
date: 2008-05-07
forum: General Help
---

### Post by crs501 on 2008-05-07
Background:  I just recently upgraded from Ubuntu 7.10 to 8.04. I had originally tried to upgrade from the network via the Update Manager like all of us were invited to do. I thought it was going to go smoothly and then for no apparent reason --- and literally one minute away from being finished with the install --- the computer froze. I tried all I knew to do but eventually I had no option but to shut down my computer knowing full well the installation was incomplete and I was probably very screwed!  I eventually managed to get online thru the GNOME option on my log-in screen, downloaded 8.04 and finally installed it successfully on 4/25/08. All was good, it worked very well and I was lovin' it until yesterday 5/06/08. I returned home from business and my wife told me about a problem she had while simply surfing and checking e-mail. She said the computer froze and she was unable to do anything. She shut the computer down, and when she turned it back on she discovered she was unable to boot back up. I don't know the full story as I wasn't here to see it all. What I saw when I tried to boot the computer was basically:

       BUG: Soft Lockup-CPU#1 stuck for 11s! (hald-probe-vide:5775)
 
There were numbers preceding that line that looked like this:

       [ 72.883132 ] and each line had progressively higher numbers in the first two digit positions. 

I have tried numerous times to re-install Hardy Heron 8.04 with the install disc I burned, but with no luck --- The yellow bar on the black Ubuntu screen just gets so far and stops, not proceeding to the install process.

I have also downloaded Gutsy Gibbon 7.10. So my question is:
Under the circumstances, can I re-install 7.10 and then attempt the upgrade to 8.04 via the Update Manager without harming my computer? 
Any advice would be helpful at this point, but I need it pretty quickly!!!  We're simple users so answers have to be relatively simple as well.  I'd appreciate any help here!  Thanks.  


PS: Those offering serious help can e-mail me at [email]crs501@hotmail.com[/email] ---- I do presently have limited ability to check e-mail. However I'm not certain that I'll be able to get any online ability back tomorrow if I turn this thing off tonight. ya dig?  I'll keep checking the "Pidgin" just in case.

---

### Post by sdennie on 2008-05-07
Does it work if you try booting with "maxcpus=1"?  To do this, when the computer starts, hit Esc when the screen says something about "grub" (It will be basically the first thing that comes on the screen).  You'll get a menu.  Hit "e" and you'll get another menu.  Go down one line in the menu and hit "e" again.  At the end of that long line, add " maxcpus=1".  Hit enter and then "b".  The system should start now.

That may or may not work but, if it does, it could help in getting to the point to diagnose the real problem and find a fix for it.

---

### Post by crs501 on 2008-05-07
Thanks "vor" for the response. I don't know, that's not something I knew how to do til you suggested it. I will try it although that may not happen til tomorrow as I am gathering all the feedback I can while this is still on tonight. Whatever the result, I will report it back here. Again, thank you for a response!

---

### Post by ghost_ryder35 on 2008-05-07
what are your specs?
hardware? cpu, ram
o/s ? 64bit or 32bit
if your running 64bit you can try booting with 
```

=noacpi

```
refer to [http://ubuntuforums.org/showthread.php?t=398948](http://ubuntuforums.org/showthread.php?t=398948) for help on adding this to grub

---

### Post by crs501 on 2008-05-09
I have successfully "Down-graded" to Gutsy Gibbon 7.10. I have tried upgrading to Hardy Heron 8.04 numerous times and have nothing but problems. At least one responder to my posts on these forums suggested I might have a CPU or Hardware problem. Yet, each time I went back to Gutsy 7.10 everything works fine and I cease having the problems I encountered on 8.04. Seems to me if there were hardware issues, they would appear no matter what I was running. PLUS: a lengthy scan of posts all over these forums reveal numerous people experiencing major issues with both 8.04 and the new Firefox similar to mine. I'm feeling lucky to have safely returned to a smooth-running Gutsy 7.10, and since I realize support for Gutsy is inevitably limited, I am contemplating scraping together the money to return to good old vulnerable XP SP2. After the past 6-7 months I've enjoyed the differences Ubuntu has to offer, but the problems I've dealt with make battling viruses and spyware on XP look like a walk in the park on a sunny day! Sorry guys, gotta be honest!!!

---

