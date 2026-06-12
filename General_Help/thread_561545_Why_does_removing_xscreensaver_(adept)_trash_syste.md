---
title: "Why does removing xscreensaver (adept) trash system?"
date: 2007-09-27
forum: General Help
---

### Post by Neobuntu on 2007-09-27
I noticed "xscreensaver" comes up when the monitor times out, but only after the kscreensaver that I have set up with "Configure Desktop" in KUBUNTU. I had guessed that the xscreensaver was redundant; for gnome or xfce and I would simply remove it and it's data and see what happens.

Why the ... does Adept then remove all manner of packages; that seem to be unrelated? It removed Nvidia-glx (for example)! About 20 major components.

How do I easily get them back? What's going on? Where did I go wrong?

I'm not a rank newbie (and I'm also not beyond an error, either). So what did I do bad?

How can I list what was just (before I stopped it) removed? 

I'm sure I can't reboot successfully now; until I reverse this. 

This is a critical problem for me.

---

### Post by Neobuntu on 2007-09-27
I could not install kubuntu-desktop (hoping this would install what was removed) but I could not due to a "lock" of the stopped adept. Finally "killall dpgk" and the requested  "dpkg --configure -a" alowed me to do it. 

Now it looks like it would install  some things but WHY are these packages "unused". I use them! Please help!


> The following packages are unused and will be REMOVED:
  abiword abiword-common abiword-help abiword-plugins anthy apport-gtk file-roller gnome-terminal-data gnumeric-common gnumeric-gtk
  gqview gtk2-engines-xfce gxine human-cursors-theme human-icon-theme human-theme libaiksaurus-1.2-0c2a libaiksaurus-1.2-data
  libaiksaurusgtk-1.2-0c2a libanthy0 libchewing3 libchewing3-data libdb4.3++c2 libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-common
  libgoffice-gtk-0-3 libgtkmathview0c2a libots0 libt1-5 libwpd-stream8c2a mousepad onboard orage python-exo python-gtkhtml2
  python-virtkey scim-anthy scim-chewing scim-hangul scim-pinyin thunar-archive-plugin thunar-media-tags-plugin ubuntu-artwork xarchiver
  xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin
  xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin
  xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin
  xfce4-taskmanager xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xubuntu-artwork-usplash
  xubuntu-default-settings xubuntu-docs
The following NEW packages will be automatically installed:
  adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater brltty ncompress p7zip-full xorg zoo
The following NEW packages will be installed:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator ark brltty kubuntu-default-settings
  kubuntu-desktop language-selector-qt ncompress p7zip-full xorg zoo
0 packages upgraded, 17 newly installed, 74 to remove and 0 not upgraded.
Need to get 8872kB of archives. After unpacking 130MB will be freed.
Do you want to continue? [Y/n/?]   

I said no and now I'm dead in the water. (Not a happy camper here) I'm trying to be civil, if you can't tell.

---

### Post by Neobuntu on 2007-09-27
Now I've said yes. I can only guess, aptitude (I actually used Adept at first) thinks it should do this when I remove xscrensaver. Is  xscreensaver part of Kubuntu?

---

### Post by Neobuntu on 2007-09-28
I found kbd and mouse errors along with glx too.

> 
aptitude search xorg | more
got me the following ideas.


> aptitude install xserver-xorg-input-kbd

So with that error solved after issuing startx, I also did...


> aptitude install xserver-xorg-input-mouse

Got me back into X. This is NOT for newbies.

This is TOTAL BS!

---

### Post by Wolki on 2007-09-28
> **Neobuntu said:**
> Now I've said yes. I can only guess, aptitude (I actually used Adept at first) thinks it should do this when I remove xscrensaver. Is  xscreensaver part of Kubuntu?

Did you install xubuntu? Apparently all these things were installed as dependancies of xubuntu-desktop, so when you removed xscreensaver it was also removed, and thus all things that got installed with it were marked as unneeded dependencies (and thus, aptitude removes them automatically)

Personally, I think automatic removal of dependencies like aptitude does is dangerous, and prefer using apt-get unless absolutely neccesary. 

One thing you could try is doing "dpkg --get-selections". All lines containing "deinstall" are those whose packages you've uninstalled, either as part of this or before. Reinstall those you want to get back.

---

### Post by Neobuntu on 2007-09-29
Thank you. That is exactly what I needed. Now I can be sure all is well.:)

---

### Post by Neobuntu on 2007-09-29
I knew it (dpkg/adept) "thought" it should do that.

I use aptitude so I can go back and remove all that came with. I have a simple link to aptitude called just apt. So I "apt" instead of apt-get and this means I use aptitude (and I believe Adept does like Aptitude).

Now that I understand the down side, I think I'll still keep on; because now, I know how to deal with it.
> 
dpkg --get-selections is cool.

I do not think I would rather have to pick out a bunch of installed crap that came with something, rather than check and reinstall what I want, if something slips by me again.

---

### Post by Wolki on 2007-09-29
> **Neobuntu said:**
> I use aptitude so I can go back and remove all that came with. I have a simple link to aptitude called just apt. So I "apt" instead of apt-get and this means I use aptitude (and I believe Adept does like Aptitude).

Apt-get since edgy marks dependencies as well, but doesn't deinstall them when you just install something, you need to do "apt-get autoremove" manually. Opt-In removal seems to make more sense to me, especially since I often notice errors. But I guess tastes are different here, else aptitude wouldn't be so popular.

> Now that I understand the down side, I think I'll still keep on; because now, I know how to deal with it.
 is cool.

Even cooler is that you can take --get-selection's output, then import it on another comnputer with --set-selections to copy one package setup from one computer to the next. apt is great. :)

---

