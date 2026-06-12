---
title: "Dual-Screen ATi on Gutsy Troubles"
date: 2008-06-04
forum: General Help
---

### Post by TTrussell on 2008-06-04
Hello All,

I had to leave the world of Ubuntu 8.04 because it was so unstable. I decided to go back to 7.10, a very robust version in my opinion (although it lacks networking support, but that can be fixed). Now something ELSE is troubling me. I use 2 17" LCD monitors for my desktop. I have them set horizontally.

In my brief experiments with 8.04, I downloaded EnvyNG which installed the ATi driver for my graphics card, along with Catalyst Control Center (CCC) which I was, unfortunately, familiar with from Windows.

CCC took about 10 minutes to actually start, turning my monitors on and off as it tried to tell it's head from it's feet. Finally, I was able to enable my second monitor, and then set the resolution to the "Big Desktop" setting. Luckily, the program figured out my usual resolution was 1280x1024 and was smart enough to make it 2560 x 1024.

UNFORTUNATELY, I had to leave the world of 8.04. For the most part, everything is the same in 7.10, with the exception of having to use Envy instead of EnvyNG, and with the exception of this whole dual-monitor business actually working.

Now I have the same CCC, and it gives me the same options, but when I select this "Big Desktop" it gives me some crackpot resolution: 3840 x 1080.

What really happens is my left monitor is not at the appropriate resolution, while my right one is. Quite a headache. They did, however, manage to get the positioning of the monitors right, and I was able to get them to have the mouse go from one to the other quite flawlessly.

Now my question is, how can I get them to the appropriate resolution?

---

### Post by TTrussell on 2008-06-04
I also tried this.

Open Envy, uninstall the ATi graphics driver that it installed, close Envy, uninstall Envy.

Open Firefox, go to [www.ati.com](www.ati.com), click "Support" click "Get Graphics Drivers" select Linux x86, select ATi Radeon x1600 Pro blah blah. Basically get the driver from [www.ati.com](www.ati.com)

Download the .run file. Drag it to the desktop. Open a terminal. Type "cd Desktop" to get to the Desktop. Type "sudo atixxxxxxxx.run" enter your password and then it has a nice GUI for you to install with.

Finish installing that, and reboot. Under applications, you should notice that the Catalyst Control Center is now available. It may or may not work. If not, try enabling the Driver in the Restricted Driver Settings.

This caused mine to run in Low Graphics Mode. No clue as to why, it just did. I then clicked "Configure" and it gave me a bunch of options about my graphics card and my monitors. I set up my monitors accordingly. For graphics card I selected by brand. ATI and fglxr or whatever, I only knew that from experience. 

On restart my computer loaded the Ubuntu logo and loading bar, and then it booted in Low Graphics Mode AGAIN. EVEN THOUGH it was able to make that beautiful UBUNTU logo, it has to be started in LOW EFFING GRAPHICS MODE.

Of course now I am quite peeved but realized it may have been because of my messed up reboot. I am quite relieved to notice the "TEST" button at the bottom of the GUI, allowing me to test my options without restarting. I reset all of my options, noting to select the Proprietary Driver as opposed to the OpenSource Vesa, and click Test. Screens go black for about 10 minutes and finally I give up and hit CTRL ALT BACKSPACE to relog the computer. Comes up with the little boot guys for a while, I hit ALT F7 to get to the GUI, blank screen with blinking guy at the top, as usual, only this time it's way longer. Hitting any buttons proved fruitless, so I decided to give the thing a hard-restart.

Upon restart, the computer did the same thing. At this point I give up. Insert disc and use recovery to hopefully grab my graphics back.

WHAT DID I DO WRONG

---

### Post by TTrussell on 2008-06-04
So I rebooted and am now working in Low-Graphics Mode. I opened up my Restricted Drivers and turned off the ATi Driver. Opened up my Apps and uninstalled the ATi Driver that I had installed. Reinstalled Envy and am installing using different options. Select "Custom" and then select the second version, "8.40.4"

Let it do its thing, agree to all of the package-maintainers files overriding your own, and then tell it to automatically configure your xorg.conf file.

Quit applications and reboot. Ubuntu boots into the loading menu, and proceeds as it should, in full-graphics mode.

Upon entering, I open my Application menu to find that it has given me a new CCC icon, which gives me an error that my driver isn't working.

I open my Restricted drivers to play with THIS driver. It tells me it can't reconfigure xorg.conf because it's MISSING! I open up my folder to discover there is now a '1' appended to the back of my xorg.conf file. Open terminal > cd /etc/X11 && sudo gedit xorg.conf.1. I Save As to xorg.conf with no stupid '1.'

Attempt to open CCC, same error. Attempt to enable driver, same error. Reboot PC to see if the xorg.conf will get reloaded in the reboot. PC boots into Low-Graphics Mode. Back to the Drawing Board.

---

### Post by TTrussell on 2008-06-04
Moved through low-graphics mode again and was able to successfully enable the Driver in the Restricted Driver Settings. Reboot and got back into low-graphics mode.

Trying the THIRD of the options for the graphics settings, the oldest driver.

Repeat the steps above for Envy except select the third and final driver 8.28.8. Allow it to do xorg reconfiguration and reboot. 

Jump through the same hoops, end up in the same place. Reinstalled the normal driver, everything works fine, boots fine, but still no Big Desktop at the appropriate resolution. Disappointing.

If anybody has a fix, please post.

---

