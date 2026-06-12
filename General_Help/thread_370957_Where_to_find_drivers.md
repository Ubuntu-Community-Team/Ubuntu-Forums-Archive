---
title: "Where to find drivers ?"
date: 2007-02-26
forum: General Help
---

### Post by teedee on 2007-02-26
Hi,

There seems to be a shortage of drivers for Compaq Presario
does anyone know the best place to find some ?

My model is ;

Compaq Presario 2500 (2521EA)

Thanks

---

### Post by Maestro23 on 2007-02-26
Drivers: [http://h10025.www1.hp.com/ewfrf/wc/product?product=297889&lc=en&cc=us&dlc=en&submit.y=6&submit.x=8&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=297889&lc=en&cc=us&dlc=en&submit.y=6&submit.x=8&lang=en&cc=us)

Best bet for you compaq.

---

### Post by teedee on 2007-02-26
what to do when there are only windows drivers there ?
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=297889&lang=en&](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=297889&lang=en&)

Does that mean I would be better of just to give up on ubuntu and go back to windows ?

---

### Post by bigken on 2007-02-26
> **teedee said:**
> what to do when there are only windows drivers there ?
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=297889&lang=en&](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=297889&lang=en&)

Does that mean I would be better of just to give up on ubuntu and go back to windows ?


no it does not meen go back to windows you need to ask how to get items working on your machine ie your graphics card ect if you dont ask people wont answer

---

### Post by mrmonday on 2007-02-26
What do you need drivers for? Graphics card? wireless? What problems are you having?

---

### Post by teedee on 2007-02-26
> **bigken said:**
> no it does not meen go back to windows you need to ask how to get items working on your machine ie your graphics card ect if you dont ask people wont answer

Ok, but I have so much to ask, I really don't know where to start.......

Display drivers for model mentioned above

How to install software (like thunderbird) as I guess there is no .exe in ubunto and after extracting the tar.gz I have no idea. Even the thunderbird help just says "click on the exe......

My wireless card doesn't work, but that is in another thread already

anything else I need / should do after a default installation ?

How do I know what devices are not working in device manager ?

Can I get windows applications like dreamweaver & cuteftp to work under ubuntu ?

And many many more.

Thanks :D

---

### Post by bigken on 2007-02-26
so 1st things 1st can you connect to the internet if you can just use add/remove programs to install thunderbird you could also install automatix 
this will install all sorts of things for you codecs ect :)

not sure about the software

---

### Post by mrmonday on 2007-02-26
The easiest way to get display drivers is to use[ envy ]("http://www.albertomilone.com/nvidia_scripts1.html")(I belive it uses an ATI graphics card)
To install software go to applications>add/remove, providing you have internet access or a cd.
For windows software you can use [wine]("http://www.winehq.org/") or virtualisation software, but their are loads of open source alternatives.

---

### Post by bigken on 2007-02-26
envy is for nvidia cards do you know the make of your video adapter ?

---

### Post by mrmonday on 2007-02-26
Envy also does ATI graphics cards now... see the site above

---

### Post by teedee on 2007-02-26
I can currently connect to the net using a cable from another PC, but this is not ideal as I cannot use it all the time (from other location) , so the wireless card is quite urgent to get going.

The video card is an ATI Radeon /GP 33M/340M/350M    according to device manager.

I will check out envy and post back

---

### Post by mrmonday on 2007-02-26
What wireless card do you use? I had lots of problems with mine, but with a bit of tweaking it works flawlessly.

---

### Post by teedee on 2007-02-26
> **mrmonday said:**
> What wireless card do you use? I had lots of problems with mine, but with a bit of tweaking it works flawlessly.

My Wireless card is an Ericsson HA691

