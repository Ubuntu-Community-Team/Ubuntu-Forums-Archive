---
title: "Getting error message when trying to install software"
date: 2018-09-19
forum: General Help
---

### Post by runion on 2018-09-19
I am running a LENOVO M91P, with 12G ram, and intel I7-2600.

I have xUbuntu 18.04.1

I am not a tech type but I get along comfortably with Ubuntu/Linux op systems usually.  
Since I have not seen any other complaints on this particular problem, it must be something
with my software.

When I try to install software, I am getting the following error.



Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libavcodec-extra libavcodec-extra57 libavutil55 libswresample2
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/


the 18.04.1 is new to me and I have just installed it to try it out.  I have a couple of programs that I 
run but this error is stoping me.

Thanks for any ideas....

180919 0532

---

### Post by Impavidus on 2018-09-19
Make sure all other programs using the package manager are closed. That includes Ubuntu Software, synaptic, apt, update manager (which may run automatically in the background). Also make sure you're running this command as root, i.e., use sudo:```
sudo apt install ...
```

---

### Post by runion on 2018-09-19
I just checked, and I used that every time.  I don't see anything running, I'm thinking it may be possible for something to be missing.



&#9492;&#9472; $ &#9654; sudo apt-get install clipgrab
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libavcodec-extra libavcodec-extra57 libavutil55 libswresample2
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

---

