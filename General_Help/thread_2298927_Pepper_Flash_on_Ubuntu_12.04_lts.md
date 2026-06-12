---
title: "Pepper Flash on Ubuntu 12.04 lts"
date: 2015-10-14
forum: General Help
---

### Post by michael-piziak on 2015-10-14
I want to try pepperflash on my ubuntu 12.04 lts,
what's the terminal code for it please

---

### Post by QDR06VV9 on 2015-10-14
To install Pepper Flash Player** for Chromium** in Ubuntu 12.04, open the terminal and type:
```
sudo apt-add-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer  

```

In order to configure **Chromium** to use Pepper Flash Player.
```
gksu gedit /etc/chromium-browser/default
```

and add the following line to the end of the file
```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh 
```
Save and exit.
Restart Chromium or just use Chrome
Regards

---

### Post by michael-piziak on 2015-10-14
ok thanks, i'll give that a try

---

### Post by michael-piziak on 2015-10-14
Thanks so much!

It made my videos work on a certain website that I can't link to do to forum rules.

Thanks again!

---

### Post by QDR06VV9 on 2015-10-14
Your Very Welcome!:D
To see what version of Pepper Flash you are runing
```
sudo update-pepperflashplugin-nonfree --status
```
Kind Regards

---

### Post by michael-piziak on 2015-10-14
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo update-pepperflashplugin-nonfree --status
[sudo] password for michael: 
sudo: update-pepperflashplugin-nonfree: command not found
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo update-pepperflashplugin-nonfree --status
sudo: update-pepperflashplugin-nonfree: command not found
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo update-pepperflashplugin-nonfree --status
sudo: update-pepperflashplugin-nonfree: command not found
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by michael-piziak on 2015-10-14
Appears to be the latest:

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo apt-get install pepflashplugin-installer
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pepflashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by QDR06VV9 on 2015-10-14
Sometimes this is needed to get it to work.
But you need to close Chromium first to run it
```
sudo [COLOR=black]update-pepperflashplugin-nonfree --install[/COLOR]
```

---

### Post by michael-piziak on 2015-10-14
> **runrickus said:**
> Sometimes this is needed to get it to work.
But you need to close Chromium first to run it
```
sudo [COLOR=black]update-pepperflashplugin-nonfree --install[/COLOR]
```


It is already working for me.

Should I still enter this code into terminal - ???

---

### Post by QDR06VV9 on 2015-10-14
This what mine shows for
```
sudo update-pepperflashplugin-nonfree --status[sudo] password for me: 
Flash Player version installed on this system  : 19.0.0.185
Flash Player version available on upstream site: 19.0.0.185

```
So it would not hurt, Remember to close Chromium before running
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]update-pepperflashplugin-nonfree --install[/FONT][/COLOR]
```

---

### Post by michael-piziak on 2015-10-14
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo update-pepperflashplugin-nonfree --install
[sudo] password for michael: 
sudo: update-pepperflashplugin-nonfree: command not found
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo update-pepperflashplugin-nonfree --install
sudo: update-pepperflashplugin-nonfree: command not found
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by QDR06VV9 on 2015-10-14
Lets see if we get a different result now.
```
sudo update-pepperflashplugin-nonfree --status
```
Post back

---

### Post by michael-piziak on 2015-10-14
nope, same results in terminal as my last post

---

### Post by QDR06VV9 on 2015-10-14
What dose this show
```
gedit /etc/chromium-browser/default
```

---

### Post by QDR06VV9 on 2015-10-15
@michael-piziak Thanks for the message, Letting me know all is good.:D
Glad it got installed OK!
I guess those commands are different for 12.04 vs 14.04???
If any one else needs to verify their version you can simply go to
[https://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf](https://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf)
Should show that you are running Version 19,0,0,207
As of the current date 10/15/2015
Kind Regards

---

### Post by coffeecat on 2015-10-15
I believe the adobe-flashplugin package is now available from the partner repository for 12.04. If I'm reading the links below correctly, it installs/updates both the adobe flash plugin for Firefox, and also the pepper flash plugin for Chromium. It certainly did for me in 15.04. No need for all that terminal stuff for the latter now. 

[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

[https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash)

@michael-piziak, if you want to try that, go to the Software and Updates window in System Settings, Repositories in Synaptic, or Software Sources in Software Centre (they all lead to the same place, but I'm not sure if all work that way in 12.04) and tick Canonical Partners under the other software tab. Refresh your metadata and you will be able to install adobe-flashplugin which will uninstall the older flashplugin-installer if you have it already installed.

---

