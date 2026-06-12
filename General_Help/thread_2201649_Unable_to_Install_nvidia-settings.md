---
title: "Unable to Install nvidia-settings"
date: 2014-01-25
forum: General Help
---

### Post by John_Gu on 2014-01-25
Hello,

I am trying to install nvidia-settings on Ubuntu 12.04.  This is a fresh install done today (Jan 25, 2014).  I have nvidia-331 installed (I believe it's 331.38, but don't think the exact version matters here).  

```

johngu@Guru-Laptop:~/Downloads$ sudo apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-settings : Depends: screen-resolution-extra (>= 0.14ubuntu2.1) but 0.14ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.


johngu@Guru-Laptop:~/Downloads$ sudo apt-get install screen-resolution-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
screen-resolution-extra is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1 thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any help here would be appreciated.  I just want to have access to the nvidia control panel.

---

### Post by jeanjd63 on 2014-01-25
Hello 
You can try download and install :

```
**wget  http://security.ubuntu.com/ubuntu/pool/main/s/screen-resolution-extra/screen-resolution-extra_0.14ubuntu2.1_all.deb**
```[B]
sudo  dpkg  -i  [/B][B]screen-resolution-extra_0.14ubuntu2.1_all.deb

[/B]and then :[B]

sudo  apt-get  install -f
sudo  apt-get  install  nvidia-settings[/B]

---

### Post by Frogs Hair on 2014-01-25
If am thinking of the same application it has always been installed along with the driver on my desktop. Open additional drivers and see if the driver is activated.

---

### Post by deadflowr on 2014-01-25
After doing the additional; drivers check, I would recommend running the "fix broken packages" command
```
sudo apt-get -f install
```
Please run it as is, nothing more (like apt-get -f install gnome, or something)

---

### Post by John_Gu on 2014-01-25
Thanks!  This solved the issue.  May I asked how you found this file?  I was searching on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for the package for precise.  I found 0.14ubuntu2 ([http://packages.ubuntu.com/precise/screen-resolution-extra](http://packages.ubuntu.com/precise/screen-resolution-extra)) but not 0.14ubuntu2.1.  Would love to learn to fish as well.

---

### Post by jeanjd63 on 2014-01-25
I have search [screen-resolution-extra precise]("https://www.google.fr/search?client=safari&rls=en&q=screen-resolution-extra&ie=UTF-8&oe=UTF-8&gws_rd=cr&ei=NOrjUqCrB8qO0AXAiYDgDQ#q=screen-resolution-extra+precise&rls=en") in google and it was found on the forth line. Thats all folk.

---

### Post by philinux on 2014-01-25
> **Frogs Hair said:**
> If am thinking of the same application it has always been installed along with the driver on my desktop. Open additional drivers and see if the driver is activated.

If I type in a terminal nvidia-settings it brings up the familar screen. However package nvidia-settings is not installed.

It must be part of the nvidia driver.

[edit] a quick trip with synaptic solved it. I have nvidia-settings-319 installed. Which is a recommended package for nvidia-319.

---

