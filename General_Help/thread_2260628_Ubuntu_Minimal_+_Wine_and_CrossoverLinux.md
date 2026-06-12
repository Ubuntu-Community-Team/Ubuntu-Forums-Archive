---
title: "Ubuntu Minimal + Wine and CrossoverLinux"
date: 2015-01-13
forum: General Help
---

### Post by Stan_1936 on 2015-01-13
Hi, I am looking to install the minimal version of Ubuntu 14.04. Then I would like to install Wine and CrossOverLinux - I do not want to install any other packages. With this in mind, I have decided to install the following:
a. a minimal Ubuntu 14.04 system
b. graphical user environment (LXDE, LXDM)
c. Wine and CrossoverLinux

I will be using the following to install the necessary packages, but I am quite poor at the Linux command line and aI have never worked with Ubuntu Mini before, so I am looking for some help with this:

**_Install Xorg, LXDE window manager with LXDM as the login manager and firefox web-browser:_**
```
sudo apt-get install lxde xorg lxdm firefox
```

**_Install Geany editor:_**
```
sudo add-apt-repository ppa:geany-dev/ppa
sudo apt-get update
sudo apt-get install geany geany-plugins
```

**_For WINE:_**
1. **Add PPA:** ```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
2. **Update APT package information:** ```
sudo apt-get update
```
3. **Install Wine:** ```
sudo apt-get install wine1.7
```

**_For CROSSOVER:_**
**Install following packages:**
```
sudo apt-get install libglade2-0 python-glade2
```

**Download crossover from here to Downloads folder:**
[https://www.codeweavers.com/products/crossover-linux/download/](https://www.codeweavers.com/products/crossover-linux/download/)

**Navigate to Downloads folder:**
```
cd Downloads
```

**Install CrossOver:**
```
sudo dpkg -i crossover_11.3.1-1_i386.deb        #the exact name/numbers may be different
```

**Additional Information (If Required):**
After installing Wine and Crossover, I will be installing an old Windows program in each of time. The program comes as a *.exe file.
The PC is 32-bit.
The Ubuntu mini ISO is the 32-bit ISO file.

[SIZE=3]**QUESTIONS:**[/SIZE]
1. Are there any more packages that I must install before I install Wine?
2. Are there any more packages that I must install before I install CrossOver Linux?
3. For the Ubuntu Mini installation + firefox/geany, are there more packages that are required by Firefox or Geany?
4. Are any more packages required for the Ubuntu Mini installation?

SOURCES:
Ubuntu minimal: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Wine: [https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu)
Crossover:
[http://www.ubuntugeek.com/how-to-install-crossoverrun-windows-applications-on-ubuntu-full-version-in-ubuntu-12-10.html](http://www.ubuntugeek.com/how-to-install-crossoverrun-windows-applications-on-ubuntu-full-version-in-ubuntu-12-10.html)
[https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install](https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install)
Geany: [https://livesoncoffee.wordpress.com/2012/11/09/install-geany-1-22-on-ubuntu-12-04/](https://livesoncoffee.wordpress.com/2012/11/09/install-geany-1-22-on-ubuntu-12-04/)

---

### Post by raptir on 2015-01-13
That should work. A couple comments:

[LIST]
[*]Apt-get does a solid job of handling dependencies. When you install Firefox, Geany, Wine, etc... it's going to pull in all the other packages that are needed automatically.
[*]Geany is already in the repos, so I don't know that you need to add the PPA unless there is a specific feature you need from the newer version.
[*]lxde will pull in lxdm by default, so you don't need to specify it separately. It can't hurt though.
[/LIST]

---

### Post by Stan_1936 on 2015-01-13
^^^^Than you for the reply - it was most informative. You were right about Geany - I did not need to add a ppa. I have tried the above procedure and have installed Wine and Crossover Linux(trial version). I did not install geany-plugins.

I should mention that I deviated a bit and I selected Lubuntu Minimal Installation from the "Select software" menu (during the minimal installation) as per: [http://amjjawad.blogspot.ca/2013/06/mini-lubuntu-part-2.html](http://amjjawad.blogspot.ca/2013/06/mini-lubuntu-part-2.html). Everything appears to have worked as expected.

I am now facing one problem with the login screen. After starting up, I am brought to a login screen in Lubuntu as is shown in the link here: [http://1.bp.blogspot.com/-1F8t2bqvozk/Uay3GTSTeLI/AAAAAAAAAiM/ASphAVjpjBw/s1600/lightdm.png](http://1.bp.blogspot.com/-1F8t2bqvozk/Uay3GTSTeLI/AAAAAAAAAiM/ASphAVjpjBw/s1600/lightdm.png). I need to bypass this since I want auto login.

I have a /etc/lightdm/default.conf file. I tried to uncomment the Autologin screen here and enter my username as per: [http://www.htpcbeginner.com/enable-lubuntu-auto-login/](http://www.htpcbeginner.com/enable-lubuntu-auto-login/). The difference is that I don't have a lightdm.conf file but only have default.conf instead.

Is there a way to bypass the auto login screen? Or to check why my change is not working?

---

### Post by raptir on 2015-01-15
It looks like lightdm doesn't read in default.conf. If I enable autologin, I have a lightdm.conf that reads:

```

[SeatDefaults]
autologin-guest=false
autologin-user=%username%
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

I would say just make a lightdm.conf that contains that and you should be all set.

Also keep in mind that a full Lubuntu install from the live CD is only about 2.5GB. For simplicity's sake you could always try that.

---

### Post by Stan_1936 on 2015-01-15
> **raptir said:**
> It looks like lightdm doesn't read in default.conf. If I enable autologin, I have a lightdm.conf that reads:

```

[SeatDefaults]
autologin-guest=false
autologin-user=%username%
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

I would say just make a lightdm.conf that contains that and you should be all set.

Also keep in mind that a full Lubuntu install from the live CD is only about 2.5GB. For simplicity's sake you could always try that.

I would need to create the file as root. What's the command to create the file in the particular location required?

---

### Post by raptir on 2015-01-19
> **Stan_1936 said:**
> I would need to create the file as root. What's the command to create the file in the particular location required?

Sorry for the delay. I personally recommend doing all operations that require root access from the terminal. You can do them from graphical applications as well, but there are potential issues with that (where root can "steal" ownership of files in your home directory).

To just create an empty file, you can run (from the terminal):

```
sudo touch /etc/lightdm/lightdm.conf
```

At that point, you can use nano (a simple console-based text editor) to edit the file. 

```
sudo nano /etc/lightdm/lightdm.conf
```

You can also skip the *touch* command because nano will create the file when you save changes if it does not already exist.

Just remember to use **shift**-ctrl-v to paste into a terminal based application.

---

