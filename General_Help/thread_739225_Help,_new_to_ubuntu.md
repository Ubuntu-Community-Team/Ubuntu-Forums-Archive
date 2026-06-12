---
title: "Help, new to ubuntu"
date: 2008-03-29
forum: General Help
---

### Post by eunos_91 on 2008-03-29
Hi all. You may be able to tel I'm new to the Linux scene. I've had a burning curiousity about alternate OS's for a long time. Doing some research I decided to go with Ubuntu Linux. Okay, enough rambling, on to the issue...

I have installed 7.10 on my spare machine to check it out. All around it runs pretty good... well, for as long as I can use it. After about five minutes from startup the whole system freezes. I've left it for hours one time and it never comes back around.

Any idea as to what is up? I am an experienced Windows (boooo) and Mac OS user and catch on fast to these sort of things. I want to try my hand at learning to use Linux efficiently and maybe someday learn the ins and outs of moddifying. 

So... maybe try re-installing? BTW on a separate partion there is a perfect running RTM build of Vista, which never locks up. Thanks in advance!

---

### Post by drhou on 2008-03-29
Can you get into the interface or it gets stuck on the boot splash screen?

I never liked installing a Ubuntu directly from the latest distribution, I always install Ubuntu 6.10 Edgy-Eft first and then upgrade through the updating manager. It sounds lame but thats the only way my machine(s) will tolerate (-_-')

---

### Post by danwood76 on 2008-03-29
YOu could have a go at re installing, it never hurts.
I would also do a media check of the install cd.

---

### Post by drhou on 2008-03-29
I think I had the same problem too when I installed Gutsy. The screen goes blank (and shows no signal) after loading from GRUB, so I stayed with Feisty.

---

### Post by Sidewinder1 on 2008-03-29
Try going to "Systems....>Power Management....>On AC Power...and set actions and display to never. Not sure that this will work but it can't hurt.
HTH

---

### Post by IceaTronic on 2008-03-29
Uhm, i think he cant even get to that screen before it locks up on him.

Perhaps a  resintall with that settng would work?

---

### Post by Dr.Ninethousand on 2008-03-29
> **danwood76 said:**
> 
I would also do a media check of the install cd.

yes..  I used to have a lazy habit of not checking md5sums and assuming everything would be fine..

it really is worth checking, a lot of little things can get broken in a 600+mb download..

---

### Post by eunos_91 on 2008-03-29
I can get to the interface, and can do some things for about five minutes. Then the mouse will cursor freezes, keyboard input does nothing, hdd light goes solid, any status bar I may have up stands still, and if I'm on the web and moving ad will freeze also.

I suppose I'll try a new install, if I have the issue again I may take the advise of downloading older version. Also FYI I did the install from the huge DVD version, also downloaded the small CD version, but the little version checked out bad when I tried using it. These were both mounted with Nero 7. 

P.S. Whats with the funny names for the different versions?

---

### Post by danwood76 on 2008-03-29
So have you installed this through wubi?

The funny names are like a second version number as I understand it.
Gutsy Gibbon, G = 7 and is the 7th ubuntu release.
Hardy Heron, H = 8 is the 8th release.

The first few didnt adhire to this scheme.

---

### Post by Miljet on 2008-03-29
Actually, the release numbers refer to the year and month of the release. Gutsy was released in October of 2007, hence the release number is 7.10. Hardy is scheduled to be released in April of 2008 and will be 8.04.

All releases are nicknamed with an adjective and the name of an animal, both beginning with the same letter (ie: fiesty fawn, dapper drake, gutsy gibbon, etc)

---

### Post by eunos_91 on 2008-03-29
I see... I have lots to catch up on. 

and wubi = ?

I've actually solved the issue though, it was happening when it was using my wireless card to access the internet or updates. Evidently it doesn't like my ancient D-Link card. Hooked up to strait LAN and everything is fine!

Thanks to all!!! I'm sure this won't be the last...

---

### Post by danwood76 on 2008-03-30
I bet your D link card has an intel chipset, I had the same issue a few weeks ago on a PC I was building.
You can get your wireless going through ndiswrapper if you blacklist the linux driver for your card and load up the windows drivers through ndiswrapper instead.

Wubi is the way of installing from within windows.

@miljet
The same letter that the release name begins with is the release number.
After Hardy heron it is Intredip Ibex. Slowly working through the alphabet.
But yes the number infront is the date it was released.

---

### Post by eunos_91 on 2008-03-30
Ok, I'll see what I can do with that ndiswrapper thing.

I installed this booting from the DVD, starting the live version and installing from the desktop. It all seems to be running great now, I'm quickly learning little things like getting Flash to work and whatnot. I'll have to read up on the ndiswrapper now lol.

Thanks again!

---

### Post by danwood76 on 2008-03-30
When you do the ndiswrapper stuff you will need to blacklist the module thats being loaded for your wifi card otherwise it will continue to crash your system.
If you say what model number the card is I can probably give you a step by step guide on blacklisting the driver.

---

### Post by eunos_91 on 2008-03-30
D-Link DWL-520 V.D1 is the card. Still haven't found process for ndiswrapper yet, but may tonight sometime.

I can't believe how helpful people are one this forum. Thanks again!

---

### Post by danwood76 on 2008-03-31
To blacklist the module you first need to reboot into recovery mode.
This can be done by pressing excape when grub pops up and selecting recovery mode.

Once its loaded you should be presented with a command line (dont be scared of it its your friend)
Then type this:
```

nano /etc/modprobe.d/blacklist

```
this will open up a text editor with your blacklist file.
add the following line to the end on a new line:
```

blacklist hostap_pci

```
then press ctrl+o to save and ctrl+x to exit.
thats the module blacklisted so it shouldnt crash your system now.
type this to shutdown:
```

shutdown -h now

```
insert your wifi card again and boot if it crashes then I may have found the wrong chipset for your card, if it doesnt then you can start trying the ndiswrapper method:
[https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)

If your system still crashes reboot into recovery mode and type this:
```

lspci | igrep wireless

```
that should dump the chipset of your card, please post it here and I will find out which module is being loaded.

---

