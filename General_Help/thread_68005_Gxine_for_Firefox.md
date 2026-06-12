---
title: "Gxine for Firefox"
date: 2005-09-21
forum: General Help
---

### Post by karimw786 on 2005-09-21
Hi all,

A total Linux newbie here!  I just installed Gxine for Hoary, but I don't know how to get it working with firefox.  It works just fine and does what I need it to do, but I just wanna get it working for firefox.

---

### Post by frodon on 2005-09-22
1. Build and install gxine.
   2. Create symbolic links to the following files in your Mozilla plugins directory: gxineplugin.a gxineplugin.la gxineplugin.so.

I never got it work perfectly, but if for you gxine plugin works please tell me.

---

### Post by karimw786 on 2005-09-22
Yes, I've also read that I have to create symbolic links, but how do I do that?  No one seems to have explained how to create symbolic links to the above mentioned files.  What I am really looking for is step-by-step instructions.

---

### Post by frodon on 2005-09-22
Sorry, i didn't understand that you requested a step-by-step help.
As you should know when you install a software a repertory is created in your/home/username folder but it's an hidden repertory,  **ls -lgrta** command will list the file in the folder including hidden files.
In the repertory /home/username/.gxine you should find the files which you want to link. All you have to do is make a link of these files in mozilla plugin directory, threfore to perform that use commands like that : ```
ln -sf /home/username/.gxine/gxineplugin.a /home/username/.mozilla/plugin/
```It's not the exact name of the directories but it should look like that. However i told you before that from my experience gxine is not the best solution to watch video streams with firefox, mplayer plugin for exemple is best for me, VLC is not bad too and you can simply install it with synaptic.

---

### Post by karimw786 on 2005-09-22
Thank you for all your help, I will give it a shot!

Also, one more thing:  instead of using gxine, what if I want to use xine?  how would I just make xine work with firefox?

---

### Post by frodon on 2005-09-22
you should know that if you install gxine, xine-ui or totem-xine all you have is xine, only the GUI change, i like a lot totem-xine interface (near from gxine i think).
Also only gxine GUI have a plugin for firefox, otherwise now the latest version of totem-xine have a plugin for firefox but unfortunately not present synaptic therefore you have to compile it by hand.
If you want to install a video stream plugin for firefox quickly, open synaptic and search for vlc and you will find the VLC plugin for mozilla (it works with firefox), maybe it the quickest way for yo to get a good plugin for firefox.

good luck  ;-)

---

