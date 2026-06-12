---
title: "Ubuntu 17.10 archiver doesn't have password abilities"
date: 2017-12-18
forum: General Help
---

### Post by toxbuntyuser on 2017-12-18
How do I get to use .7z files to be password protected?

Ubuntu 17.10 doesn't seem to allow to have rar compression as an option

---

### Post by howefield on 2017-12-18
What do you see in the *"Other Options"* field ?

You can install rar and unrar if you want to use that format.

```
sudo apt install rar unrar
```

---

### Post by toxbuntyuser on 2017-12-18
I have tried that, but it doesn't work
[IMG]http://i64.tinypic.com/2vla1ar.jpg[/IMG]

---

### Post by ajgreeny on 2017-12-18
Which p7zip packages have you installed at the moment?

---

### Post by toxbuntyuser on 2017-12-18
Basically all of the ones I need, like 7z and rar/unrar

---

### Post by howefield on 2017-12-18
If you don't have a dialogue window like the above with the password field in it for .7z you could try installing p7zip-full.

---

### Post by toxbuntyuser on 2017-12-18
> **howefield said:**
> If you don't have a dialogue window like the above with the password field in it for .7z you could try installing p7zip-full.


The thing is, I have already installed p7zip-full already, yet I still don't get the proper dialogue box like the one you posted

---

### Post by howefield on 2017-12-18
Try creating the archive slightly differently, are you right clicking on the file(s) and selecting compress ?

Instead of that, try opening the Archive Manager application and create the compressed file from there, you should be able to drop the files into the archive manager application window and be asked if you want to create a new archive, from there you should be able to select the compression format, archive name and a drop down option for "*Other Options*" above.

---

### Post by toxbuntyuser on 2017-12-18
When I tried to open this link it says that the manager already exists
[https://apps.ubuntu.com/cat/applications/file-roller/](https://apps.ubuntu.com/cat/applications/file-roller/)

I found the software, but I am unable to launch it for some reason

---

### Post by raleigh3 on 2017-12-18
Peazip lets you create pw archives.

---

### Post by mc4man on 2017-12-18
> **toxbuntyuser said:**
> When I tried to open this link it says that the manager already exists
[https://apps.ubuntu.com/cat/applications/file-roller/](https://apps.ubuntu.com/cat/applications/file-roller/)

I found the software, but I am unable to launch it for some reason

Just click on that 9 dot icon on launcher or click on Activities & search either file-roller or archive manager (you won't need to actually type out completely.
Then click on "Archive Manager" & go from there

If that doesn't work for some odd reason then open a terminal & run this
file-roller

The only thing that changed in 17.10 is the nautilus extension has been dumbed down to only offer 3 compressions with no options (as you've seen..

---

### Post by toxbuntyuser on 2017-12-19
OK, thanks, a bit arduous to create pw archives, but at least it "fixes" the temporary solution

---

