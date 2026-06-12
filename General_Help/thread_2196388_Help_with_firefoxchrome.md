---
title: "Help with firefox/chrome"
date: 2013-12-29
forum: General Help
---

### Post by d-wall08 on 2013-12-29
I'm a new Ubuntu user, I have Ubuntu 12.4, have Firefox and chrome, firefox won't play flash, and chrome will yet crashes. I download Restricted-extras package, and The flash plugin. Still having issues. I'm working with 256MB RAM, and a 32-bit system. Not good I know. Please help if possible. Thanks.

---

### Post by ajgreeny on 2013-12-29
If you are running Ubuntu 12.04 with the unity desktop I'm surprised you are even able to get the OS installed and running at all with only 256MB ram, and I suspect that is the main cause of your crashing chrome.

As for the flash problem, chrome installs its own version of pepperflash plugin, which is a google version of 11.9, whilst the adobe flash in Linux is 11.2 in all other situations, and flash in Linux takes a lot of resources; 256MB ram is, I think, very borderline.

What is your other machine specs, as it may help us give you more help?

Suggestions:-

[LIST=1]
[*]For a start I suggest you try using Lubuntu, though even that may baulk at 256MB ram.
[*]Add more ram if possible; it's the cheapest upgrade you can make to a system.
[*]If Lubuntu is still no good, look at some of the even lower resource users, such as Puppy, DSL, etc etc.  Go to  [DistroWatch.com]("http://distrowatch.com/")  for more info on OSs available.
[/LIST]

---

### Post by d-wall08 on 2013-12-29
Thanks for replying! Actually its 512MB RAM. So Lubuntu is made for low-end running and older PC's? I'm downloading it now. I'd like to completly replace Ubuntu with Lubuntu. Any suggestions on this matter?

---

### Post by deadflowr on 2013-12-29
Are you running it as a stand-alone system or is it a dual-boot?
If stand alone, since it is relatively new install it as a completely new system.
If dual boot, install it over where ever you put the ubuntu install.
Basically, install it to overwrite the ubuntu install.

In lubuntu, instead of the ubuntu-restricted-extras, put an L(small, but I used the big one so you know it is not a number or an I) in front : lubuntu-restricted-extras.

Edit: I'm not sure if it still does, but I think lubuntu uses chromium-browser as it's default.
That is the open-source verison that google chrome is based on.
However it does not use the chrome flash plugin.
But if you follow this guide, it will give the you the abilty to use the chrome flash plugin.
[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

otherwise, you can just install the restricted packages and use the linux version of flash, which is old(because adobe dropped development of flash for linux, though it still supports it;for now)

---

### Post by d-wall08 on 2013-12-29
Thanks deadflowr. I tried that went to gedit and tried editing and saving default.sh, and it won't let me. I don't have permission, which i don't understand. Iv'e replaced windows XP with Ubuntu 12.4. No dual boot. And I don't have permission on my own computer? Confused... Please help. Thanks.

---

### Post by deadflowr on 2013-12-29
> **d-wall08 said:**
> Thanks deadflowr. I tried that went to gedit and tried editing and saving default.sh, and it won't let me. I don't have permission, which i don't understand. Iv'e replaced windows XP with Ubuntu 12.4. No dual boot. And I don't have permission on my own computer? Confused... Please help. Thanks.

Firstly, did you install Lubuntu, or is this still Ubuntu?
Secondly, did you run the gksu command
```
gksu gedit <filenamehere>
```
?
I'm guessing this is for the pepperflash ppa setup.

Added: I don't know if Lubuntu uses gedit, anyway.
I though it used leafpad, or maybe even mousepad.
Concept's the same though, just change gedit for the text editor Lubuntu uses.

---

### Post by d-wall08 on 2013-12-29
Ok. Now I downloaded lubuntu 13.10. Should I create a startup installation disk and reboot and install Lubuntu from there, or can I open and install the .iso with Ubuntu running? And yes its for the pepperflash ppa setup.

---

### Post by deadflowr on 2013-12-29
Reboot after you burn/make an install disk/usb thingy.
If the burn is bad, the worst thing that'll happen is it won't be read and you'll just boot into the existing Ubuntu you have already installed.
I know, though that when you put an install disk in the cd drive when using Ubuntu it sometimes will tell you it has found install packages, or something to that effect. But I've never run that, so don't know what to except.
Simpler to just reboot and re-install.

---

### Post by mörgæs on 2013-12-29
Please run (using any kind of Buntu)
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by d-wall08 on 2013-12-30
I downloaded and installed Lubuntu, I have a 32 bit system with 512 MB RAM. It's not in dual boot. Foxfire doesn't play flash, and I'm new to Lubuntu, is there any updates I should know about?

---

### Post by sudodus on 2013-12-30
Run the following command in a terminal window to play multimedia (including flash) in a better way.

```
 sudo apt-get install lubuntu-restricted-extras
```

And after you restart Firefox, it should be able to play flash.

---

### Post by mörgæs on 2013-12-30
Threads merged. 
If you want help then please post the results from post 9.

---

### Post by monkeybrain20122 on 2013-12-30
> **deadflowr said:**
> 
Edit: I'm not sure if it still does, but I think lubuntu uses chromium-browser as it's default.


No, it uses Firefox now.

---

### Post by monkeybrain20122 on 2013-12-30
Well if you have that weak a system even if flash works it won't be pretty. If you use flash just for usual sites like Youtube, Vimeo I suggest you get Viewtube
[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

Install the greasemonkey addon for Firefox then go to the link above and click install then restart Firefox and you are set. You may want to use standard or low resolution instead of high.

Videos for supported sites (you can find a list on the link) will play in gecko-mediaplayer (think it is installed in lubutu by default) and it will be a lot easier on your system. 

Use flash only when you have to.

---

### Post by deadflowr on 2013-12-30
> **monkeybrain20122 said:**
> No, it uses Firefox now.
Yeah, I remember there was a discussion, but couldn't remember if it was for 13.10 or 14.04.:confused:
It might have even been for 13.04.
Probably should have noted to OP to check and see which browser did in fact install during installation.
Oversight on my part, maybe.
Still, it'd be nice to know the specs from the output of lshw to determine if the machine can even run the latest flashes.

---

### Post by d-wall08 on 2014-01-07
I'm running a 32bit system, 512mb RAM, ubuntu 12.4, no dual boot. I installed restricted extras. IcedTea, and a Java plugin. Java still doesn't play, for instance- Pogo.com. And it crashes every now and then. Been having this problem for awhile. What to do, and is there a different browser I can get that won't crash with flash or java?

---

### Post by monkeybrain20122 on 2014-01-07
What do you expect with 512m of ram? I wouldn't be surprised that it freezes or crashes occasionally with heavy stuffs like flash or java.  Is it actually possible to run Ubuntu 12.04 on this specs? I am impressed, but think lubuntu will work better. Chrome also tends to use more ram than say Firefox especially if you have a few tabs open.

---

### Post by Impavidus on 2014-01-07
You'd best switch to Lubuntu 13.10. It's much happier on just 512MB memory.

---

### Post by mörgæs on 2014-01-07
Threads merged AGAIN.
Your multiposting is getting annoying. Please take this as a warning.

---

