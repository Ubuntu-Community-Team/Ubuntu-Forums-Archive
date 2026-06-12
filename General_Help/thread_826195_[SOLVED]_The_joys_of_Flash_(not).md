---
title: "[SOLVED] The joys of Flash (not)"
date: 2008-06-11
forum: General Help
---

### Post by windoze87 on 2008-06-11
All of you have heard the saying "if it aint broke, dont fix it", right? Or in my case, "if it's only partially broke, dont fix it"... anyway, in my quest to pursue an answer to the lack of sound in Flash videos on youtube and such, i decided to uninstall and reinstall the flashplugin-nonfree package. Joy and O Joy, i see a frustrating message.

"Download done. md5sum mismatch install_flash_player_9_linux.tar.gz The Flash plugin is NOT installed"

From what little i've found about it, this little problem is wrapped up in how Ubuntu checks a new version of Flash against the old version, and if something doesnt match up, it won't install it... that, and the lovely people at Adobe are ever so kind as to only have download-and-go Flash for Windows users. In any case, my question is... is there a way around the checksum? Or am i doomed to wait until this problem is solved, or i learn how to fix it myself (which im not against doing, i just dont have enough knowhow yet)? And if neither is a viable option, is there a way for me to install an older version of Flash, and would i still be able to watch dumb people doing dumb things on Youtube? I've tried using the open-source equivalents of Flash, and while they're worthy projects, Gnash in particular doesnt like my computer. I'll be waiting to hear any suggestions you guys have. Thanks in advance

---

### Post by aysiu on 2008-06-11
You can always try installing Flash manually:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by windoze87 on 2008-06-11
That's a neat trick, i didnt know you could go into your filesystem as root. Anyway, i got Flash to install, but now i have a new problem... the flash videos won't load. The plugin works and i see the Magical Spinning Buffer Icon of Death, the volume slider works, etc, but the video itself won't load. My firewall doesnt detect anything going in and out during the "loading", nor does GDesklets or KPPP. If i don't have something installed correctly, how could i find out? I believe i have everything i need for firefox installed from Synaptic... i temporarily set NoScript to allow everything, and under about:config in Firefox, the value for noscript.forbidflash is set to "false". Any ideas, anyone? Btw, i'm running Firefox 2.0.0.14 under Ubuntu 7.04, and my internet connection is Verizon's crappy "high-speed" 2Mbit EV-DO. Thanks guys

---

### Post by aysiu on 2008-06-11
Can you try this?

Close Firefox. Press Alt-F2. Type ```
firefox --profilemanager
``` and create a new profile and use that. With that new profile, can you view Flash?

---

### Post by windoze87 on 2008-06-11
sure didn't. I looked in Firefox's error console to see if i could maybe find something helpful, but alas, nothing. Would I be better off uninstalling everything Flash-related, and then reinstalling it all? I'd like to find out why it's doing this and fix it a lot more than reinstalling and it just work, but if that's the easier route, ill try it. I'll be waiting to hear back from anyone with suggestions, and once again thanks for your help.

---

### Post by windoze87 on 2008-06-11
On a whim, i decided to go into the mozilla directory where i installed the plugin to look and see if everything was in there... and it wasnt. The file i have is called "libflashplayer.so"...but im going to hazard a guess that the file i need is "flashplayer.xpt" Kinda weird that it's not floating around in there. I'm going to see if i can find this .xpt file and why it wasn't installed... ill post back with what i find.

this flashplayer.xpt isnt in the .tar.gz folder...so i'm back to square one :(

---

### Post by benny bronx on 2008-06-11
libflashplayer.so is the file I have in my usr/lib firefox 3 and firefox add-ons folders.  Everything is working fine, but I am using the flash 10 beta.  Did you try disabling noscript from tools-add-ons, at least this will completely eliminate NS as the problem

Edit: libflashplayer.so is actually in the plugin sub-folder in usr/lib/firefox3
and usr/lib/firefox add-ons (link to folder)

---

### Post by Linux_Man on 2008-06-11
A similar thing happened to me, I deleted my Firefox profile directory and started again (be sure to back it up though if you want your bookmarks and etc.)

---

### Post by windoze87 on 2008-06-11
i was looking at the Ubuntu wiki on ubuntuguide.org when i saw the info about the .xpt file, so after i removed flashplugin-nonfree, i installed it from the tarball through the command line, and that's when i noticed that there WAS no .xpt file in the tar, but i reinstalled it anyway. The two plugins i have to do with flash as far as i can see in my /firefox/plugins directory is libflash-mozplugin.so and libflash.so. I tried your suggestion, benny bronx, and had the same result as before. I tried running sudo firefox -H, thinking maybe installing it as root led to me only being able to use it as root even though i installed it in my directory, and still no good. I'd rather not wipe out Firefox and start over, not for fear of losing my bookmarks, but that's a long list of plugins i use with Firefox that i don't wanna search through again lol... I do have Konqueror installed as a backup browser though, i'll try installing its plugin for Flash and see if it works with it, so i know if it's a problem with Flash or a problem with Firefox. I'll post back after i do that. Many thanks for everyone's help so far.

---

### Post by windoze87 on 2008-06-14
Well, I reinstalled Firefox and flash works pretty decent now... I can now watch videos most anywhere on the Internet. I still can't watch videos on Youtube, but i figure that's a problem with them and not me if i can use it everywhere else. Thanks for everyone's help, you rock my socks :guitar:

---

