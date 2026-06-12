---
title: "Journal and Tracker extensions - how to install in Gnome Shell"
date: 2012-12-26
forum: General Help
---

### Post by Bucic on 2012-12-26
[https://extensions.gnome.org/extension/62/journal/](https://extensions.gnome.org/extension/62/journal/)
[https://extensions.gnome.org/extension/284/tracker-search/](https://extensions.gnome.org/extension/284/tracker-search/)
Normal way i.e. via web browser @ [https://extensions.gnome.org/](https://extensions.gnome.org/) doesn't work for me. (It works for other extensions). I tried installing the Journal by copying the com/org file to /home/YourUserName/.local/share/gnome-shell/extensions - to no avail. Same with copying the contents of the com/org file as well as installing the extensions packed into zip file via the Gnome Tweak tool. It returns an unspecified error.

One of the comments on extensions.gnome.org mentions a problem with missing dependency - gir1.2-gnomedesktop-3.0 but I have it listed as installed in Synaptic.

Can somebody provide step-by-step instructions on how to install both extensions?

---

### Post by Bucic on 2012-12-27
The tracker seems to be working fine/got it installed. This was helpful: [http://askubuntu.com/a/130101/](http://askubuntu.com/a/130101/)

I issued
```
sudo apt-get install tracker gir1.2-tracker-0.14
```
and then I installed the extension using the button on the page [https://extensions.gnome.org/extension/284/tracker-search/](https://extensions.gnome.org/extension/284/tracker-search/)

One more to go!

---

### Post by daKoolaid on 2013-01-06
How is Tracker supposed to work? I installed the metapackage and the GUI to set it up, then the Tracker extension but I can't search for files in the overview. Nothing comes up. I'm using Gnome 3.6.2 and I do have the gir packages you mention.

Can't get Journal to work either. Crazy how something so useful is so hard to get working.

---

### Post by cannywizard on 2013-01-17
Some of them have dependencies. I needed gir1.2-gnomedesktop3.0 to install journal on 12.10

---

### Post by daKoolaid on 2013-01-19
> **cannywizard said:**
> Some of them have dependencies. I needed gir1.2-gnomedesktop3.0 to install journal on 12.10
 I have that installed. Still, neither work though. Is searching through the shell even supported natively? RIght now I have gnome search tool and that works, but I'd like to do it through the shell like Unity.

---

