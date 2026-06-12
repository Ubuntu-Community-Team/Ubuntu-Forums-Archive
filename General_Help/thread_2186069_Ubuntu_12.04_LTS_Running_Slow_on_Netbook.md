---
title: "Ubuntu 12.04 LTS Running Slow on Netbook"
date: 2013-11-05
forum: General Help
---

### Post by AdHoc92 on 2013-11-05
I just installed Ubuntu 12.04 LTS on my netbook and it's running slower than I thought it would- I assumed it would be fine since the Netbook version of Ubuntu merged with the Desktop version. Once applications are opened, they usually run fine, but it takes 6+ seconds to open most applications, and it freezes up when trying to run more than one thing at a time. 

I know I shouldn't expect much from a netbook, but it works better with Win 7 than Ubuntu, which is ridiculous. Does anyone have any ideas on how I can make it run faster? 

Specs: 
-Intel Atom N455
-1GB memory
-Intel Graphics Media Accelrator 3150

Notes: 
-It's installed within Win 7 as Dual-Boot
-In System Settings > Details OS Type is 64 Bit, which I'm assuming is a problem. I have no idea why it says that because I made sure to download the 32 bit version.

On an unrelated note, how do I change my username? Right now it's my E-mail and I don't feel like getting murdered.

---

### Post by TheFu on 2013-11-05
Load a lighter DE - like XFCE or LXDE, then use that instead of Unity. You will see a huge difference.

To change your username - 
* modify /etc/passwd - change username and HOME directory
* modify /etc/shadow - change username a 
* modify /etc/group - change all references to the old username
* move the HOME directory to match the new username
* logout/login

If you make a mistake, you could be screwed, so be certain to have a liveCD ready and backups of the passwd/group/shadow files AND know how to put them back.  If not, some root-fu will be needed.

If there is any encryption involved - I do not know if this stuff works or not. Make a 100% backup before beginning.

---

### Post by Old_Grey_Wolf on 2013-11-05
I agree with TheFu about XFCE and LXDE. You may just what to install Xubuntu or Lubuntu.

I have the same N455 CPU in my netbook, and 6+ seconds to load an application is about what I get using Ubuntu 12.04 with the Unity DE.

---

### Post by AdHoc92 on 2013-11-05
-Snip-

---

### Post by AdHoc92 on 2013-11-05
I actually tried to install the Xubuntu, but instead of the ISO opening like normal, it would just open up a window saying "Import Pictures and Video". I have no idea why it's doing that, and I've never had the problem before. The Ubuntu ISO worked fine. 

I guess I'll take TheFu's advice. If that doesn't work, I'll try to install Xubuntu again. 

As for chaning my username, I think TheFu thought I meant on Ubuntu. I'm wondering how to change my username on these forums. It won't let me. It says I have to post more or something.

---

### Post by Old_Grey_Wolf on 2013-11-05
> **connor.george.spen said:**
> On an unrelated note, how do I change my username? Right now it's my E-mail and I don't feel like getting murdered.

Are you referring to the username on the computer or the Ubuntu Forum?

---

### Post by TheFu on 2013-11-05
> **Old_Grey_Wolf said:**
> I agree with TheFu about XFCE and LXDE. You may just what to install Xubuntu or Lubuntu.

I have the same N455 CPU in my netbook, and 6+ seconds to load an application is about what I get using Ubuntu 12.04 with the Unity DE.

I'm using a netbook with a N280 CPU and LXDE on ubuntu server (don't ask).  Some apps take long to open ... firefox/thunderbird bloatware, but most others open very quickly even with encryption enabled - under 2 sec.

The key is to avoid Unity ... er .... always, regardless of CPU, RAM, SSD. ;)  If you enjoy the side-bar, setting something up like that under LXDE is relatively easy. It won't be as "smart", but Grandma doesn't care. My 80+ yr old Mom didn't.

---

### Post by Old_Grey_Wolf on 2013-11-05
> **connor.george.spen said:**
> I'm wondering how to change my username on these forums. It won't let me. It says I have to post more or something.

Post a request to change your Ubuntu Forums username in the Resolution Center at [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by Old_Grey_Wolf on 2013-11-05
> **TheFu said:**
> If you enjoy the side-bar, setting something up like that under LXDE is relatively easy. It won't be as "smart", but Grandma doesn't care. My 80+ yr old Mom didn't.

Be careful, you may offend some of **us** Grandma's and Grandpa's on the forum that actually are the family geek. 

:lolflag:

---

### Post by AdHoc92 on 2013-11-06
I ended up just installing Lubuntu and it works great. Thanks for the help, guys.

---

