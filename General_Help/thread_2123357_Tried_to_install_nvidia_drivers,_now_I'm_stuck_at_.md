---
title: "Tried to install nvidia drivers, now I'm stuck at the termnial with api mismatch"
date: 2013-03-07
forum: General Help
---

### Post by grandkodiak on 2013-03-07
I decided to install the drivers from nvidia and now I've lost the gui.

I get the ubunutu splash, then it dumps to a shell, and after login I get an error if I try "startx"

The resulting message boils down to this:

"Nvidia API mismatch: kernal module 310.32, however driver component 304.64. fatal server error, no screens found." are the most important details I can gather.

What do I do now? I tried apt-get update then upgrade and a reboot, but it didn't change anything. I'm not a terminal kind of person, so any input would help on how I can update the "driver component" to 310.32, perhaps that will resolve the issue.

Thanks all!

-Brian

(ubunutu 12.10, nvidia gtx470)

---

### Post by oldfred on 2013-03-07
If you can get to command line. I would purge everything, install headers and then install one of the nVidia drivers from Ubuntu.

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by grandkodiak on 2013-03-08
I dont know where on this forum I can select the "solved" status you mention, but it is solved!

I ended up logging in as root and doing the following basics before getting into what you suggested just to make a clean slate sort of:

apt-get update

apt-get upgrade

reboot

nvidia-installer --latest

(go through the prompts to search for newest drivers direct from nvidia instead of the driver .run file I downloaded from the website)

I then ran:

nvidia-installer --update

(go through the prompts to download the latest drivers, accept the ula and proceed with the prompts to install the new drivers over whats already installed. It ran into a script error but had an option to continue anyway, which I did. It then uninstalled "what it could" as it said and exited back to the prompt.)

I then ran:

reboot

(upon reboot, I got a flicker after the Ubunutu flash screen and it went right back to my GUI user interphase completely intact as it was before I tried the initial driver upgrade that resulted in my loss of a GUI. I restarted once more to confirm and all is well. All my icons, resolution and even background image choices were preserved.)

I figure the only explanation is that my download was corrupt, or the trully newest 310.40 that it downloaded over the 310.32 my original download was corrected whatever issue I had.

---

### Post by Paqman on 2013-03-08
The standard Ubuntu tool for dealing with Nvidia drivers actually works fine on the command line. To see the available drivers:
```
jockey-text --list
```
To enable a driver (such as your previous one, or nouveau):
```
sudo jockey-text -e drivername
```
Easy peasy, lemon squeezy.

---

### Post by bogan on 2013-03-09
Hi!, **grandkodiak**,

I see you have found the Quick & Dirty way to re-install or update the nvidia.com downloaded driver.

To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.

The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.

The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.

Chao!. **bogan.**

---

### Post by Elludium_Q-36 on 2013-03-12
Same boat as OP was. :(

I bought a NVIDIA 8871 Ver: 100 (PNY GF4TI00AGP), AGP card and wasn't sure about which driver to use.

Downloading ALL NVIDIA packages was NOT the right move. :(

On that incarnation of Ubuntu, I'm stuck at the command prompt...

Unfortunately there are many on here who just post "REINSTALL", maybe to increast their post count.
That should never be the catch all answer.

---

### Post by bogan on 2013-03-12
Hi!, **Elludium_Q-36**,

You should start your own Thread and post a link here, the OP said he has a gtx470.

The info you gave: "NVIDIA 8871 Ver: 100 (PNY GF4TI00AGP)" does not give any useful data from Google or Nvidia.com.
The nearest I can find is: "Nvidia GeForce 4 Ti 4200 with AGP8x", which would require the 96.xx legacy driver, and probably a Linux prior to 12.04.2

Please Post:```
 uname -ar
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```And describe your actual problem, when it occurs, and the error messages that are shown, as well as the details of your computer, CPU/Memory/Monitor/ etc.

Chao! **bogan**..

---

