---
title: "Cannot open Ubuntu 14.04 without NOMODESET &amp; can not boot Mint 17.3 (New laptop)"
date: 2016-04-02
forum: General Help
---

### Post by ender7 on 2016-04-02
Hi,
Today I am having very terrible times with my 6 hours laptop. I changed my 2-months-old new laptop because GPU does now work well with ubuntu. And again this "new new" one but I get some crazy errors and I am about cry :(
Please share your ideas with me after reading the problems. Should I send back or not.
Firstly, I was getting this error while booting Ubuntu. 
[IMG]http://i.imgur.com/PXuu7io.jpg[/IMG]
I get this console output by hitting F1 when it stuck on splash screen.
Now somehow this problem solved and I can boot ubuntu from USB. I installed successfully. But now I stuck on splash screen if I do not add nomodeset to boot options. 
Anyway, I go into Ubuntu with nomodeset and install Nvidia driver from "additional drivers" and restart what I get is this: Black screen and I hear a sound that when the login screen come out. I hear sound but can not see anything. Even If I switch one of the tty screens I am not able to see it. Any ideas?

Now I want to install Mint 17.3 but I can not boot from USB. I press "Install Mint 17.3 etc..." but it shows me splash then get stuck on "black screen with curser". I can not even install it. I can not get logs by hitting F1 Please tell me what is going on here.

As I said before It is a new laptop. Now please tell me it is a hardware problem or not?
**Dell 7559 [B][COLOR=black][FONT=Verdana]B70F161C[/FONT][/COLOR]**
[COLOR=#000000][FONT=Verdana]Intel® Core™ i7-6700HQ 2.6GHz
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]NVIDIA® GeForce® GTX960M 4GB GDDR5 128Bit
ChipSet: Intel HM170[/FONT][/COLOR][/B]

---

### Post by X-RED_Tech on 2016-04-02
The driver version available for the old 14.04 is probably inadequate for the GTX960M. The rapidly aging 14.04 release is also inadequate as a whole. For such new hardware I would go with 15.10 or even the yet to be released 16.04, the newer the better.
I cannot comment about Mint. Don't know, don't care... What I can say is Mint is based on Ubuntu so for the most part the old Brazilian adage of "exchanging six for half of a dozen" applies.

---

### Post by Bashing-om on 2016-04-02
ender7; Hello;

I see that Nvidia recommends the 361 version driver for that video card:
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)
That driver is not in the 14.04 software repository, but it is available from our trusted PPA.

I do suggest we try this 361 version.
from the F1 console- booted with the nomodeset boot option; 
Terminal commands:
```

sudo apt-get remove nvidia-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt full-upgrade
sudo apt install nvidia-361 nvidia-prime

sudo reboot

```

What I do not know, is IF Mint honors the ubuntu install of the driver. Maybe boot up a ubuntu live Environment and 'test' ? Same for Mint. If all goes well in the live environment, Should then be good in the install.

Do you now boot to the GUI ?

[INDENT][INDENT]kernel has got to have that means
[INDENT][INDENT][INDENT]to talk to the hardware
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-04-02
The new Skylake systems just work better with 16.04 even though not finalized yet. 
You should not rely on it, until it is released.

 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

### Post by ender7 on 2016-04-02
> **Bashing-om said:**
> ender7; Hello;

I see that Nvidia recommends the 361 version driver for that video card:
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)
That driver is not in the 14.04 software repository, but it is available from our trusted PPA.

I do suggest we try this 361 version.
from the F1 console- booted with the nomodeset boot option; 
Terminal commands:
```

sudo apt-get remove nvidia-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt full-upgrade
sudo apt install nvidia-361 nvidia-prime

sudo reboot

```

What I do not know, is IF Mint honors the ubuntu install of the driver.  Maybe boot up a ubuntu live Environment and 'test' ? Same for Mint. If  all goes well in the live environment, Should then be good in the  install.

Do you now boot to the GUI ?
[INDENT][INDENT]kernel has got to have that means[INDENT][INDENT][INDENT]to talk to the hardware
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


First of all I could not understand what you mean last 3 line :(
I  installed 15.10. I opened it with nomodeset and I will try you  commands. I will write in to terminal directly. Is there anything else  needs to be done before it?



> **oldfred said:**
> The new Skylake systems just work better with 16.04 even though not finalized yet. 
You should not rely on it, until it is released.

 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

It seems I am up all night long. It is 22:10 PM here Turkey. I will try steps on first thread and let you know if you still be here :)

---

### Post by ender7 on 2016-04-02
> **Bashing-om said:**
> ender7; Hello;

I see that Nvidia recommends the 361 version driver for that video card:
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)
That driver is not in the 14.04 software repository, but it is available from our trusted PPA.

I do suggest we try this 361 version.
from the F1 console- booted with the nomodeset boot option; 
Terminal commands:
```

sudo apt-get remove nvidia-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt full-upgrade
sudo apt install nvidia-361 nvidia-prime

sudo reboot

```

What I do not know, is IF Mint honors the ubuntu install of the driver.  Maybe boot up a ubuntu live Environment and 'test' ? Same for Mint. If  all goes well in the live environment, Should then be good in the  install.

Do you now boot to the GUI ?
[INDENT][INDENT]kernel has got to have that means[INDENT][INDENT][INDENT]to talk to the hardware
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I installed 15.10 with nomodeset and log in to desktop with  nomodeset and followed your commands and its work! Thank you very much. I  will try it with 14.04 too.



> **oldfred said:**
> The new Skylake systems just work better with 16.04 even though not finalized yet. 
You should not rely on it, until it is released.

 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

It seems 16.04 is the way to go. I did not use nomodeset for boot or login to desktop. But I was getting the error that I mentioned in first post on shutdown/restart. After the nvidia drive installation it disappeared. Thank you very much for your help.

On the other hand, I was having trouble with monitor. I could only test it 16.04 with nvidia driver installed. When I plugged in HDM cable after 4-5 seconds Ubuntu stucks. I can not do anything. Tomorrow I will try to provide some more information If I can get more. I hope you could help me on this too :)

---

### Post by Bashing-om on 2016-04-02
ender7; Great;

Pleased things are working out.
As the original question has been addressed ;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
And open a new thread on this new issue. That gains a targeted audience with greater visibility.

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

