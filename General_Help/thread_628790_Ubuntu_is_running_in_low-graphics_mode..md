---
title: "Ubuntu is running in low-graphics mode."
date: 2007-12-01
forum: General Help
---

### Post by tetrafuran on 2007-12-01
Ubuntu is in low-graphics mode. It's asking me for a driver.
I just can't figure out which driver it wants in order to get over that eternal driver asking loop. I'm using geforce 440 MX so It should work with drivers called, nvidia, nvidia 4 series, nvidia generic or what ever.
Unfortunately I'm running out of ideas. I can always use the terminal if in the driver query I answer "shutdown" I just don't know what would I do with it.

Here's some boring history and the long version of what "exactly" happened, how I got into this mess and what I've tried so far.

I disconnected my hard drive, took it with me, visited a firend of mine with it and returned home in the after noon. As I plugged it in I experienced lots of unexpected stuff for no apparent reason. 

1) I got no signal to the screen. I removed the HD and for no apparent reason this fixed the problem. I was able to see bios and everything normally.

2) I booted from HD and I got some errors I can't remember any more. I thought that perhaps linux is like windows in this sense, that I'll just reboot and problems get fixed for no apparent reason. IT WORKED!! Cool.

3) Booting went a lot further this time. When starting X it says that ubuntu is running in low-graphics mode. It asked for a driver for the 3d card. I gave it and it just kept asking the same thing over and over again. I shut it down and restarted. I can't quite remember what I did, but I managed to start X in a very strange mode. Mouse was disabled and I could see a close up of the middle of the screen. I can't do that any more though.

"your screen and graphics card could not be detected correctly" What's this supposed to mean? When I installed ubuntu, it detected everything without complaining like this. When I installed the nvidia drivers I wasn't bothered with this nonsense. In the morning before detaching the HD it worked like always. What has changed now all of a sudden? 

I beginning to thing there's an evil spirit in the HD and it got angry bacause I let it stay a long time in my bag. It was cold outside and I had to wait for a train for quite a while. :)

---

### Post by Craigus on 2007-12-01
I suspect a loose cable connection somewhere - it was working, you unplugged stuff, and now it's flaky. Go over the machine and make sure that everything (inlcuding RAM and cards) is plugged in firmly.

---

### Post by tetrafuran on 2007-12-02
Thanks. I checked the cables before posting yesterday, but today I rechecked them. Nothing new.

In fact it's beginning to look like it lost all of it's drivers. They exist somewhere, but this little gibbon just doesn't remember how to use them. By default it's using a driver called vesa generic vesa compliant cards. With it I can shutdown (i.e. enter terminal) and then startx. This way I can enter the zoomed desktop. with ctrl+shift+numpad I was able to use a numpad "mouse". Then I lowered the resolution to 640*480 so that I could see all of the desktop without the silly zoom close up. I also noticed that I can't enter the net either. Sounds like all the drivers are somehow lost.

I'm beginning to consider just simply re-installing gutsy. I just need to figure out how to not loose all my data in the process.

---

### Post by PmDematagoda on 2007-12-02
Try doing:-
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tetrafuran on 2007-12-02
Thanks. That worked for the screen and network. Sadly though the mouse still doesn't work. Any ideas? In the setup you gave, I have tried a couple of choices now.

---

### Post by PmDematagoda on 2007-12-02
What kind of mouse do you have?

---

### Post by tetrafuran on 2007-12-02
logitech weel mouse with an extra button for thumb. It's also optical wireless. It uses USB. In the setup I have the following choises:
/dev/input/mice
/dev/psaux
/dev/ttyS0
/dev/tts0
/dev/gpmdata
Most of these make no sense and the guiding text that preceeded, didn't help at all. The only one that made sense was /dev/input/mice. After that I have the decision between:
ImPS/2
ExplorerPS/2

BTW I've noticed that certain keyboard commands can shut down X. This is particularly annoying since most of them are in the numpad and that's what I have to use at the moment. 

And another annoying "feature" is in my microsoft wireless desktop keyboard. The buttons in it have a tendency to repeat a signal every now and then. The repeating continues untill I press that button again. Since I'm now useing a numpad mouse this means that quite frequently the mouse spins out of control and keeps on charging to the direction where I was going. It's a feature of this keyboard that existed even under windows. That's another reason for not playing computer games any more.

---

### Post by tetrafuran on 2007-12-02
I managed to get the mouse working with a usb - ps/2 adapter. Lots of strange things have happened today. Complicated stuff like computers and weather are very strange and unpredictable. I suppose that's why a certain level of mysticism has developed around both of them. Apparently this is a quick and dirty method of getting on. At the moment the automatic configuration gave some sort of custom settings that work. They aren't the correct settings since I can't change the resolutions, which just happens to be something other than the standard 3:4 ratio. In any case it works and it should be good enough for a while. 

Attempting to get the correct screen and display adapter, will always result in the problem I just "solved".

---

