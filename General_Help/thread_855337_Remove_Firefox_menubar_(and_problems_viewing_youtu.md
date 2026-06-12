---
title: "Remove Firefox menubar? (and problems viewing youtube vids)"
date: 2008-07-10
forum: General Help
---

### Post by Parkbench on 2008-07-10
Hey all, I'm fairly new to ubuntu so I'm just getting used to it. I was wondering if there was a way to remove the menubar at the top of a firefox window, that is, the bar that has "File Edit View History" ect in it, possibly make them into a button on the navigation bar or something. The reason for this is that when I have the ubuntu top panlel, the name of the window, and the menu/navigation/bookmark/tab bars, it looks very cluttered and ugly. 

The other issue was that when I navigate to a youtube page, sometimes firefox abruptly closes. When it doesn't the videos play fine, but maybe once in five times, it will just close itself. Does anyone know why this is, and anything I can do to fix it?

Thanks.

---

### Post by Ramses de Norre on 2008-07-10
[https://addons.mozilla.org/en-US/firefox/addon/1455](https://addons.mozilla.org/en-US/firefox/addon/1455)

---

### Post by Parkbench on 2008-07-10
Just what I wanted, cheers.

---

### Post by kevmitch on 2008-07-10
The flash problem (which is what I'm assuming the youtube thing is) would definitely be a bug. Unfortunately this is not uncommon with flashplugin-nonfree, but especially if you are running it on an amd64 system through nspluginwrapper. 

I would file it with launchpad. Provide as detailed information as possible including the version of flash (navigate firefox to about:plugins) and firefox itself (about:). Also be sure to include information about your sound and video hardware (lspci should give these to you) as well as what video driver you are using (take a look in /var/log/Xorg.0.log). You could even take it a step further and see if you can reproduce the crash using the "vesa" driver for the xserver instead of one specific to your card.

I just randomly found this on google:
[http://grumpymole.blogspot.com/2006/10/ubuntu-firefox-flash-crash-this-fix.html](http://grumpymole.blogspot.com/2006/10/ubuntu-firefox-flash-crash-this-fix.html)

No idea what that does or why it should work, but you might give it a shot.

Oh, and an other thought: are you using compiz? Does disabling it help?

---

