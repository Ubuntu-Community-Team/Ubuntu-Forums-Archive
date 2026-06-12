---
title: "Unable to install AMD-GPU-PRO drivers"
date: 2018-10-30
forum: General Help
---

### Post by gottaslay on 2018-10-30
[COLOR=#242729][FONT=Arial]I'm running on Ubuntu 18.10 and just got a new graphics card, RX580. I downloaded the latest package from AMD's site and tried to do [/FONT][/COLOR]./amdgpu-pro-install[COLOR=#242729][FONT=Arial]. Which returns me an error saying: [/FONT][/COLOR]The following packages have unmet dependencies: amdgpu : Depends: amdgpu-core (= 18.40-676022) but 18.20-606296 is to be installed amdgpu-pro : Depends: amdgpu-pro-core (= 18.40-676022) but 18.20-606296 is to be installedE: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).roope@roope-Z97P-D3:/mnt/4989a2cf-a299

---

### Post by lordboltar on 2018-10-30
should be - sudo bash ./amdgpu-install

looking on the inside of package all the missing dependencies you list are there so try running it as listed and open the terminal inside the extracted folder before you run it

---

### Post by LwIh%*7 on 2018-10-30
> **gottaslay said:**
> [COLOR=#242729][FONT=Arial]I'm running on Ubuntu 18.10 and just got a new graphics card, RX580. I downloaded the latest package from AMD's site and tried to do [/FONT][/COLOR]./amdgpu-pro-install[COLOR=#242729][FONT=Arial]. Which returns me an error saying: [/FONT][/COLOR]The following packages have unmet dependencies: amdgpu : Depends: amdgpu-core (= 18.40-676022) but 18.20-606296 is to be installed amdgpu-pro : Depends: amdgpu-pro-core (= 18.40-676022) but 18.20-606296 is to be installedE: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).roope@roope-Z97P-D3:/mnt/4989a2cf-a299

According to this [https://www.amd.com/en/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-580](https://www.amd.com/en/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-580) only 18.04.1 LTS is supported NOT 18.10 you may have to wait till 20.04 to get it or use the open source AMDGPU driver as a workaround.

---

### Post by dennis-restle on 2018-12-20
Edit:
OHHH, 
This "Fix" Crashed my Computer somehow. The GDM was not able to start anymore, Xorg had a segfault at address 0....


AMD, your PRO-Linux software is giving me headache and wasting my time....

> 

I had a similar Issue. Finally i had to reinstall my system new after i messed up my ubuntu 18.04 after installing AMDGPU-pro 18.10 and 18.30 and then 18.50.

The Installer from AMD is not good. They have to improve on this piece of Software.

On my freshly new installed Ubuntu 18.10 i used the AMDGPU pro from their website.
It complained, that amdgpu core could not be installed because of whatever.
i tried 
[QUOTE]sudo ./amdgpu-pro-install
the result was
Fehler traten auf beim Bearbeiten von:
 /tmp/apt-dpkg-install-Lz3JXC/044-amdgpu-core_18.50-708488_all.deb

then i did

> apt --fix-broken install 

it had a error, too.
Then i did

> dpkg-deb -R /var/opt/amdgpu-pro-local/amdgpu-core_18.50-708488_all.deb edit

the I edited the file DEBIAN/preinst and set the following:

if [ "$VERSION_ID" != "18.10" ] ; then

> dpkg-deb -b edit /var/opt/amdgpu-pro-local/amdgpu-core_18.50-708488_all.deb

a simple apt --fix-broken would complain about wrong hashes, so i installed it manually

> sudo dpkg --install /var/opt/amdgpu-pro-local/amdgpu-core_18.50-708488_all.deb

and then again i used

> apt --fix-broken install [/QUOTE]

---

