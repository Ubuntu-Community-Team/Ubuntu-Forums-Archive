---
title: "No GUI on start up -really very noobie..."
date: 2007-09-04
forum: General Help
---

### Post by rogrobin on 2007-09-04
I have recently installed 7.04 which had been working for 10 days or so.

My problem: When I startup I dont get a GUI -by no GUI I mean I just get the white on black text with no windows and no mouse pointer.  I have tried starting in safe mode but the same.  

What I did: This is my first attempt at linux and it had taken me several very long and late nights to get to a stage where I was nearly happy with my install.  Only problem was no sound.   So I looked up my problem on the forums and downloaded the appropriate driver.  Then I copied some command line stuff from the "what to do if have no sound" thread into my terminal window.  I dont know what this was and unfortunately I cant find this page again because I cant get at my bookmarks. Hey presto no GUI next time I restarted.

I wish I could tell you more.   I feel a little bit stupid but please be gentle and help me make it better.

Thanks

Roger

---

### Post by taurus on 2007-09-04
At the login prompt, log in with your username and password.  Then, run this command and if there is an error, post the whole thing here.

```
startx
```

p.s.  Did you install the desktop or the server version?

---

### Post by rogrobin on 2007-09-04
OK thanks taurus.  Yes it all seems to load up fine with that command -so no errors.  -and yes I installed the desktop version.  

Is there any way I can make this permanent so I dont have to write startx every time I boot up?

Now I have my bookmarks I have been able to find the post with the instructions that I followed. So this is what i did to try and remedy my sound problem and which Im guessing caused my initial problem.
Quotes are from [COLOR=SandyBrown][COLOR=Red][this page]("http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound")[/COLOR] [/COLOR]on the Ubuntu help forums[INDENT]
"Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils
[list]
[*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot
[*][left]
VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop  "


[/INDENT]So thats it -thanks for your suggestions.  

Roger

P.S .Oh and by the way I still have no sound....  but I guess thats for another thread.

---

### Post by init1 on 2007-09-04
Looks like you erased you GDM. 
Try this in the terminal:
```
which gdm
```

---

### Post by rogrobin on 2007-09-04
Thanks init1. 

 I tried             

 which gdm                    

and nothing happens.

Roger

---

### Post by por100pre1 on 2007-09-04
Try installing and starting it:

```
sudo aptitude install gdm
```

```
sudo /etc/init.d/gdm start
```

---

### Post by rogrobin on 2007-09-05
OK thanks very much for your help. 

That seems to do the trick.  All is good now. 

Just need to work out how to get some sound.....  

Roger

---

