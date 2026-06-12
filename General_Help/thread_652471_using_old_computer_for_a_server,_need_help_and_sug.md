---
title: "using old computer for a server, need help and suggestions"
date: 2007-12-28
forum: General Help
---

### Post by thebloggu on 2007-12-28
i am a noob in linux but i want to use a computer here that is an old laptop [LifeBook C325]("http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/lifebook/index.html").

>     *   Intel Pentium MMX 266MHz
    * 12.1in TFT LCD screen
    * ESS ES1879Technologies Sound Blaster pro compatible,
          o 16-bit stereo codec
          o Full duplex support
          o 3D sound
          o Hardware volume control
    * Trident Cyber 9388
          o 2MB VRAM
          o 32-bit PCI bus VGA controller with Graphic Accelerator
          o LCD/CRT simultaneous display capability
          o 1024x768 resolution for CRT
    * 32MB SDRAM DIMM Max 160MB (1 Dimm Expansion Slot)
    * Texas Instrument PCI 1225 PC Card Controller
          o Two Type II PCMCIA or One Type III slot (Zoom Video Support)
    * 2400mAh Li-Ion Battery
          o 2-2.5Hrs, Max APM enabled
          o 3Hrs Charge Time when Off
          o 8Hrs Charge Time when On
    * Li-Ion Bridge Battery
    * 2.8A/16V Mains Adapter


i tried to ran freenas but i only have a linksys wireless PCMCIA card (wpc54g-v2) that i cant get to work. tried to run ubuntu, xubuntu and fluxbuntu but they are still heavy. tried to use ubuntu lite but can't connect to the internet. tried dsl but seems too difficult.

my idea is to or use it like a server for files or a dedicated jukebox or something (i have an external drive). i want to use it. but didnt get it yet. what should i do? what do you think? more ideas? what linux distro to run? please help

remember i am beggining so i need clear instructions

thanks

---

### Post by empthollow on 2007-12-28
unfortunatly your link does not work so i can't take a look at the laptop.  i have tried many distros and ubuntu has by far been the easiest to configure both hardware and software.  If you are looking for a lightweight desktop xfce (xubuntu) for fluxbox (fluxbuntu) are the lightest.  i like fluxbox personally but it does leave most of the configuring to you.  if you are not opposed to leaving the graphical desktop out of it you could download a copy of ubuntu server.  it is completely stripped down base system and boots in a flash.  It still allows the easy configuration with apt-get and the great hardware and software support that ubuntu offers.   it doesn't take alot to get a nfs or samba server going in a command line environment, there are just a couple of text files you need to edit and commands to run.  if you want a graphical desktop you can always install one from the repositories.

---

### Post by thebloggu on 2007-12-28
sorry, i already shown specifications. i tried ubuntu server. first it was looping while booting. then i solved the problem but i still dont know how to work in command line. thanks

---

### Post by empthollow on 2007-12-28
i am pretty familiar with the command line if you have some questions i can probably answer them.  Check out this web site if you are new though, it help me ALOT when i first started [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by thebloggu on 2007-12-28
thanks again. i might use that but i would like something simple. just turn the laptop on and its working (after installation) and something easy to configure.

---

### Post by louieb on 2007-12-28
32 MB ram is going to be a challenge. Probably to little for any of the Ubuntu flavors. If you must have a GUI,  Puppy and  DSL are the only two distros I can think of that might run in 32MB ram and I'm not sure about Puppy.

---

### Post by dagnabit dang doohickey on 2007-12-28
If the computer has only 32MB RAM and you have no interest in the command line, this project is probably not such a good idea.

---

### Post by thebloggu on 2007-12-28
its not that i am not interested. i dont mind if i can make it. but i dont know command line. i may learn, but its difficult to make a server like that. thanks

btw tried dsl but dont know what to do to use wireless

---

### Post by CREEPING DEATH on 2007-12-28
The new Generic-Kernel Ubuntu is going to be too heavy, you're going to have to learn Debian or another CLI Linux.

CD

---

