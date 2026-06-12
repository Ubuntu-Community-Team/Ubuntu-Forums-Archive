---
title: "Optimizer Pro"
date: 2014-04-11
forum: General Help
---

### Post by czmacbudder on 2014-04-11
Okay so I choose to run 14.04 as my main os and I new there would be a few bugs but this isn't with ubuntu I installed a package from "CNET" and it gave me some thing called "Optimizer Pro" I tried to uninstall it and I got a red sign at the top of my bar I just ignored it then I rebooted and had a ton of error reports coming I have a few screenshots if you would like to see it I cant get one of optimizer though Screenshot: [http://imgur.com/JEvtxHK](http://imgur.com/JEvtxHK)

---

### Post by gifford on 2014-04-11
You have tried to install a "windows" program that is not compatible with Linux.
It is not a "bug" with Ubuntu but is something you have done that you should not.
What is your system, dual boot with windows?
If not, how long have you had Ubuntu 14.04 installed?

---

### Post by czmacbudder on 2014-04-11
> **gifford said:**
> You have tried to install a "windows" program that is not compatible with Linux.
It is not a "bug" with Ubuntu but is something you have done that you should not.
What is your system, dual boot with windows?
If not, how long have you had Ubuntu 14.04 installed?

About a week now I don't duel boot I deleted windows and I just want to know how to remove optimizer

---

### Post by gifford on 2014-04-11
Without more information I would not know where to start. If it were me and this is a new installation, I would reinstall 14.04 and start over.
A good rule of thumb is to only install software using the Ubuntu software center or synaptic package manager. It will prevent you from 
making mistakes like you did.
Also, check with the user forum if you have any doubts before attempting to do something that could harm your system.
You cannot install windows program in Ubuntu...Linux is not windows.

---

### Post by czmacbudder on 2014-04-11
I know I only installed it because it came with cnet -.- isnt there a add and remove software thing

---

### Post by gifford on 2014-04-11
There is but it is for Ubuntu Linux apps...not windows. I do not know how badly your system is damaged.
Also, for future reference you should post in the general help forum or absolute beginners section. You will get more responses with better advice.

---

### Post by craig10x on 2014-04-11
And remember...never try to install an .exe file (windows file) ubuntu linux uses what is known as debian files...actually called deb files for short...
So, as your preference, try to use ubuntu software center to install programs whenever possible and if you are installing from a web site it must be a program that works with linux and that they provide a deb file for...

Normally, those "outside" deb files can be installed by Ubuntu Software Center but there is a current bug that may prevent one from doing that...if that is the case, then you can install a program called gdebi from the Software Center which will be able to install any deb file..I'm sure that bug should get corrected soon...

As they mentioned, if you had somehow got this .exe windows file to install, no doubt it probably messed things up in your system, so best bet is to just do a nice clean install of 14.04 and that will take care of it...now, you know better for the future ;)

---

### Post by lykwydchykyn on 2014-04-11
Is it possible this software was installed in WINE?  If so, there's no need to reinstall ubuntu, just delete your ~/.wine folder.  If you use any other software in WINE you'll need to reinstall it, of course.

---

### Post by czmacbudder on 2014-04-11
> **lykwydchykyn said:**
> Is it possible this software was installed in WINE?  If so, there's no need to reinstall ubuntu, just delete your ~/.wine folder.  If you use any other software in WINE you'll need to reinstall it, of course.

Thanks so much you actually helped me unlike anyone else! how do I delete it though?

---

### Post by monkeybrain20122 on 2014-04-11
The red thing is just a notification. It doesn't have to be errors, it could be something trivial like reminding you to update. What happens when you click on it?

If that has been installed through wine all your need is to delete the hidden file .wine and  all launcher files in .local/share/applications/wine

Edited: Not sure what you downloaded from cnet, this is apparently a 'registry cleaner' which in some ways behaves like a malware. [http://malwaretips.com/blogs/pc-optimizer-pro-virus/](http://malwaretips.com/blogs/pc-optimizer-pro-virus/)
Of course the 'how to remove' guide from the link doesn't apply. Just delete the hidden folder .wine in your home and you are good.

---

### Post by craig10x on 2014-04-11
You didn't mention that you had installed it in wine...for all we knew, you had somehow installed it on your main system...wine of course, you would use .exe files...try some of the suggestions they had mentioned...
wine is kind of a separate entity from the main linux system you are using...

---

### Post by czmacbudder on 2014-04-11
> **monkeybrain20122 said:**
> The red thing is just a notification. It doesn't have to be errors, it could be something trivial like reminding you to update. What happens when you click on it?

If that has been installed through wine all your need is to delete the hidden file .wine and  all launcher files in .local/share/applications/wine

Edited: Not sure what you downloaded from cnet, this is apparently a 'registry cleaner' which in some ways behaves like a malware. [http://malwaretips.com/blogs/pc-optimizer-pro-virus/](http://malwaretips.com/blogs/pc-optimizer-pro-virus/)
Of course the 'how to remove' guide from the link doesn't apply. Just delete the hidden folder .wine in your home and you are good.

Alright that helped a lot I can't seem to find the "applications folder"

---

### Post by coffeecat on 2014-04-12
Support question, not an Ubuntu, Linux and Other OS Chat thread.

*Thread moved to **General Help**.*

> **czmacbudder said:**
> you actually helped me unlike anyone else!

That is uncalled for. Everyone was trying to help you. You did not give relevant information to start with.

---

### Post by 3rdalbum on 2014-04-12
> **czmacbudder said:**
> Alright that helped a lot I can't seem to find the "applications folder"

Copy and paste this into the terminal:

```
nautilus ~/.local/share/applications/wine
```

Alternatively you can just delete the whole ".wine" folder from your home directory, which will erase all Windows programs you've installed in Wine:

```
rm -rf ~/.wine
rm -rf ~/.local/share/applications/wine
```

---

### Post by stalkingwolf on 2014-04-12
wine used to have a remove / uninstall software option.

---

