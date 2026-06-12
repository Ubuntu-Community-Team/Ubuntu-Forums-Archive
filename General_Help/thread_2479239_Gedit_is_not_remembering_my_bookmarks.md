---
title: "Gedit is not remembering my bookmarks"
date: 2022-09-19
forum: General Help
---

### Post by Paddy Landau on 2022-09-19
I often use the Bookmarks feature in Gedit (menu > Preferences > Plugins > Bookmarks).

The feature has always worked well. But, since moving to Ubuntu 22.04, Gedit no longer remembers my bookmarks. I can set a bookmark and later navigate to it, but as soon as I close the file after saving it, Gedit forgets the bookmarks that I've set.

Do you know how I can fix this problem, please?

[LIST]
[*]Ubuntu 22.04
[*]Gedit 41.0-3 from the standard installation
[*][FONT=courier new]gedit-plugin-bookmarks[/FONT] 41.0-1 installed from the standard repositories
[/LIST]

---

### Post by zebra2 on 2022-09-19
The only thing I have to offer is that I'm using Ubuntu 22.10 with gedit bookmarks v 42.1-1 and it works just fine.

```

ii  gedit-plugin-bookmarks 42.1-1       amd64        Bookmarks plugin for gedit

```

---

### Post by Paddy Landau on 2022-09-19
> **zebra2 said:**
> The only thing I have to offer is that I'm using Ubuntu 22.10 with gedit bookmarks v 42.1-1…
Interesting! On 22.04, Gedit and its plugins are all version 41.0.

I installed Gedit 42.2 using flatpak, and it has the same problem. On the other hand, the snap version, Gedit 40.1, does work.

I wonder if Canonical is fixing the problem in its snaps? (Unfortunately, the snap version is unusable because of Canonical's excessively [paranoid security model]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1897562").)

I've just [raised a bug]("https://gitlab.gnome.org/GNOME/gedit/-/issues/525") about this with the Gedit devs.

---

### Post by zebra2 on 2022-09-19
OK, I just installed the plugin but v41.0 (default for 22.04), on my 22.04 system and it doesn't work.

---

### Post by zebra2 on 2022-09-19
Gedit on my 22.10 system is 42.2. You might be able to install the later version, not sure.

Edit: Since the problem has been duplicated I would call it a bug.

---

### Post by Paddy Landau on 2022-09-19
> **zebra2 said:**
> OK, I just installed the plugin but v41.0 (default for 22.04), on my 22.04 system and it doesn't work.
Yes, that's my situation.
> **zebra2 said:**
> Gedit on my 22.10 system is 42.2. You might be able to install the later version, not sure.
The flatpak version is 42.2, and it doesn't work. There is obviously a difference between the flatpak and PPA version, though I couldn't tell why.
> **zebra2 said:**
> Edit: Since the problem has been duplicated I would call it a bug.
Agreed, thank you. Would you mind [upvoting the bug]("https://gitlab.gnome.org/GNOME/gedit/-/issues/525"), please (the thumbs-up underneath the report)?

---

### Post by zebra2 on 2022-09-19
> **Paddy Landau said:**
> 
Agreed, thank you. Would you mind [upvoting the bug]("https://gitlab.gnome.org/GNOME/gedit/-/issues/525"), please (the thumbs-up underneath the report)?


Done! Pleased that I could help.

---

### Post by sudodus on 2022-09-19
I edit text files with the GUI program **[FONT=Courier New]geany[/FONT]**, installed via the apt package with the same name.

---

### Post by #&amp;thj^% on 2022-09-19
> **sudodus said:**
> I edit text files with the GUI program **[FONT=Courier New]geany[/FONT]**, installed via the apt package with the same name.

+1 Same for me.....great minds. LOL

---

### Post by norobro on 2022-09-19
FYI, I get the following warning on my Debian Sid box running Gedit 42.2 from the command line, setting a bookmark and saving the file:```
[FONT=monospace][COLOR=#000000]** (gedit:18460): [/COLOR][COLOR=#ff0000]**WARNING** [/COLOR][COLOR=#000000]**: [/COLOR][COLOR=#1818B2]11:33:32.804[/COLOR][COLOR=#000000]: Set document metadata failed: Setting attribute gedit-bookmar[/COLOR]ks not supported[/FONT]
```

---

### Post by Paddy Landau on 2022-09-20
> **zebra2 said:**
> Done! Pleased that I could help.
Thank you :)
> **sudodus said:**
> I edit text files with the GUI program **[FONT=Courier New]geany[/FONT]**, installed via the apt package with the same name.
I'm unsure how that's supposed to help me. Does Geany have the same functionality (including the same functionality from Gedit's plugins)? If so, I can look.
> **norobro said:**
> I get the following warning on my Debian Sid box running Gedit 42.2 from the command line…
Thanks for the heads-up. I get that too, regardless of whether I use bookmarks or not.

But, if I turn off the Bookmarks plugin, that error disappears.

Searching for the last part of that text in quotes gets zero results from Google. That must be a first for me! Without quotes, I get no useful information.

I'll test this with all the relevant versions, and add it to the bug report.

---

### Post by sudodus on 2022-09-20
geany has the functionality that I need, and I know that there are plug-ins, that I don't use. You might like it.

---

### Post by Paddy Landau on 2022-09-20
> **sudodus said:**
> geany has the functionality that I need, and I know that there are plug-ins, that I don't use. You might like it.
OK, I'll have a look at it.

---

