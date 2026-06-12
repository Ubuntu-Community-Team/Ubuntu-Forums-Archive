---
title: "Fspot - edit and fullscreen show blank image"
date: 2008-02-12
forum: General Help
---

### Post by tj111 on 2008-02-12
I'm having some issues with F-Spot photo manager.  When browsing photo's, it correctly shows my thumbnails of all the images ([screenshot](http://i30.tinypic.com/kd8vsx.png)).  However when using the Edit or Fullscreen views, it shows a blank image icon, and no image is displayed([screenshot](http://i28.tinypic.com/2qjlqpz.png)).  Also, when trying to right-click and select open with, it only tells me "No applications available".  I did some googling and messed with the settings, but can't seem to get it to work right.  Just wondering if anyone knows a fix for this.

---

### Post by ajgreeny on 2008-02-12
I have a similsr problem.  The edit works OK and I get a window with the photo showing OK, but if I go to Fullscreen, nothing at all shows except the taskbar button, and if I right click on that and chose Maximise, the fullscreen display appears.  It makes the program less than useful.  But I prefer digikam anyway, even though I'm on gnome, so it doesn't worry me too much. By the way, the slide show works perfectly as my screensaver, but not from the program, where nothing much happens.

---

### Post by tj111 on 2008-02-13
Well I used F-Spot for a while and really liked it.  Tried digikam but didn't think the interface was as intuitive.  I was hoping someone would have some fix for this.  Otherwise I guess I'll have to dig around in the repos and find another program I like.

---

### Post by ajgreeny on 2008-02-13
Rather stupidly I didn't think to look before my last post here at the effect compiz might be having on this problem; I don't know why as I'm always telling others to try with compiz turned of  if there are strange things happening with display of many and various things.

So today I tried f-spot with and then without compiz running and that seems to be the reason for the problem, in my case at least.  Give it a try, it may help you as well.  If you want a quick way to turn compiz on and off get a copy of forlong's compiz-switch here:-
[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

---

### Post by tj111 on 2008-02-13
Hmm, it could be compiz that is causing the problem, I'll have to test it when I get home.  But saying as I use Avant as my only window manager disabling compiz to view photos seems like more loss than gain.  That script, though, will be excellent when launching programs that use full screen OpenGL.  I'll tinker with the Compiz settings, see if a certain one is interfering with F-Spot.  If I can't fix it, I guess I'm off to the repositories to find a new program.  I'll let you know what I come up with.

---

### Post by tj111 on 2008-02-13
It appears there is a known bug between Compiz and F-Spot, but it doesn't match my problem description.  I tried the fix for it anyway, disabling 'legacy fullscreen fix' in compiz settings, but i'm still having the problems.

---

### Post by tj111 on 2008-02-13
So I'm an idiot.  Turns out the problem was that I moved my photos toa  different drive.  I changed the photo location in the Preferences so I figured it updated automatically, turns out it didn't.  I had to delete all the photos from my catalog and re-import them.  So, yeah, idiot.

---

