---
title: "sound setup dropping everytime after bootup"
date: 2006-12-10
forum: General Help
---

### Post by broekskw on 2006-12-10
hello everyone.finally got my sound card going some what on ubuntu 6.10.i have to use this guide [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
and go to this section and follow the direction

update I now recommend using the stable version 1.0.12

The alsa-project route is very similar to the alsa-source route without the module-assistant. First you would have to get the alsa-driver tar from alsa-project then pretty much do configure, make and make install again. However, I do recommend that you make a specific directory when you compile something from source. Remember the name of your soundcard driver and use it place of the blue text below.

mkdir src
cd src 
mkdir alsa 
cd alsa 
sudo apt-get install build-essential linux-headers-$(uname -r)
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12.tar.bz2)
tar -xvjf alsa-driver-1.0.12.tar.bz2
cd alsa-driver-1.0.12
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes
sudo make
sudo make install

after this i can type this command into terminal and see my sound card  aplay -l then i go into alsamixer and unmute everything and exit then i type this in terminal to save my setting from alsamixer  sudo alsactl store 0  then i go into my sudo nano /etc/modules and under the last line type in  snd-sbawe and then save file but everytime i reboot i loose everything no more sound card,have to do all again just to get it going again. how do i get everything to save 

thanks:mrgreen: :mrgreen:

---

### Post by broekskw on 2006-12-10
ok did another reboot and lost everything](*,) ](*,) 
in terminal after you run and make changes and then exit out of terminal does everything save or is there a command to save in terminal before you exit?
:mrgreen:

---

### Post by broekskw on 2006-12-10
ok so nobody has a solution for this helppppppppppppppp:cool:

---

### Post by broekskw on 2006-12-10
everyone must be sleeping or [-(

---

### Post by broekskw on 2006-12-10
sorry for begging but all other post comes up zero replies.
[http://ubuntuforums.org/showthread.php?t=316180](http://ubuntuforums.org/showthread.php?t=316180)
have ubuntu installed one computer and everything working except sound.had to install manually and after install it works ok untill i reboot and then everything is gone.followed the sound guide but still will not keep setting after reboot;
w h a t  if any am i doing wrong](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by taurus on 2006-12-10
What do you have to do to set your sound working?

---

### Post by loell on 2006-12-10
try
```
alsactl store hw:0,0
```

---

### Post by broekskw on 2006-12-10
i have to build the driver from the following guide
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
under " Using drivers from alsa-project" if i follow directing can get sound going(right now i am listening to prism with my headphones)but after reboot i have to reinstall from the giude](*,) ](*,)

---

### Post by broekskw on 2006-12-10
thanks for your reply but get this error
alsactl: save_state:1177: Cannot find soundcard 'hw:0,0'...
broeks@broeks-desktop:~

---

### Post by taurus on 2006-12-10
I hate to do this again but your other thread is still active so I am going to merge this one into that then...

---

### Post by broekskw on 2006-12-10
here is a screen shot after command "aplay -l"

so it is there i think??](*,)

---

### Post by broekskw on 2006-12-10
thanks sorry for all the post but i am at my wits end with this

---

### Post by broekskw on 2006-12-10
ok so according to the guide if i type this into a terminal aplay -l i should see my sound card(i have a sound blaster awe64 driver is sbawe)but i get this on the screen
*** List of PLAYBACK Hardware Devices ****
card 0: S16 [Sound Blaster 16], device 0: SB16 DSP [DSP v4.16]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
so is it installed or not???
if it is i am to do this command to find the sound driver " lspci -v

but as you can see not sound device found(but sound is going)
????:mrgreen: so what next

---

### Post by broekskw on 2006-12-10
ok mods can close this one,got every thing going including sound.reboot and working aok.
i had a dvd player that i installed and also a live dvd disc of ubuntu that i ran (6 time install) and then did the sound guide and it works, so could have been the cdrom drive or the cd live disc.also in the command "sudo nano /etc/modules" could never get the added command to save "snd-sbawe but for :mrgreen: :mrgreen: :mrgreen: some strange reason this time it saved,

---

