---
title: "A few questions.."
date: 2008-05-25
forum: General Help
---

### Post by Depth on 2008-05-25
Installed Ubuntu for a while ago and i got a few questions .

1. I have a creative SB X-fi gamer soundcard and i cant seem to find any drivers for this one leaving me without sound

2. My pc makes an awful lot of sound so in windows i used Speedfan to turn down the fan speeds, is there something like this for Linux? Because the sound is horrible.

3.Is there a easy-newbish way to move files (movies,music and such) from Windows to Ubuntu?

All the questions i got at the moment :)

---

### Post by Prospero2006 on 2008-05-25
> **Depth said:**
> Installed Ubuntu for a while ago and i got a few questions .

1. I have a creative SB X-fi gamer soundcard and i cant seem to find any drivers for this one leaving me without sound

2. My pc makes an awful lot of sound so in windows i used Speedfan to turn down the fan speeds, is there something like this for Linux? Because the sound is horrible.

3.Is there a easy-newbish way to move files (movies,music and such) from Windows to Ubuntu?

All the questions i got at the moment :)

Question 1: X-Fi Sound:
    -I played around with an X-FI card about 6 months ago, and at that time, there was no support on Linux. If the support isn't there now, I would imagine it is around the corner.
Question 2:
     Fan speed: lm_sensors may be something to look into.
I'm not an expert with lm_sensors, but it's a good starting point maybe.
Question 3:
    Moving files from Windows to Ubuntu:
             -This one is easy. I use a Linux machine as my primary file
server on several networks. It shares all of the files for the network and Linux and Windows machines both can access everything from these central storage points. 
            -You have to install samba. (sudo apt-get install samba)
            -Then you have to go in and edit /etc/samba/smb.conf
                    -Getting acquainted with this file takes a little
                     time, but it's well documented.
            -Once you have Samba running correctly on the network,
             your windows machines will recognize it as a network
             computer and you will be able to transfer files to 
             and from the Ubuntu machine.

---

