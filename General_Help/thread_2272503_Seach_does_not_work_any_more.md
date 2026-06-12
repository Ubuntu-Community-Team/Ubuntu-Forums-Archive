---
title: "Seach does not work any more"
date: 2015-04-07
forum: General Help
---

### Post by 171742 on 2015-04-07
Hello,

I deleted a lot of data, now the search does not work any more. Takes a long time and shows nothing. What to do?

Ubuntu 14.4 lts.

Thanks!

---

### Post by Bucky Ball on 2015-04-07
Which search do you mean?

---

### Post by 171742 on 2015-04-07
Dashboard search? The default that comes up when (former) windows bar is pressed. Noted just now: Some folders work, for others no result. Thanks!

---

### Post by 171742 on 2015-04-09
Any ideas? Its really annoying..

---

### Post by dino99 on 2015-04-09
dont know how the dash works (never use that stuff as i prefer searching via nautilus); possibly a bug if it is not smart enough to rebuilt its index when the user manually delete data, as you have done.
[http://askubuntu.com/questions/37814/how-does-unitys-dash-index-and-search-work](http://askubuntu.com/questions/37814/how-does-unitys-dash-index-and-search-work)

looks like it needs zeitgeist for working; is that yours installed ?

---

### Post by 171742 on 2015-04-09
Hello,

yes it is.

---

### Post by 171742 on 2015-04-22
Hello,

any ideas? Other search engines like catfish do not work as well, recoll does. Zeitgeist reinstelled. This really makes the system far worse..

---

### Post by 171742 on 2015-05-18
?

---

### Post by corti-nico on 2015-05-18
You can use Tracker to search between files:
```

sudo apt-get install tracker tracker-search-tool

```

And let us know ;)

---

### Post by 171742 on 2015-05-18
seems not to install, no "tracker" on programms?

o@o-HP-Compaq-6910p-KL536AV:~$ sudo apt-get install tracker tracker-search-tool
[sudo] password for o: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tracker-search-tool is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  tracker-gui:i386 tracker-gui

E: Package 'tracker-search-tool' has no installation candidate
o@o-HP-Compaq-6910p-KL536AV:~$

---

### Post by corti-nico on 2015-05-18
> **171742 said:**
> seems not to install, no "tracker" on programms?

o@o-HP-Compaq-6910p-KL536AV:~$ sudo apt-get install tracker tracker-search-tool
[sudo] password for o: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tracker-search-tool is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  tracker-gui:i386 tracker-gui

E: Package 'tracker-search-tool' has no installation candidate
o@o-HP-Compaq-6910p-KL536AV:~$

Sorry my fault.
Try with this:
```
sudo apt-get install tracker tracker-gui
```

---

### Post by 171742 on 2015-05-19
Hello,

does nothing: when I search nothing turns up. But I do have recoll, that is not practical as well. Is there any way to fix the dashboard search?

Thanks!

---

### Post by corti-nico on 2015-05-20
> **171742 said:**
> Hello,

does nothing: when I search nothing turns up. But I do have recoll, that is not practical as well. Is there any way to fix the dashboard search?

Thanks!

Please note that the command I suggested you install a new software: Tracker.
Can you try to use it to find files and let us know if it works?

:p

---

### Post by 171742 on 2015-05-20
Hello,

thats what I meant: it does not work. Does not do anything, finds nothing.

BR

---

### Post by monkeybrain20122 on 2015-05-20
Did you exclude your home accidentally in system settings? Happens to me before. :)

---

### Post by 171742 on 2015-05-21
How do I test that? Sorry, very noob. I have a dropbox folder in Home, and all other is in there.

---

### Post by dino99 on 2015-05-21
i've reread the first post, and suggest to reinstall the meta-package 'ubuntu-desktop' it will list the missed packages that needs to be installed

---

### Post by 171742 on 2015-05-21
Hello,

what to post in the terminal then? Remember, I am absolutely new to this and have no skills.

BR

---

### Post by monkeybrain20122 on 2015-05-21
What data did you delete? If you just deleted data instead of uninstalled progams then there is no reason to reinstall ubuntu-desktop because it is most likely some messed up configuration in your home. In that case reinstalling ubuntu-desktop would make no difference.

If you have not uninstalled programs

 Do two things
1) Go to system settings by clicking the gear icon on the top right corner, go to Security & Privacy and then the Files and applications tab, make sure that Record file and applications usage is turned on and that the /home directory is not excluded. See screenshot.

2) If that doesn't work, nuke the Zeitgeist folder and start afresh. in the terminal type

```
mv ~/.local/share/zeitgeist ~/.local/share/zeigeist-bk
```

Then reboot (or logout and log back in should do)

---

### Post by 171742 on 2015-05-22
Hello,

I only deleted a folder from thunderbird data, so I dont think unstinstalling programs wrong was the case. As for 2) a geek friend of mine already did it and reinstalled zeitgeist. twice. thats not it. AS for 1), I cant see the home folder. How to include it? See screenshot.

Thanks[ATTACH=CONFIG]262118[/ATTACH]

---

### Post by monkeybrain20122 on 2015-05-22
Your screenshot look ok. I am stumped. :(

Check this, hope it would help [http://askubuntu.com/questions/501880/applications-dont-appear-in-the-dash-14-04](http://askubuntu.com/questions/501880/applications-dont-appear-in-the-dash-14-04)

---

### Post by 171742 on 2015-07-07
Hello,

does not seem to be the same problem. Any other tipps?

Thanks!

---

