---
title: "Setting file permissions within folders"
date: 2007-02-12
forum: General Help
---

### Post by _jj on 2007-02-12
In the process of moving to Ubuntu from Windows I have transferred my music collection (mainly mp3s).  The permission of these files is set as Read Only.  In order to be able to change tags I need it to be read and write.  I have worked out how to do this to all the songs in an individual folder (sudo chmod u=rwx *.mp3) but I have is a separate folder for each artist and then within each artists folder a seperate folder for each album.

Is there anyway to apply a change of permission to for example all of the mp3 files in all of the folders within my music folder?
I am sorry if this is a bit of a newbie question!
thanks for the help

---

### Post by gh0st on 2007-02-12
I may be wrong here as I'm not an expert but if you just right-click your main music folder in Nautilus (file explorer), select properties and go to the permissions tab, you can set the permissions there and click the button at the bottom that says "apply permissons to enclosed files". I think that might work.

I have to be honest though I haven't tried it myself with a large amount of sub folders, it's only a suggestion. I apologize if it doesn't work for you, someone more qualified will no doubt be along to help you shortly :) 

Let me know if it works. Good luck.

---

### Post by _jj on 2007-02-12
Thanks a lot that has sorted it.  However if anyone knows how to do this in a Terminal or for example only to certain types files within the folders I would love to know.

---

### Post by TyphoonJoe on 2007-02-12
> Is there anyway to apply a change of permission to for example all of the mp3 files in all of the folders within my music folder?

You are in luck, as you can easily do this from the command line.  Move to the base directory for your mp3 files, such as /media/music/ and run:

```
sudo chmod -R u=rw *.mp3
```

You were so very close with your example ;)  The "-R" makes the command recursive, and I took off the "x" bit as mp3 files are not executable. 

Good luck.

---

### Post by FlashDragon on 2007-02-20
I tried to do this with some files & folders I brought in from a Windows machine. I don't have the  "apply permissons to enclosed files" option on the perrmissions tab. 

I have a whole bunch of subfolders & files that need to have their permissions changed. I can open the files as "root" and as the designated user but I can't change the permissions en masse, They have to be done folder by folder, working down the tree. 

Is there a way to get that "apply permissons to enclosed files" option to appear & fucntion?

Thanks,

Pete

---

