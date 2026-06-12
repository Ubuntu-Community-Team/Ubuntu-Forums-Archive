---
title: "Overheating in HP Pavilion dv6 and AMD Catalyst cannot be installed"
date: 2013-06-03
forum: General Help
---

### Post by Peptid on 2013-06-03
Dear All,

I know that this is a general problem with HP Pavilion series. I have a hp pavilion dv6 series laptop with windows 7 and ubuntu 12.04 dual boot. It has ATI Radeon 4650 graphics installed.

My problem is, although no overheating happens in windows, ubuntu overheats no matter how hard the fans operate. General temperature range is around 75-80 celcius when idle.

I have tried to download and install AMD Catalyst 13.1 Legacy driver from ATI website, for 32 bit. At the end of the installation, `installation is  done` prompt appears, after immideatly closing it, `there are several errors during installation, see ....log file` prompt appears. In the log file, 

[Error] Kernel Module : Failed to build fglrx-8.97.100.7 with DKMS
[Error] Kernel Module : Removing fglrx-8.97.100.7 from DKMS

errors are present. I also add the full log file at the end of the thread.

I also cannot start AMD catalyst centre since it says either no drivers are installed or not functioning properly. Moreover, ubuntu turned back to low graphics mode (I use unity, by the way) and now it is very unpleasant to use. 

System graphics in `Details` show graphics as VESA:m96. 

This problem is present since I first installed ubuntu two years ago, but now I have enough time to deal with it. 

Any help would be much appreciated.

Log file (usr/share/ati/fglrx-install.log)

Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Dryrun uninstall succeeded continuing with installation.
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.
Forcing uninstall of AMD Catalyst(TM) Proprietary Driver.
No integrity verification is done.
restore of system environment completed
Errors during DKMS module removal
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
/usr/share/ati/amd-uninstall.sh completed with 0

Creating symlink /var/lib/dkms/fglrx/8.97.100.7/source ->
                 /usr/src/fglrx-8.97.100.7

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.97.100.7/build; sh make.sh --nohints --uname_r=3.5.0-31-generic --norootcheck.....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.97.100.7 with DKMS
[Error] Kernel Module : Removing fglrx-8.97.100.7 from DKMS

------------------------------
Deleting module version: 8.97.100.7
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs

---

### Post by Mark Phelps on 2013-06-03
If you installed Ubuntu recently, it's likely that you installed 12.04.2 -- and that version uses the newer X-server version that is incompatible with AMD restricted drivers that work with your card. IF that's the case, you'll need to uninstall the restricted drivers and use the default Radeon drivers, instead.

You can find out what kernel version you're using by opening a terminal and entering "uname -r".

---

### Post by Peptid on 2013-06-03
> **Mark Phelps said:**
> If you installed Ubuntu recently, it's likely that you installed 12.04.2 -- and that version uses the newer X-server version that is incompatible with AMD restricted drivers that work with your card. IF that's the case, you'll need to uninstall the restricted drivers and use the default Radeon drivers, instead.

You can find out what kernel version you're using by opening a terminal and entering "uname -r".

Yeah, you're right, I am using 12.04.2 Do you think that uninstalling the restricted drivers and use default Radeon drivers would solve the heating problem? Also, how can I remove these restricted drivers?

My kernel version is 3.5.0-32-generic.

---

### Post by Mark Phelps on 2013-06-03
> **Peptid said:**
> Yeah, you're right, I am using 12.04.2 Do you think that uninstalling the restricted drivers and use default Radeon drivers would solve the heating problem? 
Unfortunately, no.  The default Radeon drivers do not provide the ability to control the GPU temps, as do the restricted drivers.

> Also, how can I remove these restricted drivers?

My kernel version is 3.5.0-32-generic.

See the following: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Peptid on 2013-06-04
Mark, thank you for your replies. After reading your posts and searching through the web a bit more, I believe I come up with a possible solution.

First I made a clean install of 13.04, but that did not solve the problem. I found the solution that

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install fglrx-legacy

commands solve the problem. The computer is working for several hours, and although the outside temperature is around 30 celcius, computer temperature dwells around 55 celcius with 10% cpu usage, also the fans are not screaming anymore.

---

### Post by mastablasta on 2013-06-04
> **Mark Phelps said:**
> If you installed Ubuntu recently, it's likely that you installed 12.04.2 -- and that version uses the newer X-server version that is incompatible with AMD restricted drivers that work with your card. 

that's really dumb. i am sure it's AMD's fault (=not). Ubutnu could recognise which card you have and use propper kernel. especially since this is LTS.

> **Peptid said:**
> Mark, thank you for your replies. After reading your posts and searching through the web a bit more, I believe I come up with a possible solution.

First I made a clean install of 13.04, but that did not solve the problem. I found the solution that

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install fglrx-legacy

