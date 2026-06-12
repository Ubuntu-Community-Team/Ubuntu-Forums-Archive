---
title: "Deleting software"
date: 2016-09-21
forum: General Help
---

### Post by Jack_Shankle on 2016-09-21
I am by no means a Ubuntu expert.

I need to clean up wiffies computer of unneeded software.

EX: Firebird, Thunderbird, All languages but American English.

How do I go about doing this???????

---

### Post by &amp;KyT$0P# on 2016-09-21
Synaptic package manager.

Install it like this -
```
sudo apt-get --no-install-recommends install synaptic
```

---

### Post by #&amp;thj^% on 2016-09-21
How to Completely Remove a Package

Quick Instructions

1) Open the apt log file (/var/log/apt/history.log).

2) Locate the files _that were installe_d.

3) Remove the files using "sudo apt-get remove --auto-remove <file names>"

NOTE: it is a good idea **to ensure that you are not removing any extra files. **This might happen if you (or someone else) has installed other packages or updates.

4) Locate and remove configuration files and data associated with the package. Most often, they will be found in /home/ and /home/.config/ directories.
Hope this Helpful.
Regards

---

### Post by Jack_Shankle on 2016-09-21
This is probably to difficult for me but I will give it a shot.
Hope I don't destroy wiffies computer.

---

### Post by #&amp;thj^% on 2016-09-21
> **Jack_Shankle said:**
> This is probably to difficult for me but I will give it a shot.
Hope I don't destroy wiffies computer.

Start Slowly:)...and read what is being removed.
And by the way..you can always re-install packages again.
Cheers and Good Luck

---

### Post by Jack_Shankle on 2016-09-22
I feel it's to dangerous to remove these programs.
They cause other programs to be removed that would destroy
the Ubuntu version.

IMHO the OS should only include items that are necessary for
it to function. By that I mean the user should be able to make
simple selections at install time. EX: which Browser would you like 
to install, Which Email program would you like to install, what
language would you like to use etc., etc., etc.

Don't misinterpret these remarks, I like Ubuntu.

---

### Post by ian-weisser on 2016-09-22
> **Jack_Shankle said:**
> I feel it's to dangerous to remove these programs.
They cause other programs to be removed that would destroy
the Ubuntu version.

Everything installed by the Ubuntu Installer is ineligble for autoremoval.
Removing applications will remove ONLY the ubuntu-desktop metapackage in addition to the application.
If you installed using the normal Ubuntu Desktop .iso, there will be no other effect whatsoever. Even orphaned dependencies won't be removed.

If you manually added Unity (or any Desktop Environment) on top of Ubuntu Server or Ubuntu Minimal, then your Desktop may be eligble for autoremoval...but that's trivial to check and change using apt-mark.

---

### Post by HermanAB on 2016-09-22
You want to unscramble an egg...

Just clean up the menu and leave the programs in place.

---