which I found out does work on Linux (just not on my Linux yet ) at [http://puppylinux.org/wikka/Wireless...how_comments=1](http://puppylinux.org/wikka/Wireless...how_comments=1)

Thanks

---

### Post by teedee on 2007-02-26
envy did not help with the display driver issue, it says mine is not supported.

still searching for the wireless card drivers, but no luck :(

---

### Post by mrmonday on 2007-02-26
Do you have the windows driver for your wireless card on a disk? you could use ndiswrapper

---

### Post by bigken on 2007-02-26
> **mrmonday said:**
> Envy also does ATI graphics cards now... see the site above

well one learns something every day

so it envy for the video 


ndiswrapper to try for the wireless card 

and wine for the software unless we can find alternative linux software ?

---

### Post by teedee on 2007-02-26
This is where I am with the wireless card.

I just installed wireless assistant 0.5.5 and it picks up 3 signals, so it would seem that the card is working....

I just cannot connect to the network I want to connect to.

Should I configure the card in "network settings" ? If so, what do I choose to access a WEP protected network ? I tried all the options in Wireless assistant and could not connect at all.

My WEP key is 10 digit

Still stuck on the video drivers as well....

Thanks again

---

### Post by mrmonday on 2007-02-26
what does
```
glxinfo | grep rendering
```
give?

---

### Post by teedee on 2007-02-26
> **mrmonday said:**
> what does
```
glxinfo | grep rendering
```
give?

driect rendering: No

---

### Post by teedee on 2007-02-26
Trying other things here to see if it helps.

WiFi Radar shows

"Connected to Lilledisain ip(none)"

(Lilledisain is my SSID) but for some reason it is not getting an IP.

I have 2 windows boxes connected to the network without any problems

---

### Post by teedee on 2007-02-26
ok, now we are getting there, WiFi is working (I disabled the wired connection in network settings and it started working)

Just the video drivers to go and I will be all set !! :D

---

### Post by mrmonday on 2007-02-26
try:
> 

   1.   Install the xorg-driver-fglrx package from the “Restricted” repository (see Chapter 3, Adding, Removing and Updating Applications).
   2.  To set up the new driver, enter in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
      Agree to automatic detection of your video, and choose the driver fglrx when asked.



---

### Post by Maestro23 on 2007-02-26
> **teedee said:**
> ok, now we are getting there, WiFi is working (I disabled the wired connection in network settings and it started working)

Just the video drivers to go and I will be all set !! :D

Have you tried any of the Integrated drivers over at the ati.com site?

Search: linuxX86>>Integrated Motherboard>>>

[http://ati.de/support/driver.html](http://ati.de/support/driver.html)

---

### Post by teedee on 2007-02-26
just tried, but no success :(

Currently my screen is watchable, however all fonts look jagged and blurred like they are not at a high enough screen resolution, and it won't go any higher without the right driver.

I tried changing font settings but it doesn't help. 

Will get a really bad headache using this for a couple of hours :(

---

### Post by mrmonday on 2007-02-26
try the second post [here]("http://ubuntuforums.org/showthread.php?t=359702")

This is a good solution if you don't want 3D graphics yet... a temporary solution otherwise.

Only do resolutions your graphics card supports...

---

### Post by teedee on 2007-02-26
i edited xorg.conf to include higher resolutions, but they are not available in the screen resolution options.

my xorg.conf looks like 

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
        Modes       "1650x1050" "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
	SubSection "Display"
		Depth		15
        Modes       "1650x1050" "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
	SubSection "Display"
		Depth		16
        Modes       "1650x1050" "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
Subsection "Display"
        Depth       24
        Modes       "1650x1050" "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

but the highest resolution option I have is 1024x768

---

### Post by mrmonday on 2007-02-26
I believe you need to add your resolution to all the subsections... have you restarted your PC? you will need to do this. What is your resolution meant to be? 1200x800?

---

### Post by teedee on 2007-02-26
1200x800 would be good.

I added it to all sections and rebooted. still doesn't show as an option

---

### Post by mrmonday on 2007-02-27
if you are sure that the xorg.conf has the correct resoultions in all the subsections then try ctrl + alt + backspace, hopefully this will work. how are you trying to change your resolution? system>prefrences>screen resolution?

---

### Post by bigken on 2007-02-28
if I were you I would concentrate on one at a time get your wireless running 1st then your video trying to do two things at once will only confuse and get you frustrated for yor network settings go to system/administration/network
select your wireless card and enter the essid your wep and select dhcp let us know how you get on :)

---

