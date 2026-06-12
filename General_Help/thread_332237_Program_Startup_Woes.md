---
title: "Program Startup Woes"
date: 2007-01-05
forum: General Help
---

### Post by cj100570 on 2007-01-05
I've been a Linux user for about about 3 years now. SUSE has been my distro of choice but I recently gave it up and decided to switch to Ubuntu. All in all I'm very happy about the switch. But, and you knew this was coming, there's one thing that is driving me nuts. I've installed Firestarter and Beryl which I'd like to have start automatically when I log in. Much to my surprise there doesn't seem to be a way to get either to do so. I've tried adding each to the Startup Programs in the session manager menu but they disappear each time I log out and back in. I've read through the forums and noticed that others have had similar isues with Firestarter but as of yet I haven't found a fix. Can anyone shed some light on why programs added to the Startup menu don't actually start?

---

### Post by ingo on 2007-01-07
Hi,

my history is just about the same as yours, only that I'm hooked on Kubuntu.

As for firestarter, it starts automatically. Just do a 

ps aux|grep firestarter

and there it is - despite the fact that you do not see the interface. 

I'm afraid I can't help you with Beryl as I'm on kde and not gnome.

HTH

---

### Post by orb9220 on 2007-01-07
Are you using  **beryl-manger** as the command? That is the command.

can't help with firestarter tho.

---

### Post by cj100570 on 2007-01-07
> **orb9220 said:**
> Are you using  **beryl-manger** as the command? That is the command.

can't help with firestarter tho.

Yeah orb. Funny thing is that both FS and Beryl start with no problem when I log in as root with them set to start at log in. It's a really perplexing problem. Using a spare HD that I have Fedora Core 6 installed on I tried setting Beryl to start at login and had no problem.

---

### Post by absoludity on 2007-01-18
I'm not sure why this happens, but found a way to get beryl-manager starting automatically...

Seems that editing System->Preferences->Sessions->Startup Programs just adds special files to your ~/.config/autostarts folder.

Problem is, on my system (and probably yours) the autostarts folder is owned by root, not me. I'm guessing this is why the entry is never saved when we do it through the Sessions dialog as ourselves.

I followed: [http://gentoo-wiki.com/Beryl#Using_GNOME](http://gentoo-wiki.com/Beryl#Using_GNOME) with a few mods as follows:

# cd ~/.config/autostart
# sudo gedit beryl-manager.desktop

Then added the following to the file:

[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=beryl-manager
X-GNOME-Autostart-enabled=true

If you check your Sessions->Startup Programs now you should see it there.

BTW: I'm guessing that a simpler solution would be to change the ownership of the autostarts folder... can anyone confirm?

---

### Post by cj100570 on 2007-01-18
> **absoludity said:**
> I'm not sure why this happens, but found a way to get beryl-manager starting automatically...

Seems that editing System->Preferences->Sessions->Startup Programs just adds special files to your ~/.config/autostarts folder.

Problem is, on my system (and probably yours) the autostarts folder is owned by root, not me. I'm guessing this is why the entry is never saved when we do it through the Sessions dialog as ourselves.

I followed: [http://gentoo-wiki.com/Beryl#Using_GNOME](http://gentoo-wiki.com/Beryl#Using_GNOME) with a few mods as follows:

# cd ~/.config/autostart
# sudo gedit beryl-manager.desktop

Then added the following to the file:

[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=beryl-manager
X-GNOME-Autostart-enabled=true

If you check your Sessions->Startup Programs now you should see it there.

BTW: I'm guessing that a simpler solution would be to change the ownership of the autostarts folder... can anyone confirm?
Thanks, that did the trick.

---

### Post by cj100570 on 2007-01-19
> **cj100570 said:**
> Thanks, that did the trick.

Oops! I spoke to quick. It does start beryl at startup but the the icons can't be activated. Thank goodness I set up a root login.

---

