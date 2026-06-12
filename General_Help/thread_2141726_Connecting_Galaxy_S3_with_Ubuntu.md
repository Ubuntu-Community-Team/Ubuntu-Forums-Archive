---
title: "Connecting Galaxy S3 with Ubuntu"
date: 2013-05-03
forum: General Help
---

### Post by wadie on 2013-05-03
Hi,

I plug my S3 to my PC which is running latest version of Ubuntu and for  some reason I can't view or move files from or to the phone.

Any ideas?

---

### Post by Toz on 2013-05-03
[This]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html") works for my daughter with her S3 on Ubuntu 12.10. The only caveat we have run into is if the S3 locks, the connection is lost. So need to keep it unlocked while transfering files.

---

### Post by efflandt on 2013-05-03
I have not tried **go-mtpfs** yet, but the regular mtp  related suggestions or methods did not seem to work in 12.04 for my S3.  If the phone is set to MTP, in the file manager (nautilus?) I only see  the root of the phone storage and microSD (anything under that appears  empty). If I set the phone to camera (PTP?, I forgot my phone at work  this noon), the file manager shows files on the phone's internal  storate, but nothing on the microSD. **ConnectBot** is also  a useful Android app to ssh to Ubuntu (or my NetBSD shell account on  the internet), although, it helps to set the font in the ConnectBot  settings a bit larger.

So on the phone I have either been using **AndFTP** app to sftp to Ubuntu, or **SSH Server**  app on the phone to sftp to the phone from Ubuntu. I use my Linux  openssh keys for either (I have ssh password login disabled in Ubuntu).  That also works between phone and Raspberry Pi (a credit card size ARM  computer that runs a Debian wheezy version called Raspbian).

One other useful phone app for wireless LAN if your Ubuntu does not have a static IP is **ZeroConf Browser**.  By default Ubuntu has avahi-daemon installed (which I also installed on  the Raspberry Pi, which has a dynamic IP) to find IP addresses of  hostnames, although, from Linux they are found by hostname**.local**.  You cannot find your phone that way (check its IP address in its  settings), but you could find Ubuntu from your phone. Zeroconfig is an  Apple thing, which avahi can do in Linux, and Apple has a related  Bonjour program for Windows.

---

### Post by wadie on 2013-05-04
oh thanks guys :)

---

### Post by SeijiSensei on 2013-05-04
One reason I upgraded from Kubuntu 12.04 LTS to 13.04 was because it was supposed to have better support for the MTP protocol, and it does!  When I plug my S3 in, it is now recognized as both a camera and a media device.  i can copy files to and from the phone directly now, when I could not do so in 12.04.

I believe similar improvements were included with vanilla Ubuntu 13.04 as well.

---

