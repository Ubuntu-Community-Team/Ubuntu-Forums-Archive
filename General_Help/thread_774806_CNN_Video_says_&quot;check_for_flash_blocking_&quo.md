---
title: "CNN Video says &quot;check for flash blocking &quot;"
date: 2008-04-29
forum: General Help
---

### Post by ruetheday on 2008-04-29
I installed Ubuntu, then went to firefox and then to CNN.  It said i needed to install 3 plug-in's, and gave me 3 boxes to check.  Only one box was able to be checked at a time. I thought you installed each one separately, so I did the first one which was something to do with flash. I think swfdec. However,the second choice seemed like the one i should have clicked,it was a general flash install.  

     I can't un-install that program and then go back to cnn and have it recognize i need new plug-in's. I tried already.

     I also reinstalled Firefox 3 using this code in the terminal:  
  wget -P ~ [ftp://ftp.mozilla.org/pub/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2](ftp://ftp.mozilla.org/pub/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2) && tar xjf ~/firefox-3.0b4.tar.bz2 -C ~

     This reinstalled it, however it didn't ask for the installation of any plugin's. Ubuntu, will not let you uninstall firefox from add and remove programs.

     I also see a huge "PLAY" emblem over flash items that never happened when I used Ubuntu and firefox before.  I have tried every combination of add-on's to correct this.  My initial install of flash in firefox Flash was version 9.0 r100 I updated to Flash version 9.0 r124 and i cannot remove the other version from add on's, i can only disable it.  version 9.0 r124 is not working.  

     can someone help before I go and reinstall ubuntu and have the same thing happen 
 
Thanks

---

### Post by forrestcupp on 2008-04-29
The easiest way to install Flash in a way that works is 
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by ruetheday on 2008-04-29
Yeah good point, that is how i did the update i should have mentioned that.  It still won't work like it did in my previous use of Ubuntu and firefox

---

### Post by forrestcupp on 2008-04-29
Are you using Gutsy or Hardy?

---

### Post by ruetheday on 2008-04-29
Ubuntu 8.04 LTS (Hardy Heron)

I already installed a few programs. i would hate to re install ubuntu ...but i will if i have to.  I am determined to make this Ubuntu work, for my day to day use.  DEEEEEETERMINED!!!!

---

### Post by cynical_remarks on 2008-04-29
I have the same problem with the CNN website.

YouTube works fine though.

I think CNN has this Turner Player and appears to be a pain in the proverbial to get it to run. 

It worked for me on 7.10, but after a fresh install of 8.04 nada, niente, nothing, nichts.

I would really like to get this to work.

Mike

---

### Post by ingrid_ozikem on 2008-04-29
Same problem here.. Firefox allowed only one kind of package the first time I went to Youtube. I opted to install Shockwave flash player (the other options included Adobe and something else). Now Youtube works but CNN says I have a flash blocker.

On the other hand, no flash works for Opera & Konqueror.. does anyone know how to install flash for Opera? (I do have the flashplugin-nonfree installed.)

---

### Post by DirtDawg on 2008-04-29
I had problems with the Flash install as well (I couldn't even watch youtube videos). But here's how I fixed it.

Uninstall whatever version of Flash you installed through Firefox (use synaptic). Go to youtube.com where you will be advised to download the linux version of Flash. Follow the links and download said Flash. Unzip the package and inside is a script. Run the script in the terminal, follow the easy instructions and you're set.

This fixed all my Flash woes.

EDIT: I haven't tested this on CNN, which is what this thread is about (dar!). Still, maybe it's worth a shot.

---

### Post by NilsE on 2008-04-29
I got CNN and most everywhere else like Google, Youtube etc working by going into Synaptic and removing everything that search of just the word flash found just leaving the following installed.

libswfdec-0.6-90  (0.6.4-2)
flashplugin-nonfree  (9.0.124.0ubuntu2)
ubuntu-restricted-extras  (15)

Installed version in ( )'s

---

### Post by ruetheday on 2008-04-29
Ahhhhh synaptic!!  thats what you use....  once i found it i used it like you said, searching flash... then i saw the swfdec file still installed.  i got rid of it, thanks to the icon legend that got me started using the program super fast.  it's working , kind of jerky like in windows.  flash has gotten too fat or something.  i remember version 5 i think was the best.   ahhhhhhhh  Ubuntu i can start to fix my pen tablet and install my editing software.  my next tweak!!!   thanks everyone

---

### Post by forrestcupp on 2008-04-30
> **ingrid_ozikem said:**
> 
On the other hand, no flash works for Opera & Konqueror.. does anyone know how to install flash for Opera? (I do have the flashplugin-nonfree installed.)

The latest flashplugin-nonfree has issues with the latest stable release of Opera, but it works just fine with the latest beta release of Opera.  Just go to their site and download the deb for your version of Ubuntu, and if you already have flashplugin-nonfree installed, it will just work.

---

### Post by PatricioLearner on 2008-10-27
I have 
firefox 3.0.3
libswfdec-0.6-90 (0.6.4-2)
flashplugin-nonfree (10.0.12.36ubuntu1~ppa1)
ubuntu-restricted-extras (15.2)
kubuntu-restricted-extras (15.2)
Xubuntu-restricted-extras (15.2)
everything works but CNN video (the live video does work! [http://www.cnn.com/video/flashLive/live.html?stream=stream1](http://www.cnn.com/video/flashLive/live.html?stream=stream1))
Thist does not work: [http://www.cnn.com/video/](http://www.cnn.com/video/), 
you tube works, java works (including sound)
any suggestions?

EDIT: now [http://www.cnn.com/video/](http://www.cnn.com/video/) also WORKS. Maybe there was something going with the site.  It is a bit choppy now.

---

