---
title: "Ubuntu, Lubuntu 13.04 Non-pae"
date: 2013-04-09
forum: General Help
---

### Post by Redalien0304 on 2013-04-09
Anyone know of ANY Raring 13.04 Ubuntu Lubuntu Non-Pae ISO's? I have tried Lubuntu 13.04 but it want pae support thought LUbuntu didnt Require PAE support??
I have installed 12.04 Non-Pae version of Ubuntu then did Dstribution upgrade to 12.10 then Distrubtion upgrade 13.04 but obviously is PAIN. I NEED a Non-Pae version of 13.04 please.

Have 12.04 Non-Pae installed on a Dell Latitude D600 now W/ 2Gb ram.

---

### Post by mörgæs on 2013-04-10
Only PAE releases are available in 13.04 (and 12.10), but you could try [Fake-PAE]("http://ubuntuforums.org/showthread.php?t=2113826").

---

### Post by jerrylamos on 2013-04-10
My Thinkpad T40 is stuck on 12.04 Pangolin Unity 2D Lubuntu because of the PAE issue.
To upgrade I boutght a $199 Acer C710 Chromebook thinking I could put ubuntu on it.  Only directions I found on the forums were for 12.04 Chrubuntu so nothing gained.
BTW, Chromebook is so fast, easy, and convenient compared to unity I'm keeping it as is, no ubuntu, until/if there is some other method of ubuntu install supporting the fast video display accelerator.

---

### Post by mörgæs on 2013-04-10
Did you read about Fake-PAE before declaring yourself stuck?

---

### Post by Redalien0304 on 2013-04-10
I tried Lubuntu 13.04 beta 2 it requires pae. i have tried the Fake pae 1 time. i will try it again. Gonna try Xubuntu 12.10

Update Lubuntu Xubuntu 12.10 both want a Pae kernel?? Thought they were supposed to be Non-Pae??

---

### Post by mörgæs on 2013-04-10
> **alien0304 said:**
> Update Lubuntu Xubuntu 12.10 both want a Pae kernel?? Thought they were supposed to be Non-Pae??

Please see post #2.

---

### Post by Redalien0304 on 2013-04-12
I tried the Fake-Pae works but slow on Ubuntu 12.10 & 13.03. Mainly looking for Non-Pae version of raring 13.04 (yes i know it is only Pae). There has to be a way to replace the kernel on Live Cd or Usb. I did find a way to install 12.10 via bootable Usb here: [http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html). Gonna try it with 13.04 & see what happens.

---

### Post by kevashcraft on 2013-04-28
Thanks for the info! :KS

Just installed 13.04 on a non-pae CPU =)

_**Path:**_
-Install Xubuntu 12.04 Alternate (because I like the full-disk encryption and wasn't sure if the desktop release yet had that option and was quite tired of downloading different releases.. anyway, digressing...)
-Install fake-pae ```
sudo apt-add-repository ppa:prof7bit/fake-pae && sudo apt-get update && sudo apt-get install fake-pae
```
-Reboot (because when unsure, sudo reboot)
-Upgrade to Xubuntu 12.10 ```
update-manager -d
```
-Upgrade to Xubuntu 13.04 
-Recant tale to lessen others woes and appease my rambling soul

---

### Post by mörgæs on 2013-04-29
Good, please spread the word :-)

---

### Post by alanhoyle on 2013-06-05
I installed Lubuntu 12.04 via the mini.iso on my ancient Thinkpad X40, and had to install an additional command line tool in order to follow the instructions to add the PPA for fake-pae. 

Depending on the specific distribution, you may need to install python-software-properties or software-properties-common in order to have the apt-add-repository command available at the command line. 

On my 12.04 install, I needed to run:

    sudo apt-get install python-software-properties

Apparently on later versions like 12.10, the package is:

    sudo apt-get install software-properties-common

I wanted to post this as a follow-up in the thread, but something about the ubuntuforums configuration prevents me from doing so.

---

### Post by mörgæs on 2013-06-05
I gathered some advice here: 
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Feel free to fill in, if something is missing.

---

### Post by cariboo on 2013-06-05
Seeing as we are supposed be discussing the usage of Saucy in this sub-forum, and the non-pae kernel isn't an issue here, moved to General Help.

---

### Post by neu5eeCh on 2013-06-16
Just ran into this problem. Lubuntu has got to get its act together. It's just silly. They might as well just tout themselves as the-lightweight-OS-for-old-computers-that-you-can't-install. It's just stupid. Sorry. If they can't offer a version of Lubuntu without PAE, then who needs the hassle? Guess I'll be using Crunchbang.

---

### Post by neu5eeCh on 2013-06-24
I've found two distros that offer non-PAE Ubuntu respins. There may be more. Bodhi and Puppy. Bodhi is easy enough to find, and Puppy can be found [here]("http://www.bkhome.org/blog/?viewDetailed=03066"). I don't think either are 13.04, but there may be an upgrade path once either of these are installed.

---

