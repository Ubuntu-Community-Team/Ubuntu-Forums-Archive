---
title: "Why do I seem powerless in Edgy?"
date: 2007-01-18
forum: General Help
---

### Post by nuggetz on 2007-01-18
I'm just curious why the out of the box ubunto experience seems dumbed down. I know it's the distro that "should just work" but I wanna be root and have the liberty to rule my own box. So what's up? I know I can sudo all day but where are all the icons that point me to advanced features. Is there a control panel type app? So far, this is the best distro I've used and I'm loving it but I was just curious about this.

---

### Post by robert-s on 2007-01-18
You can become root by typing 

```
sudo su
```

then your password, but for most things that's not needed, since su does the job. Many settings can be configured in the System > Preferences and System > Admin menus, and if you're feeling brave there are lots of text based config files you can edit. A little bit of Googling should tell you what to edit to do what.

---

### Post by Henry Rayker on 2007-01-18
The root policy comes from the fact that we don't want to encourage the new users to keep up with their Windows"always administrator" habits. There are ways to enable the root account, but I'm sure a quick search will bring you the information you crave.

As for icons to advanced features, what kind of features do you have in mind.

---

### Post by mcduck on 2007-01-18
> **robert-s said:**
> You can become root by typing 

```
sudo su
```

then your password, but for most things that's not needed, since su does the job. Many settings can be configured in the System > Preferences and System > Admin menus, and if you're feeling brave there are lots of text based config files you can edit. A little bit of Googling should tell you what to edit to do what.

Better use 'sudo -i' instead. 'sudo su' will use your own profile while 'sudo -i' loads root's profile.

Apart from Configuration Editor there is no 'advanced' options in Gnome. If you want to change something that's not in normal options or in Configuration Editor you need to do it by editing text files. To start Configuration Editor run 'gconf-editor' in terminal or enable the entry in Applications menu with the menu editor.

Anyway, using sudo instead of root account takes no power away from you. During my time in Ubuntu I haven't found anything I couldn't do with 'sudo', and I can tell you that I mess a lot around with my computers..

---

### Post by nuggetz on 2007-01-20
Why does the screen saver have no configuration options? I want to tweak some of them. Is this a gnome screen saver and is it different from the Xscreensaver? Maybe that it.

---

### Post by mcduck on 2007-01-20
> **nuggetz said:**
> Why does the screen saver have no configuration options? I want to tweak some of them. Is this a gnome screen saver and is it different from the Xscreensaver? Maybe that it.

Yes, that's the problem. At some point Gnome developers decided to replace Xscreensaver with Gnome Screensaver which has no configuration options. Sometimes they say that the lack of options is because of corporate users and such wouldn't want their workers to have offending screensavers, sometimes they say that configuration options are just not done yet.. :rolleyes: 

Anyway, you can just uninstall gnome screensaver and install xscreensaver instead. Gnome screensaver handles disabling screensavers while watching videos better than xscreensaver does but other than that there should be no problems.

---

### Post by allwin on 2007-01-20
If you want to play with some config files, try running gconf-editor, which allows you some finer grain changes to your Gnome desktop environment.  And then you could always install a package called BUM (boot up manager) which allows you to poke at a few more wires under the hood.  And read up about hdparm (try the man pages "man hdparm") to put a little charge into your disk's speed, maybe.  Then, there's a lot of fiddling you could do with /etc/X11/xorg.conf if you go out and find your graphics card driver's documentation specific to the release of the driver you are using.  But no, no CONTROL PANEL...hey, wanna WRITE ONE?  I'll be your first "customer".

---

