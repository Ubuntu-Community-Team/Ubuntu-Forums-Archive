---
title: "Ubuntu Software Center Unable to Install Updates to Installed Software"
date: 2019-02-12
forum: General Help
---

### Post by goodstuff9 on 2019-02-12
Ubuntu 18.04.1, Gnome Shell 3.28.1, Ubuntu Software 3.28.1, on an x86_64 architecture computer.  

Recently I began having this problem:  

Ubuntu Software presents desktop notifications saying that various software packages have updates available.  I start Ubuntu Software, go to the "Updates" tab, and see all the packages to update with "Update" buttons next to them.  For every single one, when I click on the "Update" button, I get an error message of this format:  

Unable to update xxxxx:
Could not find update for 'xxx/xxx.xxx.xxx.xxx/x86_64/stable'

where "xxx" represents some text.  

(I attached a screenshot of a typical message to this posting for a software package called "Cozy".)  

After I dismiss this message, the application disappears from the list of packages to update.  Eventually, I go through them all, and then Ubuntu Software says "Software is up to date".  

I have no idea whether or not the packages actually updated correctly.  

What does this message mean, and what should I be doing to fix whatever is wrong?  

[ATTACH=CONFIG]282488[/ATTACH]

---

### Post by deadflowr on 2019-02-12
That's a [flatpak]("https://flatpak.org/") package, so maybe try updating the flatpak with
```
flatpak update
``` from a terminal,
just to see what it does.
post back the results.

A shot in the dark is you might be running into this issue:
[https://gitlab.gnome.org/GNOME/gnome-software/issues/235]("https://gitlab.gnome.org/GNOME/gnome-software/issues/235")

---

### Post by goodstuff9 on 2019-02-12
Testing out your idea on just the one software package ("Cozy"), I did this:  


main1@system1:~$ flatpak update com.github.geigi.cozy
Looking for updates&#8230;


        ID                           Arch   Branch Remote  Download
 1. [&#10003;] org.gnome.Platform.Locale    x86_64 3.30   flathub 1.0 kB / 222.9 MB
 2. [&#10003;] com.github.geigi.cozy.Locale x86_64 stable flathub 1.0 kB / 190.0 kB

Updates complete.
main1@system1:~$


So, it appears that your theory is likely correct.  Something is wrong with the Ubuntu Software application when it comes to flatpak packages.  I don't know what is wrong, nor how to fix it.  (I guess in the meantime if I get notifications from Ubuntu Software that there are updates, and those updates will not work in Ubuntu Software, I can just go to a terminal and run "flatpak update".  Not a solution, just a workaround.)

---

