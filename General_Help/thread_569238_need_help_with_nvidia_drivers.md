---
title: "need help with nvidia drivers"
date: 2007-10-06
forum: General Help
---

### Post by FreeThePenguin on 2007-10-06
i have been researching for several hours not and nothing seems to work, i have my graphics driver downloaded i just need to get it installed, when i run the paqckage it tells be i have to have root access,  sudo doesn't work either, envy wont even install it says: dependency is not satisfiable: build-essential,

im on my last nerve, and ready to throw ubuntu in the trash,,, its 64bit feisty btw

---

### Post by climatewarrior on 2007-10-06
Have you tried using the restricted drivers manager instead?

---

### Post by climatewarrior on 2007-10-06
What nVidea card do you have exactly?. And did you download the drivers directly from nvidea or  when you say that you downloaded the drivers you mean envy? And have you checked if you they are already installed?

Ubuntu can sometimes be hard to set up. But after that you should have an extremly smooth and stable experience, maybe even more than with windows or mac. At least that was my experience.

---

### Post by oldos2er on 2007-10-07
> **FreeThePenguin said:**
>  envy wont even install it says: dependency is not satisfiable: build-essential, 

 In a terminal, type sudo aptitude install build-essential
then try re-running envy.

---

### Post by FreeThePenguin on 2007-10-07
well there are two GeForce 8800 GTS's, i d/l the drives from nvidia, and i tried the sudo... install command and it couldn't find build-essential.  btw i can't use the restricted driver manager because i can't get my network working either.

---

### Post by climatewarrior on 2007-10-07
I think it is best if you let the restricted drivers manager take care of your nvidea driver for the following reasons

a) you wont have to do anything when you do a kernel upgrade
b) you wont have to do anything when you upgrade your Ubuntu from one version to another. 

For this reason I suggest that you connect to the internet via ethernet if you have an ethernet card and it is working. And try to get yout nvidea card setup with the restricted drivers manager.

Also as far as I know envy also needs internet to fetch your nvidea drivers and install them.

If you dont have any way to conect to the internet without a wireless card the i suggest you setup your wireless card by dowloading the dirvers needed for it from another computer. I would be glad to help you out with doing this.

You could also just wait for someone with more experience and knowledge than me to come up with a better solution.

I hope you are able to solve your problem very soon.

---

### Post by FreeThePenguin on 2007-10-07
ok, thats sound like a better option, i have posted a thread about the [Wi-Fi]("http://ubuntuforums.org/showthread.php?t=570040") i anyone can help with that.

---

### Post by distroman on 2007-10-07
I don’t think you’re card is supported by the Restricted Drivers Manager, so you need to go with either envy which will install them for you or install them you’re self.

I do think 8xxx series will be supported in gutsy gibbon that comes out the 18 October. 

You will need (or it will be much easier anyway) a working connection so do focus on you’re wireless.

---

### Post by thegreatbeste on 2007-10-07
The build-essential package is needed for the installation of your driver.

so you open up the terminal and type

  sudo apt-get install build-essentials

To get wireless to work it is helpful if you also install the wlanassistant from KDE

  sudo apt-get install wlassistant


afterwards you run it with "sudo wlassistant" and you get a nice graphic wireless config tool

But back to your driver problem.
I assume you want to run your gfx in SLI and for this you will need the drivers from nvidia.
Check the first post in [here](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
like build-essentials you install the tools via: sudo apt-get install *toolname* 

I am also having some problems with my Nvidia drivers but i think this is due to my GeforceGo which is not supported or something. had the same problem on XP too.

But, be careful! Make sure you are able to build up an internet connection before uninstalling any old nvidia driver. As soon as you have no Nvidia driver installed and you reboot, your xserver cant start, which means you are left alone with the commandline.

Either have a LiveCD nearby or do the following:

if you have an ethernet connection to a router just type 
sudo ifconfig eth0 up 

simply type ifconfig to find out your network devices if the above command is not working with eth0

as soon as you have an internet connection and are lost, type
   sudo apt-get install nvidia-glx

and 
   sudo nvidia-xconfig

So the standard Nvidia driver will be reinstalled and you will be able to get some help








And to most of the other people that have answered in this thread, why do you bother explaining and instead just tell the threadstaarter not to change anything?
I am sorry i do not understand this behavior.
Learning is a result of trial and error

---

### Post by distroman on 2007-10-08
> **thegreatbeste said:**
> And to most of the other people that have answered in this thread, why do you bother explaining and instead just tell the threadstaarter not to change anything?
I am sorry i do not understand this behavior.
Learning is a result of trial and error
Cheerio, old chap. :)

For reference if the OP needs it.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

I don't run SLI so can't help there.

---

