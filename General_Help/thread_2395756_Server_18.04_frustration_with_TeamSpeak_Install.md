---
title: "Server 18.04 frustration with TeamSpeak Install"
date: 2018-07-06
forum: General Help
---

### Post by jpin321 on 2018-07-06
Would someone mind looking through the below thread and letting me know what is happening?  I've installed Teamspeak for years on ubuntu server countless versions without issue. This time? Nope giant PITA no idea what i'm doing wrong but I think it's related to 18.04. No idea why it keeps having trouble seeing the files keep getting "not found" yet ls shows it. 

[https://forum.teamspeak.com/threads/136323-Instructions-for-Ubuntu-Server-18-04-installation?p=458690#post458690](https://forum.teamspeak.com/threads/136323-Instructions-for-Ubuntu-Server-18-04-installation?p=458690#post458690)

---

### Post by #&amp;thj^% on 2018-07-06
There was no information as to your method used to install Teamviewer but the way "I" do it may not be disireable for you. {So kindly keep that in mind}
Mine went as follows:
```
git clone https://github.com/Dh0mp5eur/TeamSpeak3-Client.git
```
Then I CD into the newly cloned git folder, and execute the build tool to generate a new package.
```
cd TeamSpeak3-Client
```
and then run:
```
sh package .sh
```
This Package.sh will build both a 64bit and 32bit DEB package for Debian. Currently, the package works perfectly with Debian Stable (Stretch) and newer.
I also needed these to be installed for mine.(Depends)
```
Suggested packages:
  clang srtp-utils
The following NEW packages will be installed:
  libc++1 libc++abi1 libqt5sql5 libqt5sql5-sqlite libsrtp0

```
From there you can use Gdebi or use dkg to install:
I used:
```
sudo dpkg -i teamspeak3-client_amd64.deb
```
Also I have seen on some systems where "-f install" was needed.
```
 sudo apt -f install
```
**EASIEST METHOD:**There is also a PPA if you prefer which is the easiest way:
Shown here: [https://www.osradar.com/how-to-install-teamspeak-on-linux/](https://www.osradar.com/how-to-install-teamspeak-on-linux/)
```
sudo add-apt-repository ppa:materieller/teamspeak3
```
followed with 
```
sudo apt update
```
and then:
```
sudo apt install teamspeak3-client
```
Good Luck

---

