---
title: "Gutsy Gnome Splash Screen"
date: 2007-10-28
forum: General Help
---

### Post by hebetude on 2007-10-28
Gutsy has a problem with splash screens and I've read through ubuteen posts about this with no real resolution or the threads get sidetracked.  I'm not sure why this became the default option, especially when gnome was soooo buggy in Beta and would take 10-15mins to load (without any user notice as to why).

Anyways, I've installed gnome-splashscreen-manager

sudo apt-get install gnome-splashscreen-manager
I then "installed" a splashscreen, something from a theme I found.  Now, when I boot up it logins...loads splashscreen... then loads the wallpaper OVER the splashscreen.  Do I need to build a good version of gnome from source or something?  

I like compiz and all, but ever since dealing with the packaged version of Gnome for Gutsy I get a sinking feeling in my chest everytime I need to reboot (not that I ever do :) ).  Is the Ubuntu version of Gnome just very much hacked up?  What's the deal here?

---

### Post by mikewhatever on 2007-10-28
Are you still using a beta version of Gutsy? It is supposed to be buggy, that's what betas are for. Ubuntu Gnome works great, no deals.

---

### Post by hebetude on 2007-10-28
I'm all up to date, of course I didnt have any new files to download on the day of release much to my disappointment!  I haven't seen any new changes to gnome since about a week before release

---

### Post by mikewhatever on 2007-10-28
Does it still loads slowly, or what's the problem?

---

### Post by hebetude on 2007-10-28
The problem is that I can't see my splash screen loading apps.  It pops up but the wallpaper loads over it, so I can't see my splash screen.  I want the wallpaper to load in the back like wallpapers do, and the splash screen to sit on top while different apps load.  

The boot situation may or may not be fixed, I manually turned off a bunch of startup services in Gutsy until it loaded fast.

---

### Post by hebetude on 2007-10-28
You can see those changes here: [http://ubuntuforums.org/showthread.php?t=568995](http://ubuntuforums.org/showthread.php?t=568995)

---

### Post by mikewhatever on 2007-10-30
When I boot my Ubuntu, fist the splash screen appears, then it disappears and appears the login window. After I login, that window disappears too and the desktop appears. Nothing loads ever anything etc. It looks like your gnome is kind of hacked.

---

### Post by Braedley on 2007-10-30
All of a sudden within the past couple of days, gnome and compiz would take some 15 to 20 seconds to even draw my background and desktop.  I also noticed that whenever I tried to restart X (Ctrl-Alt-Backspace), nothing would start up.  I tried setting visual effects to none (ie not use compiz), but still no go.  I also read the other thread mentioned, but I, like a number of those people, don't have a file named session (hidden or otherwise) in ~/.gnome2.  I'm going to try disabling some more thing in System->Preferences->Sessions, but I'm not hopeful.

---

