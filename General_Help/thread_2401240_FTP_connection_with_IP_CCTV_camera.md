---
title: "FTP connection with IP CCTV camera"
date: 2018-09-15
forum: General Help
---

### Post by septekin on 2018-09-15
Hello all,
There must be lots of people using security cameras connected via Ubuntu.
I just cannot make use of the ftp system to record images. I've tried two cameras and two Ubuntu versions with the same failing.
My details:
Camera:      SV3C  or:  IeGeek
Ubuntu:       18.04
vsftpd installed & /etc/vsftpd.conf edited.
Command line: ftp localhost 21 results in: 230 login successful.
The camera's video is visible in real time in its web page.
In SV3C's web page 192.168.8.109, under Parameters > Network > FTP I've tried several Server, Port, User, Password and Path combinations, all resulting in Test: Login failed!
Would someone please let me know what I need to do to get the camera(s) working?
Many thanks in advance,
teoman

---

### Post by him610 on 2018-09-15
You may be able to get some ideas from the Raspberry Pi community at these links ....
[https://www.raspberrypi.org/forums/viewforum.php?f=43](https://www.raspberrypi.org/forums/viewforum.php?f=43)
[https://raspberrypi.stackexchange.com/questions/23182/how-to-stream-video-from-raspberry-pi-camera-and-watch-it-live/32521#32521]("https://raspberrypi.stackexchange.com/questions/23182/how-to-stream-video-from-raspberry-pi-camera-and-watch-it-live/32521#32521")

FWIW, if you are really running Ubuntu 12.04 or 10.04, you need to update to a more recent distro - 16.04 or 18.04.

---

### Post by septekin on 2018-09-16
him610:
Thanks for your reply and pointing out my bad signature which I've corrected.
Tried the raspberry references, nothing relevant to my problem.
Thank you again.
teoman

---

### Post by HermanAB on 2018-09-16
Err... Which device is running the server and which is the client?

You also have to ensure that there are no firewall rules tossing the packets away.

Don't poke around in the dark - see what is going on/or not, with tcpdump or wireshark.

---

