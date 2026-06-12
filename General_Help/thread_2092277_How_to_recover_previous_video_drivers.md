---
title: "How to recover previous video drivers?"
date: 2012-12-07
forum: General Help
---

### Post by szuwarek22212 on 2012-12-07
I have installed video drivers, but after that my screen has a lower resolution and I cannot see the left panel - I'm using ubuntu 12.10

I want to go back to my previous drivers (default ones).

I have a laptop, my gpu is mobility radeon 9700 128m MB. I have downloaded the drivers through ati website.

Please help!

---

### Post by elliotn on 2012-12-07
```
 $ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
 sudo apt-get install xserver-xorg-video-ati 
 
```

u must also remove fglrx

---

### Post by Mark Phelps on 2012-12-07
I don't know what you installed, but there are no current AMD Linux drivers that will work with your card and Ubuntu 12.10 because those all work with an older version of X-server than is present in 12.10.

I'm asking this because there is a thread that has been posted for folks to run a script to FORCE the install of restricted AMD drivers in Ubuntu 12.10 -- and since it DOWNGRADES the X-server, it is a BAD idea to do that.  Plus, I think those drivers wouldn't work with your card, either -- since it was relegated to legacy status years ago.

In general, the way to remove the fglrx drives is to follow the instructions in the linked information:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by szuwarek22212 on 2012-12-21
Those commands didn't work. Help!!!

---

### Post by QIII on 2012-12-21
If you installed using the instructions directly from the ATI website, you will have to use the amdconfig (formerly aticonfig) utility.

```
sudo amdconfig --uninstall
```

If that does not work, try 

```
sudo aticonfig --uninstall
```

You can't uninstall it with apt because it has no clue that it exists.

---

