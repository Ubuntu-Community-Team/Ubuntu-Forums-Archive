---
title: "Files (Nautilus) - open with Recent instead of Home"
date: 2018-06-27
forum: General Help
---

### Post by ranger12 on 2018-06-27
Greetings all,
Ubuntu 18.04 LTS  - Is there a way to have Files open by default at Recent instead of Home? I have been poking around online but have not found anything on this. I browsed the nautilus settings with DConf editor but there is nothing in there about it. It would be more convenient for.me.
As Charlie Chan(Warner Oland) use to say: "*Thank you so much*".

---

### Post by vanadium on 2018-06-27
How do you open Files? If through the Dash, then you may edit the corresponding .desktop file and add your preferred folder as command line argument.

The safe way to do this is to copy the .desktop file of nautilus file manager from /usr/share/applications to your personal .local/share/applications folder. Then you edit the .desktop file as normal user and change the exec line to "nautilus recent:///". Your private .desktop file takes preference over the system wide one, so your command line argument will be honoured the next time you start files through the launcher or the applications overview.

---

### Post by monkeybrain20122 on 2018-06-27
I think your purpose really is to easily access recently used files rather than having nautilus opening in a specific location. Depending on the type of files (if pdf or djvu) the Document viewer (evince) keeps a list of recently used documents. There maybe some gnome shell extensions that enable you to view recent files, but I am not sure since I don't use gs. I use unity (in 18.04) and the features of showing recent files and file searching is built in to the dash (IIRC GS used to do it in the early days but these features were removed later because you are supposed to use evince or some such reasons)

---

### Post by ranger12 on 2018-06-27
Mixed results. Good news is that editing a local copy of the .desktop file and launching it directly from my .local/share/applications folder does work. Bad news is trying to get it to do it from the dock. Thanks anyways but I think this is going to be a pain so I will just click on the Recent folder when I open up Files. Yes, I do mean opening up Files at the Recent folder.

---

### Post by mc4man on 2018-06-27
> **ranger12 said:**
> Mixed results. Good news is that editing a local copy of the .desktop file and launching it directly from my .local/share/applications folder does work. Bad news is trying to get it to do it from the dock. Thanks anyways but I think this is going to be a pain so I will just click on the Recent folder when I open up Files. Yes, I do mean opening up Files at the Recent folder.

Correct. In a gnome session in 18.04 you'd have to jump thru a host of hoops to get the desired result from a nautilus icon in the gnome-shell launcher. Not worth it at all.
(- in a unity session only a couple of hoops but still not straightforward..

---

### Post by vanadium on 2018-06-30
Delete the existing icon for files from the dock. Then start Files using the launcher - this will use your local .desktop file. Pin this instance to the dock.

---

### Post by mc4man on 2018-06-30
> **vanadium said:**
> Delete the existing icon for files from the dock. Then start Files using the launcher - this will use your local .desktop file. Pin this instance to the dock.

It does seem to work if the new .desktop is named anything but what nautilus installs for .desktops (it installs7 .desktops)
You can use the contents of the existing .desktops, just not the name(s)

(- if you happen to use the contents of the main nautilus.desktop (org.gnome.Nautilus.desktop) & doesn't work after a  restart then try changing the DBusActivatable=true line to false

---

