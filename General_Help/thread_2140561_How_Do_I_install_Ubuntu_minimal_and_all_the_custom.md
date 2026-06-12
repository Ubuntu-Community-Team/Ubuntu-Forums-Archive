---
title: "How Do I install Ubuntu minimal and all the customized components?"
date: 2013-04-30
forum: General Help
---

### Post by chetanbhasin on 2013-04-30
[COLOR=#333333][FONT=Ubuntu Beta]I'm new to the world of Linux to don't know all the fancy words. So here is my problem...[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I was using Ubuntu 12.04 on my laptop HP Envy 4 1046TX and had issues like low battery backup, heating etc.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]A friend of mine suggested that I install Ubuntu minimal and install all the components that I require. Now, I have a little problem understanding how I can do that.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]First of all, minimal installer only gives me a terminal, right? So, how do I add up the required stuff? Use apt-get? Please help![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Second, how do I find drivers that are specifically meant for my machine? If I stuff up all the drivers standard install comes with then I believe the problem of low battery backup might still continue, so I'm gonna have to find specific drivers and a way to install them.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]P.S. There is an MD5 given with every ISO in minimal ISO page. What does that mean?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Plesase take me as a novice and explain in simplest way possible.[/FONT][/COLOR]

---

### Post by zero2xiii on 2013-04-30
Good day,

Firstly MD5 is a hashing method. Aka a way to check that a file is not corrupted during download:
File on server > MD5 = 1234
File on computer > MD5 = 1478
Then file on server is NOT file on computer.

So do not worry about that TO much. If you have issues during install or something then you might consider a corupted download, but if it was downloaded one shot (not paused and resumed etc) there should not be any issues usually.

Then on to the minimal install. In my personal opinion, it is a waste of time and resources downloading a minimal image and then just installing everything manually that is included on the vanilla install disks. However if you do wish to go this route here are some of the basics you will need to get a desktop environment. I will post gnome3, so you will essentially end up with a full vanilla install of ubuntu. May I recommend a lighter release such as Xubuntu or Lubuntu? This should help with battery life a bit. Also, ubuntu is not quite laptop/notebook optimized so battery usage is somewhat higher than windows. There are a few tweaks to help, but that is all they are and do, tweaks that help.

Oka enough yada yada:
For gnome:
```
sudo apt-get install ubuntu-desktop
```
For KDE:
```
sudo apt-get install kubuntu-desktop
```
For XFCE:
```
sudo apt-get install xubuntu-desktop
```

also on a CLEAN install you can try:
```

sudo apt-get install tasksel
sudo tasksel
```

I see this is the recommended way on the download site [here]("https://help.ubuntu.com/community/Installation/MinimalCD"):
> To install, boot your computer from the the Minimal CD and type "cli" (command line install) at the prompt. You can then follow the instructions from the text-based installer. After the base system is installed, log in, and type "sudo tasksel" to select the system to install.

That should cover it. But just for reference see this post:
[http://ubuntuforums.org/showthread.php?t=1225523](http://ubuntuforums.org/showthread.php?t=1225523)
It is somewhat outdated but it gives you an idea of what to look for if you run into some trouble along the way.

Cheers

EDIT:
For a quick comparison of desktop environments and shells see here:
[http://scriptevolution.com/blog/2012/08/top-10-ubuntu-desktop-environments-and-shells/](http://scriptevolution.com/blog/2012/08/top-10-ubuntu-desktop-environments-and-shells/)

---

### Post by Neill_R on 2013-04-30
I also joined the Ubuntu (Linux) community with xubuntu 9.04 and then switched to Ubuntu 9.10. Now running a Ubuntu server 12.04 which is joined to a Windows Active Directory domain by means of Centrify Diect control software

---

### Post by fantab on 2013-04-30
> **chetanbhasin said:**
> [COLOR=#333333][FONT=Ubuntu Beta]I'm new to the world of Linux to don't know all the fancy words. So here is my problem...[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I was using Ubuntu 12.04 on my laptop HP Envy 4 1046TX and had issues like low battery backup, heating etc.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]A friend of mine suggested that I install Ubuntu minimal and install all the components that I require. Now, I have a little problem understanding how I can do that.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]First of all, minimal installer only gives me a terminal, right? So, how do I add up the required stuff? Use apt-get? Please help![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Second, how do I find drivers that are specifically meant for my machine? If I stuff up all the drivers standard install comes with then I believe the problem of low battery backup might still continue, so I'm gonna have to find specific drivers and a way to install them.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]P.S. There is an MD5 given with every ISO in minimal ISO page. What does that mean?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Plesase take me as a novice and explain in simplest way possible.[/FONT][/COLOR]

Seriously, "minimal install" is not for Linux newbs. Its for those who know what they need to make their systems run, with all the required drivers, libraries and dependencies and can troubleshoot their way through.
Download and Install from the regular Ubuntu.iso. As suggested XUBUNTU and LUBUNTU consume less system resources and are more suitable to your problems. I would suggest you go with [Lubuntu]("http://lubuntu.net/").

I suggest you check with your HP "customer-care" or "Service" to see if the problems you are having are part and parcel of the HP you bought or is there any other problem with it. If there is any Hardware problem then installing Ubuntu is not a solution.

---

### Post by chetanbhasin on 2013-05-10
Thanks a lot zero2xiii. It really helped a lot! :D

---

