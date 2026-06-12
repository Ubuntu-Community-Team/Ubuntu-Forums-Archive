---
title: "Can't Delete File, Software Can't Install, Can't See file in Terminal (ZynAddSubFX)"
date: 2019-12-29
forum: General Help
---

### Post by ic-racer on 2019-12-29
I re-installed Ubuntu Studio but my DAW compositions can't find a plugin called ZynAddSubFX.so in /usr/lib/vst 
I used that plugin before, but with the new Ubuntu Studio re-install (same version) the plugin is gone. All the other plugins are there.

(problem deleting file is at the bottom of this post, the text is all background as to how I got there)


So I have tried the following....

From the internet I found this post:


 "Just install the zynaddsubfx-git package and you're set :)"



## HOW TO DO THAT? -- two days trying nothing working

##Try

apt-cache search zynaddsubfx-git

## gives no output

## Try from firefox [https://kx.studio/Repositories:Plugins](https://kx.studio/Repositories:Plugins)

Link opens software installer but warns : No Software Repository included and gives 
no indication that there are plugins. 

Install button clicked anyway but error "unable to overwriet /usr/lib/lv2 zynaddsusbfx-lv2 3.0.5-2

So try to remove that

sudo thunar

from file manager /usr/lib/lv2/zynaddsubfx-3.0.5/ and right-click DELETE

re-try installer 

unable to overwrite /usr/lib/lv2/zynaddsubfx.lv2/zynaddsubfx.so

Back to sudo thunar

delete all these

/usr/lib/lv2/ZynAddSubFX.lv2
/usr/lib/lv2/ZynAddSubFX.lv2presets
/usr/lib/lv2/zynaddsubfx-3.0.5
/usr/lib/lv2/ZynAlienWah.lv2
/usr/lib/lv2/ZynChorus.lv2
/usr/lib/lv2/ZynDistortion.lv2
/usr/lib/lv2/ZynDynamicFilter.lv2
/usr/lib/lv2/ZynEcho.lv2
/usr/lib/lv2/ZynPhaser.lv2
/usr/lib/lv2/ZynReverb.lv2

try installer again still giving same error. Try to close installer
go back to firefox and re-download no luck
Try re-boot

This file opened with MATLAB when saved. Need to add ".txt" in 
by "Rename" the file from the finder. 

After re-start look for above files

sudo thunar

found only these and deleted

/home/daddy/.zynaddsubfx-bank-cache.xml
/home/daddy/.zynaddsubfxXML.cfg

back to firefox and KXStudio repository

download the AMD64.deb version

same error, unable to overwrite

try 

gksu nautilus ## did not work gksu not found

try

nautilus 

need to "Show Hidden FIles"

type /usr/lib/lv2

these files are here:

x-special/nautilus-clipboard
copy:

file:///usr/lib/vst/ZynAddSubFX.so
file:///usr/lib/vst/ZynAlienWah.so
file:///usr/lib/vst/ZynChorus.so
file:///usr/lib/vst/ZynDistortion.so
file:///usr/lib/vst/ZynDynamicFilter.so
file:///usr/lib/vst/ZynEcho.so
file:///usr/lib/vst/ZynPhaser.so
file:///usr/lib/vst/ZynReverb.so

can't remove them or open as administrator

Try
sudo add-apt-repository ppa:noobslab/apps ##gave lots of errors
sudo apt-get update #more of the same errors
sudo apt-get install open-as-administrator #unable to locate package

try

sudo apt-get install nautilus-admin  #worked

nautilus -q #does not seem to do anything but

nautilus # opens finder window with 'administrator' available

#go to /usr/lib/vst and it allows moving to trash

back to firefox
#still errors unable to install... /usr/lib/lv2/ZynAddSubFX.lv2/Zyn...

back to natilus #files not there

try "empty trash"

back to firefox still get same error

try reboot

back to firefox kx studio page...

now "software installer" gives an error "unable to download updates failed to refresh cach
E: the repository Http/ppa.launchapd.net/noobslab/apps/ubunto ean releas does not have a release
file"

press "install" anyway

Still errors ZynaddSsubFX.so file cant be overwritten

back to nautilus -q
nautilus
go to file and open /lv2 as administrator and files are not there

to go terminal and files are there. Try to delete from terminal
daddy@daddy-Macmini:~$ locate ZynAdd
/usr/lib/lv2/ZynAddSubFX.lv2
/usr/lib/lv2/ZynAddSubFX.lv2presets
/usr/lib/vst/ZynAddSubFX.so
/usr/lib/x86_64-linux-gnu/lmms/RemoteZynAddSubFx
/usr/lib/x86_64-linux-gnu/lmms/libZynAddSubFxCore.so
/usr/share/lmms/presets/ZynAddSubFX

daddy@daddy-Macmini:~$ cd /usr/lib/lv2

ls # doesn't show it

ls -a  
 
does not show it

daddy@daddy-Macmini:/usr/lib/lv2$ ls -la

drwxr-xr-x   2 root root  4096 Oct 17 08:30 vynil-swh.lv2
drwxr-xr-x   2 root root  4096 Oct 17 08:30 wave_terrain-swh.lv2
drwxr-xr-x   2 root root  4096 Oct 17 08:30 xfade.lv2
drwxr-xr-x   2 root root  4096 Oct 17 08:30 xfade-swh.lv2
drwxr-xr-x   2 root root  4096 Oct 17 08:30 yoshimi.lv2
drwxr-xr-x   2 root root  4096 Oct 17 08:30 zm1-swh.lv2

daddy@daddy-Macmini:/usr/lib/lv2$ locate ZynAddSubFX
/usr/lib/lv2/ZynAddSubFX.lv2
/usr/lib/lv2/ZynAddSubFX.lv2presets
/usr/lib/vst/ZynAddSubFX.so
/usr/share/lmms/presets/ZynAddSubFX

[B]So, at this point "ls -a" won't show the file but "locate" shows them. 

I'm stumped , can't move on from here, can't delete the files. 
[/B]
daddy@daddy-Macmini:/usr/lib/lv2$ rm /usr/lib/lv2/ZynAddSubFX.lv2

rm: cannot remove '/usr/lib/lv2/ZynAddSubFX.lv2': No such file or directory

Running DAW Qtractor I get which puts me back to where I was two days ago :
"/usr/lib/vst/ZynAddSubFX.so(0): VST plugin not found."

---

### Post by ic-racer on 2019-12-29
More research shows the "locate" command can be wrong:


[LIST=1]
[*]> locate can name files that no longer exist. 
  GNU locate and mlocate have the -e  flag to make it check for file existence before printing out the name  of each file it discovered in the past, but this eats away some of the locate speed advantage, and isn't available in BSD locate besides.


So I tried "locate -e" and can't find the files. 


OK but now to try the installer again from KXStudio and see what happens... 
[/LIST]

---

### Post by ic-racer on 2019-12-29
No go.  Back to square one
> 
"Unable to install "ZynAddSubFX-Alsa": Error whie installing package: trying to overwrite /usr/lib/lv2/ZynAddSubFX.lv2/ZynAddSubFX.so", which is also in package zynaddsubfx-lv2 3.0.5-2"

---

