---
title: "firefox crashes, freezes, slows down"
date: 2007-07-19
forum: General Help
---

### Post by TLD321 on 2007-07-19
I have a rediculous amount of firefox woes.

first off, whenever I play any flash game on firefox, the sound is screwed up; it sounds choppy, little pings and clicks every second. It took me a very, very long time to get my 5.1 speakers up and running with surround sound, and if the solution to the crappy sound is to disable the speakers, I'm not doing it.

secondly, sometimes firefox freezes ubuntu. The only time I've ever had my system freeze was when a firefox page was loading.

thirdly, QUITE OFTEN, firefox wil shut down automatically, again, usually when loading a page. I'll just click a link and my browser will close.

fourth, QUITE OFTEN, firefox will slow down...or something. You see, what happens is, I'm running firefox and I open a new tab, only to find myself unable to click on that tab. I can CLOSE the tab, but I cannot go to the page.

fifth, QUITE OFTEN, loading a flash on firefox will freeze it, causing me to force quit. You don't know how many f'n times I've had to force quit firefox...probably more times that I've been able to close it normally.

if anyone has any idea, a guess even, at why all this nonsense is happening, talk to me please

---

### Post by jonathanmotes on 2007-07-19
Try Swiftfox, it seems to be MUCH better with Flash, at least for me. It is available with the Automatix package manager. The Swiftfox plugins are also very useful for playing other media inside the browser. Try this [link.]("http://www.getautomatix.com/wiki/index.php?title=Installation")

---

### Post by TLD321 on 2007-07-20
but you see, that's not FIXING the problem, that's AVOIDING the problem...hardly the same thing.

thanks anyway though...by the way, I found another thread of folks with similar woes:

[http://ubuntuforums.org/showthread.php?t=480563](http://ubuntuforums.org/showthread.php?t=480563)

seems that firefox and ubuntu have some issues to work out, hm? Lets get on that, software people.

---

### Post by Seisen on 2007-07-20
What extensions if any do you have installed.

---

### Post by TLD321 on 2007-07-20
> **Seisen said:**
> What extensions if any do you have installed.

I have Video Downloader 1.1.1 installed, that's it.

---

### Post by Seisen on 2007-07-20
Run firefox from the terminal in safe-mode and see if you still have the same problems.```
firefox -safe-mode
```

---

### Post by Siph0n on 2007-07-20
Yup firefox and me dont get along either... I have a thread posted about it freezing ubuntu when I go to certain websites... Im looking for an alternative.... :)

---

### Post by stchman on 2007-07-20
> **TLD321 said:**
> I have a rediculous amount of firefox woes.

first off, whenever I play any flash game on firefox, the sound is screwed up; it sounds choppy, little pings and clicks every second. It took me a very, very long time to get my 5.1 speakers up and running with surround sound, and if the solution to the crappy sound is to disable the speakers, I'm not doing it.

secondly, sometimes firefox freezes ubuntu. The only time I've ever had my system freeze was when a firefox page was loading.

thirdly, QUITE OFTEN, firefox wil shut down automatically, again, usually when loading a page. I'll just click a link and my browser will close.

fourth, QUITE OFTEN, firefox will slow down...or something. You see, what happens is, I'm running firefox and I open a new tab, only to find myself unable to click on that tab. I can CLOSE the tab, but I cannot go to the page.

fifth, QUITE OFTEN, loading a flash on firefox will freeze it, causing me to force quit. You don't know how many f'n times I've had to force quit firefox...probably more times that I've been able to close it normally.

if anyone has any idea, a guess even, at why all this nonsense is happening, talk to me please

My FF was doing the same thing on youtube and I fixed it this way:

Delete the flash plugin in your ~/.mozilla/plugins folder.

Install the flash plugin via synaptic.

sudo apt-get -y install flashplugin-nonfree

Worked for me.

---

### Post by Siph0n on 2007-07-20
wow thanx!!! I will try that!!! :)

---

### Post by TLD321 on 2007-07-20
> **Seisen said:**
> Run firefox from the terminal in safe-mode and see if you still have the same problems.```
firefox -safe-mode
```

I ran firefox in safe mode, sound was still crappy, and it still crashed on me when loading a youtube video, so I'm guessing the problem still remains. In my terminal I got a message:

Segmentation fault (core dumped)

right when it crashed, does that have something to do with it?

---

### Post by Seisen on 2007-07-20
Have you tried uninstalling flash and then reinstalling it using synaptic?

---

### Post by TLD321 on 2007-07-20
well I uninstalled my flash player by deleting the files in my .mozilla/plugins folder, and executed 


sudo apt-get -y install flashplugin-nonfree

but it didn't physically "install" the flash player...even my konsole said "flash player NOT installed"...is that a problem on my end or is there another thing I have to do?

---

### Post by Seisen on 2007-07-20
Open up synaptic and do a search for ```
flashplugin-nonfree
``` and see if it is installed or not. If it isn't installed, install it and see what happens.

---

### Post by TLD321 on 2007-07-20
I re-installed the flashplugin-nonfree through synaptic, but nope, still no flash loads. Youtube tells me:

Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player.

and my firefox browser says "Additional plugins are required to view all the material on this page" 

should I just install the plugin with firefox?

---

### Post by Seisen on 2007-07-20
Did you restart Firefox after reinstalling?

---

### Post by TLD321 on 2007-07-20
as in closed the browser and then opened the browser again, yes

---

### Post by TLD321 on 2007-07-21
so...I kinda need a solution here or the internet is pretty useless...

should I just install flash through firefox in the meantime until a solution to the many, many problems is found?

---

