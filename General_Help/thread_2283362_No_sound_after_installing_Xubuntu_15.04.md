---
title: "No sound after installing Xubuntu 15.04"
date: 2015-06-21
forum: General Help
---

### Post by pbwolf on 2015-06-21
I can open gmusicbrowser and double click a tune.  A little progress bar begins to march, so it evidently thinks it is playing the tune.  Beside the date in the upper-right corner, where the volume should be, there is a red arrow pointing left (pointing at the wifi signal indicator). I can click the left-pointing red arrow and indeed it brings up a volume display.  It shows volume cranked all the way up, and gmusicbrowser with pause, previous, and next buttons.  The menu has a Sound Settings button at the bottom.  I can click it and see a big dialog box with an indicator of the ever-changing voltage or ear-drum pressure or whatever it indicates.  The dialog also has an Output Devices tab that says Port "Headphones (plugged in)".  The same cable and speaker work when plugged into another system, and worked on this system prior to Xubuntu 15.04, so I think they are ok.  But no sound comes out of Xubuntu 15.04.

I saw advice to run alsamixer.  Alsamixer does not want to run. 

```

$ alsamixer
cannot open mixer: No such file or directory

```

By the way, I installed Xubuntu 15.04 over Fedora 21, which was working ok and had in turn been installed over Ubuntu 14.04, which also worked fine.

---

### Post by QDR06VV9 on 2015-06-21
Hi pbwolf.could you install inxi?
```
sudo apt-get install inxi
```
and paste back the results of 
```
inxi -A
```
When you installed did you format or clean install?

---

