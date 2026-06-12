---
title: "Declare dependencies on oddball projects"
date: 2017-09-11
forum: General Help
---

### Post by Myoldmopar on 2017-09-11
Greetings,

I'm working on a project where we have a Github repo storing a variety of things: LaTeX code for generating reports, datasets and python scripts to mine the data, etc.  It's not a single standardized project type.  I'd like to declare the dependencies in a standardized manner if possible.

On my Django apps, we specify dependencies using requirements.txt files for pip packages and bower files for JavaScript nonsense.  Similarly gem files for Ruby projects.  On this app, we have at least a couple "apt-get" dependencies.

Is there a certain file naming convention and file format most commonly used for declaring apt-get dependencies when the project itself is not suitable to be turned into a full .deb package?

Thanks!

---

### Post by mc4man on 2017-09-12
I would seriously doubt it, apt is designed for .deb's (via the control file)

Edit: I would think (with a little trial & error) you could create a dependencies package (.deb) 
Similar to what you'd see if you used mk-build-deps on a repo source

---

### Post by dragonfly41 on 2017-09-12
Could your app bundle be distributed as an [appimage]("https://askubuntu.com/questions/774490/what-is-an-appimage-how-do-i-install-it")?

---

