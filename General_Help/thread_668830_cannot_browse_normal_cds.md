---
title: "cannot browse normal cds"
date: 2008-01-15
forum: General Help
---

### Post by Meow27 on 2008-01-15
whenever i try to open up a normal cd (in every case i have so far this is a game cd) sound juicer will thing this is an audio only cd and i cannot browse my disks! (i want to install windows apps in WINE .... >_>)

im a complete beginner to all of this stuff but i find it difficult to look at my files on them :( can u guys help? thanks :)

---

### Post by Meow27 on 2008-01-16
bump

---

### Post by ahaslam on 2008-01-16
Are you saying that you want it to show the contents on insertion, but sound juicer is trying to load it instead?

Have you tried navigating to it with the terminal or a file manager like nautilus/thunar? Ubuntu's default location should be /media/cdrom0/
If it's not there it'll need mounting:
```
sudo mount /dev/scd0 -t iso9660 /media/cdrom0
```

I hope that helps, if not please expand on your OP.

---

### Post by patrickthebold on 2008-01-16
Try System->Preferences->Removable Drives and Media

---

### Post by Meow27 on 2008-01-16
ahaslam, i can see that my disk is mounted. my problem is i cant veiw the files there. whatever i try, sound juicer takes over. its really annoying >.>

i tried going with "Preferences->Removable Drives and Media" but i really dont know what to do (when i changed some options, nothing changed.)

---

### Post by patrickthebold on 2008-01-16
In the removable media dialog, go to multimedia and uncheck play audio cds when inserted.

---

### Post by ahaslam on 2008-01-17
A game cd should have a valid filesystem & be able to be mounted as above. Once it's mounted it's just a case of navigating to it, which you've tried. I assume these are retail CDs that are primarily audio with added extras? In which case there may be no fileststem, hence it's thought to be audio only. In this case I know of only one way to browse the disc & it'll require a few dependencies.
```
sudo apt-get install konqueror kdemultimedia-kio-plugins
```
Then launch Konqueror & type _**audiocd:/**_ in the address bar. That should get you going ;)

PS. Thanks Meow27, I never knew I had some ogg vorbis on this cd ;)

---

### Post by Meow27 on 2008-01-17
thanks mate :D

the audiocd path only searches the disk for music files. 

but the path /media/cdrom0 is browsable now. thanks mate :)

by the way i ahve alot of unwanted shortcuts in my newly made "other folder ". is there a way i can remove this without messing anything up? (i know add/remove manages menu shortcuts)

---

### Post by ahaslam on 2008-01-17
They'll be .desktop files located in either ~/.local/share/applications or /usr/share/applications. You can simply edit them & add/amend **_NoDisplay=true_**, menu editors are also available.

I'm glad you got it working, I learned something too ;)

---

