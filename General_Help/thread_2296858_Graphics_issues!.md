---
title: "Graphics issues!"
date: 2015-09-29
forum: General Help
---

### Post by john464 on 2015-09-29
Hello!

I just recently upgraded to ubuntu 15.04. I am an avid gamer, and tend to spend time on games like Minecraft, Skyrim, and Kerbal Space Program. After fully upgrading and installing the latest intel drivers for Ubuntu, I found that my games run terribly. After thinking on this for a while, I remembered that I had installed some sort of major graphics update on my installation that caused my games to run at nearly 3x the FPS. I've searched everywhere for it but I cannot seem to find it. Here are my issues:

Full flickering with Minecraft. It only flickers when I move.

KSP Space Center is completely invisible, leaving only the roads semi able to be seen. I found that it was edge highlighting, which restored the graphics, but it is still at an extremely low framerate.

Skyrim is completely unplayable. 

I've found that even simple tasks like opening new windows and playing movies won't even work. Is there any other graphics update/upgrade/alternative that I'm not finding on my own? I've searched for nearly 3 hours now, and will continue to do so, but do you have any suggestions?

I have an Asus Vivobook s550CA.

---

### Post by tristan16 on 2015-09-29
I looked up the specs for your computer. I'm not an expert, but your Intel Graphics should be able to handle simple desktop animations. Hopefully someone with more experience can find an answer. In the meantime, here's my first suggestion:

Try a different desktop environment (DE). Since you're on Ubuntu, you have Unity. Try starting with Xfce and see if it helps. Just install "xubuntu-desktop" from the Software Center and log out to change your DE. This article gives a good explanation, but it's a little outdated: [http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/)

You don't have to use Xfce just because I suggested it. You can install all kinds of different desktop environments. Just find the ones that work and pick the one you like.

---

### Post by john464 on 2015-09-29
I figured it out! It took me a while but I finally

> sudo apt-get install xserver-xorg-lts-utopic libegl1-mesa-drivers-lts-utopic xserver-xorg-video-all-lts-utopic xserver-xorg-input-all-lts-utopic

It turns out I just needed to grab the utopic graphics stack! Thanks for the suggestions though.

---

### Post by tristan16 on 2015-09-29
> **john464 said:**
> I figured it out! It took me a while but I finally



It turns out I just needed to grab the utopic graphics stack! Thanks for the suggestions though.

Very interesting solution.  Glad you got it working! Don't forget to mark the thread as solved in the thread options. ;)

---

