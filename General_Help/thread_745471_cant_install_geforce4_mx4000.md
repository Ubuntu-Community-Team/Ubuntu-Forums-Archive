---
title: "cant install geforce4 mx4000"
date: 2008-04-04
forum: General Help
---

### Post by domace on 2008-04-04
I'm I complete beginner in Ubuntu, I've read the most user friendly how to's but I still am not able to install my  geforce4 mx4000 for pci in Ubuntu, i need help and step by step, I like the feel of Ubuntu so much i uninstalled a genuine windows xp and i have no cd but i need to do this to use compiz in ubuntu please help me out.

---

### Post by forestpixie on 2008-04-04
What have you done up to now trying to get it installed?

---

### Post by domace on 2008-04-04
I reinstalled ubuntu so nothing at this point

---

### Post by forestpixie on 2008-04-05
First thing to do is to use restricted driver manager in system > admin and then post if you have problems

---

### Post by domace on 2008-04-05
what do i do from there? my video card isn't inserted in the pci slot yet should i insert it?

---

### Post by domace on 2008-04-05
it says my hardware does not need restricted drivers

---

### Post by forestpixie on 2008-04-05
You need to fit the card yes and then reboot - are you saying you have and it has booted up ok?

---

### Post by domace on 2008-04-05
nope its not connected to the pci slot yet should i shutdown connect it then reboot using the embedded video card in the mother board or pci

---

### Post by FreakerBeaker on 2008-04-05
I'm new to Ubuntu as well, but have had my share of nvidia problems.  Did you say you had the card fit into the slot or not?

---

### Post by domace on 2008-04-05
ok i found out the first step, go to bios and disable pci vide card and then use onboard video to boot and install restricted drivers then what???????????

---

### Post by FreakerBeaker on 2008-04-05
When you try to boot using the PCI card, do you receive a black screen.  What happens exactly if you don't mind me asking?

---

### Post by domace on 2008-04-05
umm ya i have it in the pci slot with restricted driuvers installed, should i enable pci video card but when i enable it i cant use onboard video card and i have installed envy-woooot im getting better at this

---

### Post by domace on 2008-04-05
i get a black screen but this is befor i installed the restricted drivers i havent tried rebooting it again with pci

---

### Post by forestpixie on 2008-04-05
If you want to use the pci card you need to disable the onboard video, fit the card and reboot. If you want to use onboard BIOS should be set to onboard and remove the pci card.

When you reboot it will probably leave you at a command prompt, use this command - answer questions that you can - but when it comes to choosing graphics pick nv or nvidia - can't remember which comes up.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It should then let you in and you can go the restricted driver way from there

---

### Post by forestpixie on 2008-04-05
If you don't get to a prompt - recovery mode and use the command

---

### Post by domace on 2008-04-05
alright im trying it now

---

### Post by domace on 2008-04-05
nope i get a black screen and i put auto in bios so that picks pci video card i get black screen after loading screen i installed the restricted drivers whats happening?

---

### Post by domace on 2008-04-05
freaker beaker are you having the same problem as me?

---

### Post by forestpixie on 2008-04-05
What happens when you boot in recovery mode and run the dpkg-reconfigure command?

You might of installed the restricted driver, but if you did it before the card was installed and working it wouldn't know it was there, it needs to be done after the card has been installed afaik.

You will keep getting the balck screen until you've told the system that the new card is there, which is done with the command I gave above.

---

### Post by domace on 2008-04-05
yep i tried it goes into a command screen after loading i type it in and nothing happens

---

### Post by domace on 2008-04-05
im going to have to reinstall ubuntu i messed up plz give me a step by step tutorial plzzzzz, i searched for simple one but i still dont understand

---

### Post by forestpixie on 2008-04-05
Well I don't know why the command is doing nothing? 

Are you sure you're entering it correctly.

You should be in this state - at least this is where I think you are :)

PCI card is fitted correctly
BIOS has onboard graphics disabled

When you boot to the recovery mode what happens? Try running the command again.

---

### Post by forestpixie on 2008-04-05
Trry the command one more time - if you do reinstall - make sure that the nvidia card is installed first before you boot the livecd - I'm assuming you're trying to install gutsy.

---

### Post by domace on 2008-04-05
i reinstalled so i have a fresh clean install and i installed with the pci connected but not in use so what is the first thing i should do, remebr this is a fresh install, and my bios only gives me to option- auto(which uses the pci card but i dont know if it dibles the onboard one and onboard only so what should i do and thx for puting up wit me  =]

---

### Post by forestpixie on 2008-04-05
Oh - so you can't disable the onboard - didn't know that. I would open restricted driver manager and see what it says - if it says there is no hardware that needs a driver it's not recognising the card.

You could also try using the envy tool - [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) - if that doesn't work then I would say that you need to try and get the inf regarding your motherboard and the auto option.

Thanks for the thanks - but the same as everyone else here - wouldn't do it if I didn't want to :)

Good luck.

---

### Post by domace on 2008-04-05
can you give me directions using envy

---

### Post by forestpixie on 2008-04-05
go to the site - if you're using hardy download the two for either gnome or kde - if you're on gutsy the other one - envy legacy I think - it will download to you're desktop.

Double click the downloaded file and it will install it. Believe it goes in application > system tools - start it from there - use it to download and install the nvidia driver. If it works you'll need to restart.

---

### Post by domace on 2008-04-05
i did installed the driver and everything just one problem, i think i need to turn of the onboard video card in order for this to work but i have a dell from like 2004 and any most dell pc's from 2005 and and back dont give you the option in bios to disable the onboard video card and my motherboard doesnt have i jumper cable i can unplug to turn it off...man i think im screwed...hmmm what about if i just install the restricted drivers?

---

### Post by domace on 2008-04-05
If I use the restricted drivers manager to install the nvidia driver which is on the current list of supported legacy devices should I be able to plug my monitor into the new pci video card while having the on board video card enabled but not in use?

---

### Post by lswest on 2008-04-05
setting the BIOS as "auto" and plugging the screen into that pci card should disable the onboard.  If you get a black screen, try changing the driver used to VESA and then re-installing (while the monitor is plugged into the pci card) the drivers you need.  To change the driver: ```
gksudo gedit /etc/X11/xorg.conf
``` and change the line that probably reads something like 'Driver "nv"' to 'Driver "vesa"' for the nvidia card.

---

### Post by domace on 2008-04-05
ok i'll try that and by reinstall you mean envy or restricted drivers?

---

### Post by domace on 2008-04-05
LOL!! the problem was the pci number was wrong thx every1 for your help i got compiz running an now i can watch youtube...

---

### Post by blackbird020377 on 2008-07-17
hello... i have a nvidia geforce4 mx 4000 and this is what i have done for it to work.

1. remove all previous nvidia driver, nvidia settings and nvidia-xconfig
2. restart your pc
3. set temporary setting for your screen/display
4. install nvidia-glx
5. run nvidia-xconfig on terminal
6. install nvidia-settings
7. restart your pc
6. viola! your nvidia geforce4 mx4000 is now working

---

