---
title: "Performance tweaks, hotkeys, and startup options"
date: 2008-03-19
forum: General Help
---

### Post by edinwood on 2008-03-19
Hey everyone, I've been spending most of my night tonight researching different ways of making my desktop very minimalist and streamlined for my needs, but I've run into a few problems. I'm still relatively new to Linux in general, so please keep this in mind when providing help.

First of all, are there any minor performance tweaks that you do with a fresh install that would make startup times slim down a bit? There's this pause when my box starts up where it's just a black screen, but after a few seconds it eventually returns to my desktop - I'm willing to bet that there's a way this can be either shortened or cut out entirely. Also, where would I go to edit my startup options - as far as which programs startup automatically. I'd like to get "Gnome-do" to start up as soon as I turn my computer on. How would I go about doing this? And one minor question that just seems to be bugging me - in Windows, whenever you'd hit 'backspace' in Firefox, it would send you back a page. I cannot for the life of me find the place to edit my hotkeys to change my 'backspace' from paging up to taking me back a page in Ubuntu.

Thanks for any help!
-Eric

---

### Post by danwood76 on 2008-03-19
Do you see the ubuntu splash screen at startup?
(It says ubuntu with an orange bar along the bottom) coz if you dont you get a blank screen instead.

If you go to Syste, -> Preferences -> Sessions you can turn off things you dont use and add the Gnome-do.
This will help you reduce startup time a little.

It would also be good if you could post a bootchart.
install bootchart by:
```

sudo apt-get install bootchart

```
then reboot and post the image contained in /var/log/bootchart/
this is a graphical chart of your bootup process and can help show if a process is taking a long time doing something, it will also show you the total boot time.
Most people have ubuntu boot in around 30 seconds.

---

### Post by der_joachim on 2008-03-19
Here's a few tips, quite random:
- If you have 1 GB+ of ram, install preload (sudo aptitude install preload). Your memory consumption will be higher, but a lot of commonly used libraries will be preloaded, thus reducing startup speed for your common apps. 
- Install the bum application. It's a nice graphical frontend to configure the services that start at boot time. A sudo aptitude install bum should do the trick.
- [http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/]("http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/") contains a few speed tweaks. Use at your own risk!

Hope this helps.

---

### Post by edinwood on 2008-03-19
Thanks for the help with the sessions manager and the bootchart. I'm going to give the preload a shot later, as well. With the bootchart, however, what am I looking for? A lot of that is foreign to me, haha

---

### Post by danwood76 on 2008-03-19
Your bootchart looks good, finishes in 20 seconds so above average.
Theres nothing hanging your boot up either so I wouldnt worry about this.

Do you get the splash screen when you boot?

---

### Post by edinwood on 2008-03-19
Yeah, I get the splash screen when I boot. So I guess I'm all set... unless you know how to edit the hotkeys for Firefox.

Thanks for the help!

---

### Post by danwood76 on 2008-03-19
Indeed I do.

Open a new tab/window and type the address 'about: config'
filter the key 'browser.backspace_action' change its value to 0 and restart firefox

---

### Post by edinwood on 2008-03-19
Thank you very much!

---

### Post by danwood76 on 2008-03-19
No problem!

Its easy when you know how ;)

---

