---
title: "Failed to start the X servers Plz help"
date: 2007-09-16
forum: General Help
---

### Post by Matt D on 2007-09-16
I booted into Ubuntu feisty fawn today and the Ubuntu boot screen loaded like usual but instead of going into the Ubuntu login screen i got a error message saying Failed to start the X server (your Graphical interface) It is likely that this is not set up correctly would you like to view the X server out put to diagnose the problem. It took me to a blue screen with some system information or some thing like that on it. I then went to a none GUI login were  was able to use the command line.
Can some help me with my problem it also told me to 
visit wiki.x.org if that is any help to you.






Thx Matt

---

### Post by reckless2k2 on 2007-09-16
can we assume that you had a working install previously? have you installed new drivers/software would have contributed to this like compiz or nvidia/ati drivers?

---

### Post by Matt D on 2007-09-16
Yes it was working yesterday it was just today it happend

---

### Post by reckless2k2 on 2007-09-17
did you recently add proprietary video drivers or compiz/beryl..etc?

this can usually be fixed with editing the zorg.conf file. depending on what might've been done, there might be a backup already there that can just be copied back and restart without issue.

---

### Post by Matt D on 2007-09-17
Yes i tried to install Beryl restarted Linux and that was when it happend

---

### Post by reckless2k2 on 2007-09-17
ok...that's helpful. did you backup the xorg.conf file prior to editing it or did you do any editing at all? 

you may be able to just remove beryl from apt-get and be alright. from the terminal/command prompt:

sudo apt-get remove beryl


if you tweaked the file with certain settings, restore you backup file. did you make a backup?

---

### Post by Matt D on 2007-09-17
No I didn't back up my files I tried the sudo apt-get remove beryl but it didn't work

---

### Post by Wellig on 2007-09-17
I have the same problem. I made a backup, but I don't know how to restore the old file with the backupped one.

---

### Post by reckless2k2 on 2007-09-17
Matt D - did you modify the xorg.conf file at all? i'll need that answer. also, post the results of your xorg.conf file. 

Wellig - boot into recovery mode and navigate to the X11 folder

```
#cd /etc/X11
```

now type 

```
#ls
```

this should display the current xorg.conf file along with your backup IF you saved it there. i assume you did. it might be named xorg.conf.bak...i don't know. if that was the file name you just copy it back like this

```
#sudo cp xorg.conf.bak xorg.conf
```

if cp doesn't work try mv like this

```
#sudo mv xorg.conf.bak xorg.conf
```

upon reboot you will be back to the old settings. then you can play around and break it again. haha

cp = copy
mv = move/rename

---

### Post by Matt D on 2007-09-17
NO i don't think so 


I followed these steps in installing beryl here if it helps 

[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

---

### Post by reckless2k2 on 2007-09-17
ok...i assume you have a nvidia card then? just reverse your xorg edit like this:

```
sudo nano /etc/X11/xorg.conf
```

change it back to this:

```
Section "Device"
Identifier- leave this line alone!
Driver "nv”
BusID “PCI:1:0:0&#8243;
EndSection

```


Reboot and you will be back to using the nv driver which you should be alright. obviously all of this you are doing in recovery mode i imagine.

---

### Post by Matt D on 2007-09-18
It didn't work in recovery mode it couldn't find the files
so i tried it by booting it up normally so i put in sudo nano /etc/x11/xorg.conf

and i put in the other bit but nothing happened  what do i do then

---

### Post by Wellig on 2007-09-18
Thank you, worked well. Now I'm going to play around again ;).
Good luck to you Matt D with solving your problem

---

### Post by reckless2k2 on 2007-09-18
not being able to find the files in recovery mode sounds a little odd. could you please post the results of the following from the terminal:

```
sudo ls -l /etc/X11
```

also, when you are "normal" booting are you getting into the normal desktop or what is going on?

and the question about nvidia has still not been answered.

please post the results from the following as well from the terminal:

```
sudo lspci -v
```

---

### Post by Matt D on 2007-09-18
When i do a normal boot it boots up with the Ubuntu boot screen but then it goes to a blank screen and it looks like a command line OS instead of a GUI it then asks me for my user name and password and then i can just use the terminal were i can type in commands its just all text on a black screen no GUI

---

### Post by reckless2k2 on 2007-09-18
considering your issues and failure to answer certain questions specific to your PC, i'd suggest a clean install if nothing terribly valuable is on there. 

in the future, review the specs more closely of you pc such as knowing the chipset and or model of you video card and monitor specs. i would shy away from volatile projects such as beryl or compiz until a better understanding of your hardware is achieved. 

also, before editing any file, copy it to a backup first so you can restore the backup if something blows up. i can't tell you how many times in my early linux years that i regretted not doing that. in my early years as well, i had terrible problems with xorg and it scared me away many times. the best thing i could've done is backed up before i messed around with it. 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

good luck. let us know how everything goes.

---

### Post by Matt D on 2007-09-22
I fixed the problem now and Ubuntu is working fine all i did was run the live disk and copy the xorg.conf file off the disk and accessed my Linux file system in vista and replaced the file i would of done it n the live disk but i didn't have the permission to edit the file when i was on the live disk thanks for you help

---

### Post by reckless2k2 on 2007-09-22
no problem. i'm glad everything worked out for the best.

---

