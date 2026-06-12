---
title: "How to uninstall Nooblab themes"
date: 2017-03-26
forum: General Help
---

### Post by lysander6662 on 2017-03-26
I installed some of the Nooblab themes today [radiance and ambiance packs] and I can't seem to get rid of them. I can't delete them directly from the /.themes folder since Ubuntu won't allow me [I logged in as root in the terminal but this didn't make any difference, presumably I have to do so another way or something?], and I can't find a command to uninstall them for the terminal. Anyone have any ideas?

---

### Post by Frogs Hair on 2017-03-26
If you installed via a Noobslab PPA the themes are located in usr/share/themes and installed as .debs. You can install and run the ppa purge.

```
sudo apt-get install ppa-purge

```
Insert the PPA name after: 

```
sudo ppa-purge ppa:someppa/ppa
```

---

### Post by lysander6662 on 2017-03-27
Thanks. I'll go into Software Updater, I'll try and find the repo through there.

Why would it not let me delete it through the GUI? The 'move to rubbish bin' option was greyed out.

---

### Post by speartip on 2017-03-27
Just install synaptic & uninstall the themes from there.
Be careful logging in as root & deleting stuff, could have dire consequences.

---

### Post by lysander6662 on 2017-03-27
Thanks, I managed to uninstall the default ambiance theme in the process but I got it back. Thank you very much.

---

