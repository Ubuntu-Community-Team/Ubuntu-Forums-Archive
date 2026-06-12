---
title: "Rar Archives: Extract To..."
date: 2008-02-14
forum: General Help
---

### Post by TombstoneX on 2008-02-14
[SIZE="4"]**Question: **Having "Extract To..." for .Rar, .zip, and ect. archives, similar to Windows On Ubuntu[/SIZE]

[SIZE="3"]**Solution:** Go to: [http://g-scripts.sourceforge.net/cat-archiving.php]("http://g-scripts.sourceforge.net/cat-archiving.php") and install the scripts to ' /home/*username*/.gnome2/nautilus-scripts '. Make sure you enable the scripts to be Executed. RIght click on the script file. Select 'Properties' Go to the 'Permissions' tab and select 'Allow executing file as program'. See image below:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60014&stc=1&d=1203347667[/IMG][/SIZE]


-------------------------
Original Message:
-------------------------
Hey guys,

This is going to sound like a worthless question. I do alot of downloading of Rar Archives (*.r01 or even *.001) 

When i was using windows with winrar i had an option that had "Extract To..." when you click this option it would take you to a screen that you could put in the folder to extract the files to. In ubuntu all i get is open Archive Manager, where i can extract it to the desired folder, problem is when i have 20 different archives to erxtract it gets redundent to open it up, extract the files, then close the archive and move to the next archive.

There is also an option to "Extract Here", this is not also a very good option as i would have to extract to the folder then cut and paste into the drive/folder i want it to go into.

I was wondering if there was a way to add the extract to option, or even to have an option that extracts to a specific location. Example: Clicking on something that says "Extract to TV Shows" which will inturn extract it to /home/username/TV_Shows

Thanks in advance,
Preston

---

### Post by NT4usB on 2008-02-14
I use unrar from a command line:```
unrar e /path/to/file001.rar /path/to/where/iwanttoextract/
```

---

### Post by danwood76 on 2008-02-14
You could setup a nautilus script to do this for you which you can add to the right click menu.

Using a combination of this guide:
[http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/)
and the command in the previosu post you could make it extract to a certain folder each time, not sure how you could add user input to this (specifying a directory) but I think it is possible.

---

### Post by danwood76 on 2008-02-14
Just found these scripts that you can download already made:
[http://g-scripts.sourceforge.net/cat-archiving.php](http://g-scripts.sourceforge.net/cat-archiving.php)

Some of them will do exactly what you want.

---

### Post by TombstoneX on 2008-02-14
Thanks for the prompt relies, i will give it a go when i get home. And ill post back my outcome.

---