commands solve the problem. The computer is working for several hours, and although the outside temperature is around 30 celcius, computer temperature dwells around 55 celcius with 10% cpu usage, also the fans are not screaming anymore.

that's a bad idea. it can break drivers and maschine sooner or later with an update (unless you do updates which is a bad idea again).

a better solution is to install older version of LTS (12.04.1) and use the older kernel. if this is at all possible.

---

### Post by |{urse on 2013-06-04
The older dv6s are 'AWESOME' for collecting dust inside the cpu fan. You probably don't even need to take it apart, blow it out real good with a can of air duster and see if it helps. Which model of dv6 is it?

---

### Post by Feathers McGraw on 2013-06-04
I have a very similar laptop (a different HP Pavilion dv6) and had the same problem as you, I couldn't get the graphics working in Ubuntu without overheating.

Try using Kubuntu 12.04 with the fglrx driver, the two are compatible and took 25*C off my temperature :).

Feathers

---

### Post by Feathers McGraw on 2013-06-04
> **|{urse said:**
> The older dv6s are 'AWESOME' for collecting dust inside the cpu fan. You probably don't even need to take it apart, blow it out real good with a can of air duster and see if it helps. Which model of dv6 is it?

This is very true, hoover/spray can of air can help!

However, I also found that using Ubuntu with open source drivers runs causes the computer to run 25C hotter than it does in Windows, so it's not entirely a hardware problem. Using Kubuntu & fglrx my temperature is actually slightly lower now than it was in Windows :D.

Feathers

---

### Post by mastablasta on 2013-06-04
ah yes: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)
assuming you do not need newer kernel to "enable hardware" then the old one will do just fine.

so better install 12.04.1 then install AMD drivers and you are good to go.

---

### Post by Mark Phelps on 2013-06-04
> **mastablasta said:**
> that's really dumb. i am sure it's AMD's fault (=not). Ubutnu could recognise which card you have and use propper kernel. especially since this is LTS..
Apparently, then, Ubuntu IS dumber than you thought -- because, according to the OP, they ARE running Ubuntu 12.04.2 -- which DOES have the X-server version that is incompatible with the HD 2x/3x/4x series cards and their fglrx drivers.

What more, the other day, another frequent poster claimed that if you installed 12.04.1 (in order to get the fglrx drivers), then Ubuntu would be SMART and NOT attempt to upgrade to 12.04.2 -- and I saw a post claiming that is exactly what happened to a person who went back to 12.04.1.

Maybe we should not be giving Ubuntu so much credit.

---

### Post by Mark Phelps on 2013-06-04
> **Peptid said:**
> Mark, thank you for your replies. After reading your posts and searching through the web a bit more, I believe I come up with a possible solution...

It's not so much a solution as it is trading one problem you know about for others we don't.  There is no certainty that if you kludge up your system using schemes like this that you will not inherit more serious problems down the road.

---

### Post by Peptid on 2013-07-01
I have been struggling with and applying your suggestions. Here are the results I have obtained.

> First I made a clean install of 13.04, but that did not solve the problem. I found the solution that

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install fglrx-legacy

commands solve the problem. The computer is working for several hours,  and although the outside temperature is around 30 celcius, computer  temperature dwells around 55 celcius with 10% cpu usage, also the fans  are not screaming anymore. 		

Above commands work fine, but with the first update package that came from update manager, desktop environment has crashed; no icons could be seen and the desktop view was very 'noisy'. So, I followed

> 
a better solution is to install older version of LTS (12.04.1) and use the older kernel. if this is at all possible.

and installed 12.04.1, than installed fglrx drivers. It appears that temperature is decreased, yet with an intense usage of CPU, it is not that good controlling the temperature. Therefore, I finally followed

> I have a very similar laptop (a different HP Pavilion dv6) and had the  same problem as you, I couldn't get the graphics working in Ubuntu  without overheating.

Try using Kubuntu 12.04 with the fglrx driver, the two are compatible and took 25*C off my temperature :smile:.

and now the temperature is lower than even in windows and the temperature stability is much better than in Ubuntu 12.04.1

In short, I believe the overheating problem in Pavilion dv6 laptops can be solved either by installing ubuntu 12.04.1 with fglrx drivers, or switching to kubuntu 12.04 (or 13.04) with fglrx drivers.

Thank you all for nourishing advices.

By the way, here are the commands required to install fglrx drivers in kubuntu;

Code:
---------
sudo apt-get remove --purge fglrx*
sudo cp  /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
sudo apt-get install fglrx fglrx-amdcccle
sudo aticonfig --initial
---------
Then reboot the computer.

Then type in this line:


Code:
---------
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
---------

---

### Post by Feathers McGraw on 2013-07-02
Glad it worked!

Viva Kubuntu! :p

Feathers

---

