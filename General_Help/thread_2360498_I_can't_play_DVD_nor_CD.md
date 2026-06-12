---
title: "I can't play DVD nor CD"
date: 2017-05-05
forum: General Help
---

### Post by Jonatan Formentera on 2017-05-05
Hi, I have Ubuntu 16.04. When I try to play a DVD or a CD the following appears: 

¨Unable to mount Blank CD-R¨Even though the CD is not blank. It's a commercial DVD with music
This also appears:
Your input can't not be opened
VLC is unable to open the MRL 'Burn:///'

I downloaded several players and codex but it doesn't work
Can someone help me?
Thanks

---

### Post by Autodave on 2017-05-05
Sorry, but I have to ask: Are you sure that the CD player/burner is good? Do you have an external one that you could try?

---

### Post by speartip on 2017-05-05
Your 1st screenshot is a common bug that Ubuntu's had for years. Just close the top box.
A couple of things. Make sure vlc is trying to open the correct location. /dev/cdrom or /dev/sr0 are the common locations.
Also do you have libdvdcss installed?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Jonatan Formentera on 2017-05-05
I think the DVD player/burner works. With other OS it does. I installed 
sudo apt-get install libdvd-pkg but it doesn't work

---

### Post by speartip on 2017-05-05
As long as your online it shouldn't be a problem.
Try:
```
sudo apt update && sudo apt install libdvd-pkg
```
Also as it installs it asks you to run another command. Make sure you copy that & run it at the end.

---

### Post by Jonatan Formentera on 2017-05-05
Now I can play just DVD but not with VLC, and only with video player. I can't play a cd. I don't know. Perhaps is the player/burner. I'll prove with an external one
Thanks

---

### Post by speartip on 2017-05-05
If it plays with video player, it should play with VLC.
When you open VLC, go to Media, Open Disc, & make sure it is searching for the Disc Device in the right place.
If your not sure, check where video player is looking.

---

