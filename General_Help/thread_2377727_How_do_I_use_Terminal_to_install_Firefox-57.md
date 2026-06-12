---
title: "How do I use Terminal to install Firefox-57 ?"
date: 2017-11-16
forum: General Help
---

### Post by Timmoore001 on 2017-11-16
nothing I've tried works.

Any ideas anyone :

A frustrated 

:  (((

Tim

---

### Post by vasa1 on 2017-11-16
Why not just run```
sudo apt-get update
```followed by```
sudo apt-get upgrade
```

If you find anything you don't understand in the terminal output of either command, post the entire output here.

---

### Post by andersoncb on 2017-11-16
Firefox 57 is a whole new edition, built for faster page loading, smoother scrolling and more responsive tab switching.
Please follow below steps to install the latest version of Firefox 57.[COLOR=#212529][FONT=Montserrat]
[/FONT][/COLOR][B]
Step 1 &#8211; Download Firefox 57[/B]
Open the Terminal app and type the following wget command:
cd /tmp/
wget -L -O firefox.tar.bz2 'https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US'
[B]Step 2 &#8211; Extract (untar) Firefox 57
[/B]Untar the tar ball named firefox.tar.bz2 into your home directory, run[COLOR=#212529][FONT=Montserrat]:[/FONT][/COLOR]
mv firefox.tar.bz2 $HOME
tar xf firefox.tar.bz2
**NOTE- **Before launching firefox type the following command to kill all instance of older firefox using the[COLOR=#212529][FONT=Montserrat] [/FONT][/COLOR]killall command:
$ killall firefox
[B]Step 3 &#8211; Start Firefox 57 from the CLI
[/B]Just type the following command:
$ ~/firefox/firefox

---

### Post by vasa1 on 2017-11-16
> **andersoncb said:**
> Firefox 57 is a whole new edition, built for faster page loading, smoother scrolling and more responsive tab switching.
Please follow below steps to install the latest version of Firefox 57. ...
OP probably has Firefox 56 from the repos and an update will be provided automatically. The steps you describe won't be required. I got my update several hours ago :)

---

### Post by kurt18947 on 2017-11-16
I've installed Firefox 57 sort of like a DOS program. I created a folder in /home, downloaded Firefox57 and extracted it to that folder. Navigate to that folder, click on "Firefox" and it runs, finding the hidden .mozilla folder. My bookmarks, addons that are updated, themes, all are there. I have version locked Firefox 56 so it doesn't update until I know that Firefox 57 works with my sites. If I get inspired I may create a .desktop file for 57. I'm reluctant to commit full time to 57 'til Noscript is ported.

---

### Post by Impavidus on 2017-11-16
Just install the regular upgrades. I got Firefox 57 this morning (not impressed, BTW). Maybe your mirror is a bit slow.

---

### Post by slickymaster on 2017-11-16
> **vasa1 said:**
> Why not just run```
sudo apt-get update
```followed by```
sudo apt-get upgrade
```

If you find anything you don't understand in the terminal output of either command, post the entire output here.
> **Impavidus said:**
> Just install the regular upgrades. I got Firefox 57 this morning (not impressed, BTW). Maybe your mirror is a bit slow.

Those ^^^

---

### Post by raleigh3 on 2017-11-16
Quantum Firefox is impressive especially in speed. It was written to use all available cores.

As it is a beta, it has some bugs.

[https://itsfoss.com/firefox-quantum-ubuntu/](https://itsfoss.com/firefox-quantum-ubuntu/)

---

### Post by vasa1 on 2017-11-16
> **raleigh3 said:**
> ...
As it is a beta, it has some bugs.
...
It was released as a "stable"version yesterday. Most Ubuntu users will get it today.

---

### Post by Autodave on 2017-11-16
Got mine with updates this morning: works fine.

---

### Post by Timmoore001 on 2017-11-16
Many thanks for responding,  I tried cutting and pasting each step but got lost somewhere along the line.

I have got this file aok...        I don't have 56 downloaded and running , do that matter ?

firefox-57.0.tar.bz2  

what do I do next ?

---

### Post by vasa1 on 2017-11-16
Type```
apt policy firefox
```into your terminal and post the output here.

---

### Post by walts48 on 2017-11-16
> **Timmoore001 said:**
> Many thanks for responding,  I tried cutting and pasting each step but got lost somewhere along the line.

I have got this file aok...        I don't have 56 downloaded and running , do that matter ?

firefox-57.0.tar.bz2  

what do I do next ?

I created a folder called Apps in my Home folder, then cut and pasted the firefox-57.0.tar.bz into that folder.
Right clicked on the file and selected Extract Here. Once extracted Firefox is ready to go.
Then I opened a terminal and type Apps/firefox/firefox to launch it.
Once the Firefox icon is in the Launcher at the bottom of the window, I lock it to the Launcher and use the icon to start it.

---

### Post by Impavidus on 2017-11-16
AFAIK, Firefox is installed by default on all Ubuntu flavours (but I don't know all of them very well). If you did not uninstall it and run a supported release of Ubuntu (and you should), a simple```
sudo apt update
sudo apt upgrade
```will install Firefox 57. If you don't have Firefox installed, use```
sudo apt update
sudo apt install firefox
```If that doesn't work, post the error messages here. (And vasa1's```
apt policy firefox
```may be helpful too.)

If you once installed Firefox in a different way than from the repositories, you may have to remove that version first.

> **walts48 said:**
> I created a folder called Apps in my Home folder, then cut and pasted the firefox-57.0.tar.bz into that folder.
Right clicked on the file and selected Extract Here. Once extracted Firefox is ready to go.
Then I opened a terminal and type Apps/firefox/firefox to launch it.
Once the Firefox icon is in the Launcher at the bottom of the window, I lock it to the Launcher and use the icon to start it.

That's the hard way that will also prevent automatic upgrades in the future.

---

