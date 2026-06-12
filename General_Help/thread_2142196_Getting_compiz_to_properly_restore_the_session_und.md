---
title: "Getting compiz to properly restore the session under 13.04"
date: 2013-05-04
forum: General Help
---

### Post by defaria on 2013-05-04
I recently upgraded to 13.04 and I want to use Compiz without Unity. I have updated my Nvidia G96 GeForce 9500 GT card driver to 313. I can play with it and configure things the way I like but when I log out and try to log back in I sometimes get that I'm operating in "low graphics" mode. Often I cannot move my mouse or use any keystroke to OK the dialog box to continue onward in low graphics mode and my only recourse is to power off and back on. Even Ctrl-Alt-F1 does not work. It's as if the keyboard is not working.

Other times I can use my keyboard and mouse and I OK the dialog box. My session starts up but gnome-panel and compiz are not running. Since I can Ctrl-Alt-F1 I do and log in through the console and start gnome-panel and compiz. Sometimes I also need to start emerald. My screenlets are not restarted so I have to do that by hand. I'm not in "low graphics mode" as far as I can tell. I get wobbly windows and all of the compiz effects that as far as I know only operate in higher graphics mode. I set up everything the way I like it and if I have to log out again I have to do all of this again.

Even if I don't get the low graphics mode warning dialog (this only started happening recently) compiz never starts correctly. I suffered through this problem for months while on 12.04. I used to put a fusion-icon into the gnome-panel and I could relatively easily get compiz running using that but now I can't even run fusion-icon - it just core dumps now.

I've put in startup apps to start both compiz and gnome-panel.

What is the best way to get a gnome/compiz login running so that I can smoothly logout and log back in and have my session restored. I know this should work because it works on my laptop (still on 12.04 for now) but never worked on my desktop. What info should I gather? What debugging can be done? Etc.

Now I can no longer run either fusion-icon nor ccsm! Both dump core!

Is there a way to reset all of compiz and start again?

Playing with ~/.config/compiz-1 stuff I managed to get ccsm to work again. But fusion-icon still dumps core.

Now when I logout/in I come up but gnome-panel does not start.

System settings seem really broken with things missing. For example, there is no Start Up Applicaitons. Other things appear to be missing like Additional Drivers. 

Finally many of the workspace switching functions don't work well. For example, I can more a window to another work space but it doesn't show up in the workspace switcher. Windows get lost. It all doesn't work very well.

---

### Post by defaria on 2013-05-31
Anybody?

---

