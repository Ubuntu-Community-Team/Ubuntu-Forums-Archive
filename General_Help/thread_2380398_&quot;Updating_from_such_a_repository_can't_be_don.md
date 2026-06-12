---
title: "&quot;Updating from such a repository can't be done securely&quot;"
date: 2017-12-16
forum: General Help
---

### Post by Kymus on 2017-12-16
I'm running a fresh install of 17.10 and when I try to apt-get update, I'm getting this (and I think it's keeping me from installing other software -_-). 

```
kymus@Sanxing:~$ sudo apt-get update
Get:1 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]                                                                  
Ign:2 http://ppa.launchpad.net/deluge-team/ppa/ubuntu artful InRelease                                                               
Hit:3 http://us.archive.ubuntu.com/ubuntu artful InRelease                                                                                                      
Hit:4 http://repo.steampowered.com/steam precise InRelease                                                                                                      
Get:5 http://us.archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]                                                                              
Hit:6 http://ppa.launchpad.net/diodon-team/stable/ubuntu artful InRelease                                             
Get:7 http://us.archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]                                                                    
Hit:8 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu artful InRelease                
Ign:9 http://ppa.launchpad.net/wine/wine-builds/ubuntu artful InRelease                                         
Err:10 http://ppa.launchpad.net/deluge-team/ppa/ubuntu artful Release
  404  Not Found
Err:11 http://ppa.launchpad.net/wine/wine-builds/ubuntu artful Release
  404  Not Found
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/deluge-team/ppa/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/wine/wine-builds/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I'm not sure what the 404 is about with connecting to launchpad, either. I have tried switching servers, but haven't had any luck (unless there's something obvious I'm missing, which could very well be the case)

---

### Post by deadflowr on 2017-12-16
Dead PPAs
Remove them (or disable them)

The deluge-team ppa only goes up to Ubuntu 17.04, so no packages built for 17.10.
and the wine-builds ppa is obsolete.

Unfortunately i know nothing about how to deal with the deluge situation in terms of installing any updated version ( I see the repos have a version; a version being probably well past it's prime, for whatever release it would be for),
but good news is you can add the wine repo by following the guide here:
[https://wiki.winehq.org/Ubuntu]("https://wiki.winehq.org/Ubuntu")

---

### Post by Kymus on 2017-12-17
Thanks! Things are running smoother now. 

For future reference, there isn't some magical way to use an old ppa source is there? Like in an instance such as this using 17.04 instead of 17.10?

edit: for stuff that's troublesome, I've just googled (software name) ubuntu 17.10 and that has helped. Deluge seems to work despite the ppa issue :)

---

### Post by oldos2er on 2017-12-17
You could compile from source, or contact the owner of the PPA to ask if it's going to be supported in the future.

---

