---
title: "Problem with video playback (Xine)"
date: 2008-01-27
forum: General Help
---

### Post by xenomorph99 on 2008-01-27
Hi,

Last year, I was having trouble playing videos after running Wine; I just got horizontal coloured lines where the video should have been in the player window but got sound.

I read on someone's blog that they'd found that reverting back to an older nvidia driver cured the problem so I did 'sudo apt-get install nvidia-glx' which appeared to cure the problem.

Recently, I've noticed that Kaffiene/Mplayer won't play video - they report things like "loading of player part 'XinePart' failed' (all video drivers failed to initialise). If I run totem, I get a 'no video output is available' errors.

However, I can run VLC OK - it plays DVDs and most other movie formats ok.

I tried to purge anything I had installed that was associated with Xine in Adept (which had the interesting result of removing things beginning with a, including adept(!), which I stopped before it purged everything) to reinstall. After reinstalling adept, I then tried to reinstall the old "new" Nvidia driver 'sudo apt-get install nvidia-glx-new' to see if Xine startedto work again. 

It didn't

So, did Xine get broken recently? Any ideas on how to fix this?

Ta,
K

---

### Post by empthollow on 2008-01-27
I had this same problem,  for me i would reboot and it work for a few minutes but then would crap out again.  i didn't have a problem with mplayer though.  The fix for me was to change the video out device.  I use opengl.  You can use system -> preferences -> multimedia systems selector to change it for totem (x11 no xv worked for me there).  in xine you can chane it by going to right click menu on xine window -> settings -> video tab.  The players were working fine for me for a long time and then one day i got the weird bad lines again.  I assume it's a bug in something that was updated but i don't know what.  Let me know if you find out where the bug is.

---

### Post by xenomorph99 on 2008-01-27
Hi,

I should say that I normally use Kubuntu but have Gnome installed for when things go wrong as it seem the only way to sort things out is via Gnome.

I don't have a system->preferences->multimedia option. if I go into preferred applications then choose the multimedia tab, however, it seems there is an option for totem (it was set to rhythmbox) which I have selected. I still get the same error messages as before, though, when trying to play movies.

The horizontal lines I can sort of live with - I'm more interested in knowing why Xine isn't working.

Incidentally, if I try to run Xine from the command line, I get a splash screen for about a second then it dies with 'This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.' 

which is really helpful.

Ta,
K

---

### Post by xenomorph99 on 2008-02-02
Oh looky - it's something to do with video and no one knows what the answer is.

Time to switch flavours of Linux, methinks. In a vain attempt of finding one that works.

---

