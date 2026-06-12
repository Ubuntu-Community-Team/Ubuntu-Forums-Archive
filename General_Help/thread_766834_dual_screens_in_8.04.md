---
title: "dual screens in 8.04?"
date: 2008-04-25
forum: General Help
---

### Post by darkthunderfx on 2008-04-25
I just tried to hookup my monitor to my laptop and i'm getting absolutely no signal. i expected that it would display the same as my laptop display, but it appears not the case. what can i do to make it show something at all? its a hp laptop dv2120us with a nvidia card.

---

### Post by CorruptNoob on 2008-04-25
Hi, I'm not experianced with Ubuntu, but I can offer what help I can.

For me, I needed nvidia-settings, I think it's sudo apt-get install nvidia-settings, but like I said, I'm new, so that command could be wrong

Once installer, type nvidia-settings into the terminal, and you'll have a GUI that let's you do all the video related stuff, click on the configuration section and click "Detect Displays" and it should detect it and allow you to use it.

I think you might need to use sudo nvidia-settings to save some stuff, but again, don't take my word for it!

---

### Post by darkthunderfx on 2008-04-25
I see that the nvidia-settins appears to be what I need to get the job done. For some reason, however, it is not working.

Using twinview I can get both screen working, but with the different resolutions and size I miss a lot on the smaller screen.

When trying to enable a second "X" screen I am not able to allow both screens to work at the same time. I can get the second screen to work by itself, and the first screen by itself, but not together. When trying to save the settings to file, I get "ERROR: Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

Help?

---

### Post by Nax10 on 2008-04-25
I have a very similar problem.

Desktop computer with a Nvidia FX 5200 and two LCD displays (different brands but very similar in size, resolution, etc).

After enabling the restricted NVidia driver and installing the NVidia settings program I can set the two monitors in twin view but not separately.

When I set each monitor as a separate X screen and try to save the configuration file I get the same error - unable to create backup.

After quitting the NVidia settings program I end up where I started: one screen is working OK but the other is off and shown as disabled in the NVidia settings.

I tried doing the backup manually using a copy command I found on another thread but I get a "permission denied" error.

Is that backup a system file that needs special permissions to be created?

As you can tell, I'm new to Ubuntu, so any help is appreciated. Trying to configure simple hardware settings has been the most frustrating experience I've ever had to deal with.

---

### Post by Nax10 on 2008-04-26
Well, one problem down, the rest of the problem unsolved.

The "cannot create backup" error from the NVidia X Server Settings program seems to be caused by the program not having admin privileges (?).

Start the NVidia Settings from Terminal with this command:
```
gksudo nvidia-settings
```

and you'll be able to save the settings without the error.

For my situation, I enabled both monitors, restarted the system, I saw two NVidia logos on both monitors but still, the second monitor is off.

Starting NVidia X Server Settings now shows both monitors enabled and active with the correct resolutions but the second monitor is not working.

If I go to System > Prefs > Screen resolution the Cloned Screen options is checked and the window shows only one square representing one active screen - I suppose. If I uncheck Cloned Screen then the message on that window says Unknown. I have no idea what all this means.

That's it for me and Ubuntu. If it's so hard to configure a dual monitor setup after so many hours of going through forums, reading FAQs, IRC chats, more and more and more pages of technical info that's not relevant only to get to one command that may or may not work with my system, then better give up hope for ever getting away from that POS called Windows.

---

### Post by encompass on 2008-04-26
Quite honestly, if you REALLY want help with this issue, you could talk to NVidia.  Ubuntu has made it dead simply easy to setup your monitors for what ever purpose you have.  Sadly, until NVidia starts making good drivers, IE open shource ones.  We can't use the features of ubuntu that would make the post never appear again.
Good luck.

---

### Post by cafe-ristretto on 2008-04-27
> **encompass said:**
> Quite honestly, if you REALLY want help with this issue, you could talk to NVidia. 

I have a Dell D830 with nVidia Corporation Quadro NVS 135M.  If I understand you right, I have to use nvidia-settings, because the the nVidia prop drivers can't be made to work with the Screen Resolution preferences screen.

Is there a list of Ubuntu supported video cards, meaning they don't just work, but can't be configured within the Ubuntu prefs?

---

### Post by encompass on 2008-04-27
good question...
The thing with nvidia drivers is that they are not open source.  Because of that, they can't be supported by ubuntu.
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
I personally love the intel chipsets... they work very well in Linux and have 3d desktop effects and are fast enough for most Linux programs and games.  there is an "nvidia-settings" program.  You can search around for the instructions on how to use it.  But like I say, you paid money for that hardware and a proprietary driver... I would talk to nvidia... they are entitled to help you.
You may even be able to do dual monitor with the open source nvidia drivers.  But that I am totally unsure of.

---

### Post by CorruptNoob on 2008-04-27
The 'cannot create backup' crap is because you need to run nvidia-installer as sudo,  sudo nvidia-installer

then it'll give you permission to write files

---

