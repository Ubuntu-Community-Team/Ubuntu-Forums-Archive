---
title: "Unity not working, SMB/CIFS Files fails"
date: 2014-11-28
forum: General Help
---

### Post by Onna_Nelson on 2014-11-28
I'm fairly new to Ubuntu and Linux. I built a computer a few months ago and today I decided to install a GPU (GeForce 750) and try to run some Steam games via Wine. I installed NVIDIA drivers, got the GPU working, switched my HDMI cord from the mobo to the GPU, rebooted the machine, everything seemed fine. I was able to download and install steam.exe through Wine. After I tried running Steam, I realized that the text wasn't displaying properly. I installed the text packages, and tried again. Steam wouldn't launch. After searching some forums, I tried finding ClientRegistry.blob to delete, but I couldn't find it. Eventually, I decided maybe rebooting would be my best bet since "have you tried turning off and back on again?" is the basic step 1 of most troubleshooting.

Upon this reboot, the dock wouldn't display, the desktop icons wouldn't display, and CTRL+ALT+T wouldn't bring up the terminal. All that would display is my desktop background. It seemed exactly like[ this problem.]("http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears") I tried following the troubleshooting steps there. Now, it's important to note that for GUI stuff, like my desktop, I had to have my HDMI cord plugged into my GPU but when doing the gnome/terminal/command line stuff, I had to have my HDMI cord plugged into my mobo for it to display. Eventually I was able to check the "enable unity" box, etc. and sudo reboot back in gnome. 

Upon that reboot, it seemed even worse. Nothing is displaying, just a black screen. I reboot again and hold shift to go into recovery mode. It says everything is [OK] except for one [fail]:

```
* Starting SMB/CIFS File and Active Directory Server        [fail]
```

I'm really at a loss of what I should do at this point. I really just want my computer working with all my desktop icons and other GUIs.

------------------------------ update ------------------------------
At this point, nothing, not matter what mode I choose or what I'm doing, will display through my GPU's HDMI port. Whenever I try something and then reboot, it takes me to the screen where it says:

* Starting SMB/CIFS File and Active Directory Server        [fail]

Then after a minute it pops up with a warning that I'm in low-graphics mode. It asks me what I'd like to do now. I can choose:

* Run in low-graphics mode for just one session
* Reconfigure graphics
* Troubleshoot the error
* Exit to console login

I'm not sure which I should pick. The first option tells me to "stand by one minute while the display restarts." I'm not sure if it's really slow or if it's just not working at all, because I'll wait a few minutes, press okay, and it just hangs with a black screen and a blinking _ until I CTRL+ALT+F1. 

When I select reconfigure graphics it asks me to restore defaults and then asks me restart, which just takes me back into this whole loop again. 

Selecting "trouble shoot the error" allows me to review the xserver log file, review the startup errors, or edit configuration file. I'm not sure if doing any of those things would be helpful. Startup errors has nothing in it. Xserver log file has some errors related to NVIDIA. Edit configuration file doesn't do anything, it just takes me back to this menu. 

Selecting "exit to console login" takes me to the same blank screen with the flashing _ on it.

------------------------------ update 2 ------------------------------

Since the errors in the xserver log file were related to NVIDIA and since any time I booted it took me to the "low graphics mode" screen, I decided to follow the instructions on [this forum]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error") for reinstalling NVIDIA drivers. It seemed to work, so I tried to reboot. Now, any time I boot, I get a message that a system error has been detected. Regardless of if I choose to "cancel" or "report this error", I am taken to a black screen. Nothing comes out of my GPU HDMI port. And only a black screen (no blinking _ or anything) appears from the mobo's HDMI port. CTRL+ALT+F1/F2/F3/F7/F8 do not do anything. I don't even have command line anymore. Literally everything I have tried has made the problem worse.

------------------------------- update 3 ------------------------------

I removed the GPU entirely and now my monitor actually receives a signal, and I have my desktop background back. Unity still is not working, and now I don't have a GPU. :(

------------------------------ update 4 -------------------------------

Unity is back. There are a LOT of unity fixes out there, but this is what finally worked for me:

ctrl + alt + F1
sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity

--------------------- update 5 --------------------

It seems physically removing the GPU and reinstalling it fixed all other problems.

---

