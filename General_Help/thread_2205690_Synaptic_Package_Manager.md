---
title: "Synaptic Package Manager"
date: 2014-02-15
forum: General Help
---

### Post by jasonbiz88 on 2014-02-15
I want to mark vuze azureus for reinstallation. Will marking the application for reinstallation remove/delete all of my files that I am seeding or will it just re-install over the old version keeping all of my files and settings in place?

---

### Post by deadflowr on 2014-02-15
removing, purging, or reinstalling shouldn't touch any of the files you have inside your home folder.
But if you are really worried that it might, go to where you have the seeds saved and back them up.

---

### Post by Dennis N on 2014-02-15
It will just do a reinstall of the marked package, possibly from your local cache. You can always simulate any install first, by using the option -s if you want:

**apt-get install -s <package>**

no sudo used. apt-get will then show what will be done.

---

### Post by Frogs Hair on 2014-02-15
Re-installing will only help if something had gone wrong during the initial installation and if the application is running a process it could interfere with it. Re-installing won't remove the settings configuration and you might want to indicate why you think the application needs to be re-installed.

---

### Post by jasonbiz88 on 2014-02-15
I manually updated the application by downloading the tar. file from the official site and copying the newer jar.file over the old one. It updated the app, but now the application in house updater is screwed up. It sill downloads and uploads, I just don't think I'll be able to keep it up to date anymore.

---

### Post by deadflowr on 2014-02-15
You'll keep getting whatever updates the program gets whenever updates for it come out.
But since you've changed a file, it'll be uncertain what'll happen when those updates come.
It's possible they'll fail because you've changed something manually.
And it's also possible that you will have to re-apply whatever manual setting you did.

If your goal is to reset to the repo version , then running a complete removal should rid the system of all. You could also go to where you put the new file in manually and, if it is there, remove it.
Then simply install the program again.

None of this should affect the actual torrent download files.

---

### Post by jasonbiz88 on 2014-02-15
I'm not worried about the files in the home folder. I'm worried about losing the originals files that live in vuze. The files that I seed. Are you familiar how vuze operates?

---

### Post by deadflowr on 2014-02-15
> **jasonbiz88 said:**
> I'm not worried about the files in the home folder. I'm worried about losing the originals files that live in vuze. The files that I seed. Are you familiar how vuze operates?

I'm familiar with how Ubuntu operates.
The files you seed are personal files and not system files.
Synaptic is only going to remove system files.

---

