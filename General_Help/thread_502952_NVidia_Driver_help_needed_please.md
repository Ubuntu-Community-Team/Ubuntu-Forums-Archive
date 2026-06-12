---
title: "NVidia Driver help needed please"
date: 2007-07-17
forum: General Help
---

### Post by wildbluerhino on 2007-07-17
I'm trying to install Ubuntu on an AMD 64 system with a Gainward 7800 GS+ graphics card.

When I try to install the drivers for the graphics card, everything runs through fine, until it comes to the part where I have to restart the Xorg interface. When I do that, nothing happens, it just hangs on a black screen and the only option is to reboot the computer. And after that, it looks like it's loading Ubuntu, but just at the point where it's meant to be loading the interface, it goes to the black screen again.
The only thing for me to do then is to reinstall Ubuntu again from the bootable disk.

I've tried several different methods of installing the drivers but all have had the same effect time and again.

Ultimately, I want to get Beryl running on my computer too, but for now it would be nice of the graphics were behaving themselves.


Please, I'm fairly new to Ubuntu, so any help would be greatly appreciated.


PS. Sorry if this has already been covered in another post, but I couldn't find it so assumed it hasn't.

---

### Post by jespdj on 2007-07-17
When you get the black screen, try pressing Ctrl + Alt + F2. Does it switch to a text screen where you can log in? If it does, log in and try to reconfigure your X settings:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I hope that helps. If it doesn't, try booting Ubuntu with the "nosplash" kernel parameter. In the boot menu (GRUB) you can set kernel boot parameters somewhere, just have a look at the boot screen for instructions.

Do a search in the forums, there are more people complaining about black screens. Check this one for example: [http://ubuntuforums.org/showthread.php?t=121819](http://ubuntuforums.org/showthread.php?t=121819)

---

### Post by dragonwings on 2007-07-17
sudo aptitude install nvidia-glx-new                         <<for new drivers

sudo apt-get update

if you still got black screen like i did just restart taping your Esc button
then start recovery mode
let it do its thing 

then type               sudo dpkg-reconfigure xserver-xorg 

then type               sudo shutdown -r +0                          

now in ya desktop go to system then administration then restricted driver manager  
and activeate driver 

enable desktop effects if things arnt working for ya
after i enabled them i went  and un tick them because they  caused trouble

---

### Post by wildbluerhino on 2007-07-18
Thanks I'll give all that a try.

---

### Post by agibby5 on 2007-07-18
> **dragonwings said:**
> sudo aptitude install nvidia-glx-new                         <<for new drivers

sudo apt-get update

if you still got black screen like i did just restart taping your Esc button
then start recovery mode
let it do its thing 

then type               sudo dpkg-reconfigure xserver-xorg 

then type               sudo shutdown -r +0                          

now in ya desktop go to system then administration then restricted driver manager  
and activeate driver 

enable desktop effects if things arnt working for ya
after i enabled them i went  and un tick them because they  caused trouble

I'm having pretty much the same problem, see this post: [http://ubuntuforums.org/showthread.php?t=504085](http://ubuntuforums.org/showthread.php?t=504085)

Anyway, I did all the steps in your post and when I try to enable the driver in Restricted Driver Mgmt, and reboot, I get the black screen.  I then have to edit my xorg.conf file to use the vesa driver to boot into the OS... Hmm.

---

### Post by wildbluerhino on 2007-07-19
What's the difference between using the nvidia driver and the vesa driver?
From what I can tell, the vesa is just some sort of standard driver. Would using this after installing the nvidia one then enable me to use the more advanced graphics settings (and eventually beryl too)?

Also (as I haven't gotten round to trying it yet), what does the 'sudo dpkg-reconfigure xserver-xorg' do exactly?

---

### Post by wildbluerhino on 2007-07-20
Ok, I've tried doing all the extras you mentioned and now the result is that when it tries to load the xorg server, it pops up a message on a blue screen saying that 'Xorg wasn't started because it's not configured correctly', or something like that.

If I were to reinstall Ubuntu *again*, what would be the stages to go through to actually be able to fully install the drivers, ie; updates, etc, etc.

I have already tried the guides on both the Beryl Project homepage, and on [this]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html") page too, but I think they may be assuming that the average reader has done a few stages beforehand.


Please, please, *please* help me - I'm ready to just scrap it as a failed attempt and go back to bloody w1ndows :evil:

---

### Post by dragonwings on 2007-07-31
sudo dpkg-reconfigure xserver-xorg 

is used to change settings
navigate using arrows space and entre keys

the ones to change arethe nanes of card eg    nv   nvidia 
 and monitor setup go for simple option 

most other stuff should be ok as it is

i know its a pain in the butt  ,but thats  what linux is sorry i cant be more help ,but if you keep trying you should get it to work i had similar troubles to .

---

