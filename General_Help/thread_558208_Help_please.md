---
title: "Help please"
date: 2007-09-23
forum: General Help
---

### Post by Atzu on 2007-09-23
I'm running Ubuntu Feisty Fawn on HP Compaq nc6220 sometimes (just sometimes) after the log in screen my ubuntu get freeze and i need to ctrl+alt+backspace to try log in again and i need to do that lot of times till i can access my account.

Any ideas?

---

### Post by p_quarles on 2007-09-23
The make and model of a computer doesn't actually tell anyone much about it. What is the processor? What's the graphics card? How much RAM?

Also, are you dual-booting with Windows, or just using Ubuntu?

---

### Post by Atzu on 2007-09-23
processor and graphic cards i dont know, RAM is 512 and  this comp is ubuntu only

---

### Post by p_quarles on 2007-09-23
Well, find out those details and I or someone else here will be happy to try to help.

---

### Post by Atzu on 2007-09-23
I believe this is the graphic card: Intel Graphics Media Accelerator 900,   and this the processor: Intel Pentium M 740 processor (1.73GHz)

---

### Post by ddrichardson on 2007-09-23
The specs are [here]("http://h18002.www1.hp.com/products/quickspecs/12130_div/12130_div.HTML"). Create a new account and see if it happens on the new account, then you know whether its a) hardware or b) a configuration error in Gnome.

---

### Post by Atzu on 2007-09-23
> **ddrichardson said:**
> The specs are [here]("http://h18002.www1.hp.com/products/quickspecs/12130_div/12130_div.HTML"). Create a new account and see if it happens on the new account, then you know whether its a) hardware or b) a configuration error in Gnome.

I made a new account and everything was fine

---

### Post by ddrichardson on 2007-09-23
So then the problem lies in something that's running in the main account then, what is in your session?

---

### Post by Atzu on 2007-09-23
I have compiz fusion, emerald (and had awn) when i uninstalled awn my account worked fine, just that when i use restart none of the users are able to log in,  got stuck in the screen says like: nautilus, restricted drivers manager... 

When i use shut down and then power on my comp i think it works just that have a delay on that screen.

---

### Post by p_quarles on 2007-09-23
AWN is pretty buggy. I used it for a bit, and found that even after I'd uninstalled, it left some stuff hanging around. If you installed it from the third-party repository, you should be able to fix it by running:
```
sudo apt-get remove libawn-bzr
```

---

### Post by Atzu on 2007-09-23
when i use sudo apt-get remove libawn-bzr  i get this:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libawn-bzr is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libawn0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

i use apt-get autoremove?

---

### Post by ddrichardson on 2007-09-23
p_quarles is right - Awn is buggy. Frankly I think that most of the whizzo eye candy stuff isn't worth the overhead, but there you go.

How did you uninstall Awn?

---

### Post by ddrichardson on 2007-09-23
```
sudo apt-get autoremove
```

Actually you can uninstall using autoremove as well - ```
sudo apt-get autoremove packagename
```It's just safer not to.

---

### Post by p_quarles on 2007-09-23
> **Atzu said:**
> when i use sudo apt-get remove libawn-bzr  i get this:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libawn-bzr is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libawn0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

i use apt-get autoremove?
Yeah, run that command:
```
sudo apt-get autoremove
```

libawn0 is the same package I was talking about, but I guess you installed it using a different repository.

---

### Post by Atzu on 2007-09-23
> **ddrichardson said:**
> p_quarles is right - Awn is buggy. Frankly I think that most of the whizzo eye candy stuff isn't worth the overhead, but there you go.

How did you uninstall Awn?

well for installing i used the guide here: [http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=272&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=272&page=1&isLive=true)

for uninstalling i did this:
```
cd avant-window-navigator
make
sudo make uninstall
```

---

### Post by Mud.Knee.Havoc on 2007-09-23
This problem, in my experience, is nearly always related to the video driver.  I've always had problems with freezing at login screens using both ATI and Nvidia drivers on various computers.  As soon as the stock driver is used, everything is fine.  Of course, the bad side is that you can't run 3d stuff. :(

---

### Post by Atzu on 2007-09-23
> **Mud.Knee.Havoc said:**
> This problem, in my experience, is nearly always related to the video driver.  I've always had problems with freezing at login screens using both ATI and Nvidia drivers on various computers.  As soon as the stock driver is used, everything is fine.  Of course, the bad side is that you can't run 3d stuff. :(

i had a comp with very old video card (Nvidia ge force 2go (32MB)) i wasn't able to run beryl, compiz and wasn't able to run videos

---

### Post by ddrichardson on 2007-09-23
Unfortunately there are guides everywhere to installing everything - as a beginner though I can strongly suggest the use of apt-get and repositories. Firstly, it enables automatic updating, secondly - trusted sources are good from a security point of view, and lastly installing and uninstalling is Ubuntu policy compliant.

Excuse my rant if awn isn't in the repos ;-)

---

### Post by Atzu on 2007-09-23
So is there any other of those bars out there?

---

### Post by p_quarles on 2007-09-23
You mean dock bars? The most stable ones are Simdock for Gnome, and Kooldock for KDE. Neither of them are as nice as AWN, but they do the job and they won't crash your system.

---

### Post by Atzu on 2007-09-23
> **p_quarles said:**
> You mean dock bars? The most stable ones are Simdock for Gnome, and Kooldock for KDE. Neither of them are as nice as AWN, but they do the job and they won't crash your system.

Any guide or i can get them with apt-get ?

---

### Post by p_quarles on 2007-09-23
Yeah, they're both in the main repositories.
```
sudo aptitude install simdock
```
or 
```
sudo aptitude install kooldock
```

---

### Post by Atzu on 2007-09-23
> **p_quarles said:**
> Yeah, they're both in the main repositories.
```
sudo aptitude install simdock
```
or 
```
sudo aptitude install kooldock
```

hmm 

```
andres@andres:~$ sudo aptitude install simdock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "simdock"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

---

### Post by p_quarles on 2007-09-23
Sorry, I guess I thought it was there. Here's a link to the .deb installer file:
[http://www.getdeb.net/app.php?name=SimDock](http://www.getdeb.net/app.php?name=SimDock)

---

### Post by Atzu on 2007-09-23
hmm and how i install that? 

Thanks a lot for helping btw ^^

---

### Post by p_quarles on 2007-09-23
It's an installer file, so you can just go to the folder where you downloaded it and left-click on it, then give it your password. 

If it gives you an error saying that dependency packages are missing, make a note of the package names and use "sudo apt-get install" to get them. 

No problem. Glad we could get your computer back in working order.

---

