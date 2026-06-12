---
title: "nvidia black screen after boot"
date: 2007-01-06
forum: General Help
---

### Post by oliwally on 2007-01-06
**_Edit: Problem solved - see 2nd post below._**

I'm sorry to bring up a much covered topic, but I just cannot get the xserver to start after boot. I'm left with a black screen. I've just done a fresh Edgy Kubuntu install on my computer. The previous install (dapper) worked well (including Nvidia drivers etc). I haven't changed any of my hardware.

Here are the details for the computer: Athlon XP 2600+ with onboard video AND I have installed a Nvidia Gforce 4 64MB. I chucked in the Nvidia because I couldn't get the onboard video to be any good in Kubuntu. This arrangement has always worked well until now.

If I take the Nvida card out and use the onboard video, X starts and I can use Kubuntu, but when I try to use the Nvidia card, X does not start and I'm left with a black screen after boot.

I have tried to install the Nvidia drivers according to the instructions at [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851) (method 1) and also tried the instructions at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

I eventually want to get Beryl going (hence the fresh install)

I've also tried Automatix2, but since the nvidia card is unplugged when I run Automatix2 it says that it can't find a nvida card (logically). 

I have read posts and advice for hours and hours but without luck. I've tried many different things but all leave me with the same result.

Could someone please help me to get my nvidia configuration going. I know it's possible - it worked before.

---

### Post by oliwally on 2007-01-06
Problem Solved !!!

I stumbled upon the 'envy' script by Alberto Milone aka tseliot on this forum. Thanks so much Alberto - total magic!

Find it at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

For those who may have the same problem (and know just as little as me ;) ), I ran into just one problem, when my command line disappeared. Here's what I did in a nutshell, but make sure to follow Alberto's instructions closely:

- With Nvidia card unplugged (X / Desktop Environment working) download and install the Envy   
  script
- Plugged in my Nvidia card and booted up - got black screen again
- Do a Ctrl Alt F1 to get into a command line
- Log in
- Make sure internet is connected and working
- Type ' envy ' at command line (as instructed) and follow prompts
- This is where the command prompt disappeared for some time. I waited 'til all the
  downloading and computer had settled down (watched the blinking lights on modem and 
  computer) and then did a Ctrl Alt F1 again and I had the command prompt (and the 
  still-running envy installation) back.
- Follow the prompts and - tadaaaaa. Faaaaaantastic!

---

