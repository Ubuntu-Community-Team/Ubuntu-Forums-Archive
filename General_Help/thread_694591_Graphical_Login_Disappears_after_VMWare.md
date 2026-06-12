---
title: "Graphical Login Disappears after VMWare"
date: 2008-02-12
forum: General Help
---

### Post by o_swas on 2008-02-12
Hello,

I set up my desktop computer to dual boot XP Pro/Kubuntu 7.10.  Everything was working great; I could either boot into XP or Kubuntu.

I need to run Linux when I'm running XP, so in XP I installed VMWare Workstation 5.5.2.  In VMWare, I created a new virtual machine, but during the setup of the virtual machine, instead of giving space in XP to install Kubuntu, I pointed the virtual machine to the Kubuntu partitions (the boot partition and the swap partition).  It seemed to work fine -- when I started the virtual machine, it was just like the computer was booting, and it started booting into Kubuntu.  So far so good.

Then the problem started.  Normally when booting Kubuntu, there's a splash screen that says "Kubuntu" with a blue progress bar as the OS loads, and when that completes a GUI with the user login appears.  However, when I started Kubuntu in the virtual machine, it booted, but it booted to "command line" environment, with a whole bunch of text flying by on the screen.  It finally settled on a login command prompt.  I entered my user name and password, which worked, but I was still at the command line.  I then entered the command **startx** and the KDE desktop started and appeared.  I also noticed that when I went to shut down (K --> Log off) the only button was to Log Off, where normally there are more buttons that include Shutdown, Restart, Log Off, etc.  

I quit the virtual machine and shut down the computer, then restarted and chose to boot into Kubuntu.  Unfortunately exhibited the same behavior as it did in the VM, so I don't know what happened.  

Now, I had just installed Kubuntu and had some issues with my driver [found in this thread]("http://ubuntuforums.org/showthread.php?t=690925").  Maybe there were problems with the video card and driver again?  I've heard various reports of resolutions getting "fixed" only to have problems again on the next reboot (I had finally resolved the resolution problem then hadn't booted into Kubuntu until I started the virtual machine).


So, my questions are:

1.  How do I get Kubuntu to boot and give the login GUI again, and I'm assuming to start KDE automatically?

2.  How do I get the Restart, Log Off, Shutdown etc. buttons to all appear when I try to shutdown Kubuntu?

3.  Was this problem caused by starting the OS in a VMWare virtual machine?  If so, how do I avoid it?

4.  If it is a video card/driver issue, how to I get it to "stay working" once it's been working?
Thank you!!!!

-Ryan

---

