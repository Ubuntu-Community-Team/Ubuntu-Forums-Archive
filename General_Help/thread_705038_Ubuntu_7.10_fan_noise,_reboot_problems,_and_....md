---
title: "Ubuntu 7.10 fan noise, reboot problems, and ..."
date: 2008-02-22
forum: General Help
---

### Post by Sarvatra on 2008-02-22
I just installed gutsy gibbon on my computer.  It is a emachines T5088. I have a PNY GeForce 8600GT video card in it. I am dual booting with Windows xp. 

Although, i consider myself to be good with computers, I have no experience at all with Linux/Ubuntu. I am experiencing three main problems:

1. The Fan noise. I have looked for a solution. I found out that the 169.09 nvidia driver is a fix for it. I have downloaded the driver. But I cannot install it. At the terminal when i input "sudo sh Desktop/NVIDIA-Linux-x86-169.09-pkg1.run" command, An error displays "It appears that you are running an X server. Please exit X" (not the exact message but close enough). I do not know what to do next b/c...

2. The CTRL+ALT+ F1 does not work. When I press those keys my monitor displays "OVER RANGE" and then goes blank (ie black). However, my fan is still at 100% so I know my computer hasnt shutdown.

3. Also when I tell Ubuntu to shutdown my computer. It doesnt. My computer monitor goes blank exactly like in the problem mentioned above.

Any help would be much appreciated. Thanks in advance.

---

### Post by mahuyar on 2008-02-23
I may have a solution to your question #1.

Be very careful here.  I'll be disabling the gdm, which starts the GUI automatically, so that you'll just have a CLI.

In the terminal, go inside rc2.d folder:
```
 cd /etc/rc2.d/ 
```

There should be a link called S30gdm.  In your case, it could be a different number other than 30.  Now, we want to change the name of the link to s30gdm (note the small "s"):
```
 sudo mv S30gdm s30gdm 
```

Reboot your system, and you'll go directly into the CLI instead of your usual graphical login screen.  You can then install the Nvidia driver.

After successful installation, you can ```
 startx 
``` to start the GUI from the CLI.  

Just change back the small "s" to the capital "S" after you're done.  

So, how did it go?

---

### Post by Cresho on 2008-02-23
yeah you cannot just install it off the bat.  Your asking the driver to install itself Like if your in the middle of a videogame session.  what you need to do is exit and........well since you want bleeding edge, here is my notes.

new
on 32bit ubuntu


install dev tools in terminal before proceeding.

1. fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. uninstall in synaptic nvidia kernel common.  Do a search. apply the changes before exiting synaptic
4
5. log out of ubuntu after download is finished
6. hit ctrl+alt+F1
7. log into your username at the prompt in terminal
8. then in terminal cd /home/yourusername/Desktop (or the directory to where it got downloaded to)
9. ls (just to see if your in the right directory where you downloaded the file in firefox)
10. sudo /etc/init.d/gdm stop
11. sudo sh NVIDIA-fileversionorwhateveritis.run (ignore the question or say no to kernel download during instal and have nvidia xconfig update the x)
12. "sudo reboot" in the terminal
13. add startup file to system->preference->sessions "nvidia-settings --load-config-only"

add this to this section "Option         "NoLogo" "true""


Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "NoLogo" "true"
EndSection

after this mess, compiz needs to get configured correctly.  It will run like crap until you do this next few steps......well get back to me on this one.

16. test in terminal glxgears

---

### Post by Sarvatra on 2008-02-23
> **mahuyar said:**
> 
So, how did it go?


I tried what you said. I successfully installed the driver. But now I am stuck in the CLI. When I type in "startx" It says There's an "API Mismatch: This Nvidia driver component has version 169.09 but Nvidia kernel module does not match."

Any way to solve this problem through the CLI mode only? Else I might have to re-install Ubuntu all over again.

(PS I also noticed that when I was in the CLI mode, my fan was not making as much noise, but it wasnt completely quiet like it is in Windows xp).
---
@Cresho: I would have tried doing what you said, but I cant' do step 6 (see my problem #2 in my orignal post)

---

### Post by mahuyar on 2008-02-23
I guess there are driver conflicts with Ubuntu's inclusion of Nvidia's driver in the linux-restricted-modules and Nvidia's own driver from their website.  We may have to disable the Ubuntu's Nvidia driver.  Follow the steps in this [guide's]("https://help.ubuntu.com/community/NvidiaManual") "Disable Conflicting Software" section and see if it solves your problem.

---

### Post by Sarvatra on 2008-02-23
> **mahuyar said:**
> I guess there are driver conflicts with Ubuntu's inclusion of Nvidia's driver in the linux-restricted-modules and Nvidia's own driver from their website.  We may have to disable the Ubuntu's Nvidia driver.  Follow the steps in this [guide's]("https://help.ubuntu.com/community/NvidiaManual") "Disable Conflicting Software" section and see if it solves your problem.

I need help. I am completely new to Linux. How do I do what the guide says strictly from the CLI? 

thanks.

---

### Post by Cresho on 2008-02-23
yeah thats why i posted what I posted.  linux restricted does not work with this problem.  You need the latest and you dont get that with restricted.

---

### Post by mahuyar on 2008-02-24
> **Sarvatra said:**
> I need help. I am completely new to Linux. How do I do what the guide says strictly from the CLI? 

thanks.
OK.  Let's try Cresho's way.  Easier.

Since you're already at the CLI, we'll first try uninstalling the package, nvidia-kernel-common:
```
 sudo apt-get remove nvidia-kernel-common 
```

Now, Install the Nvidia driver that you've downloaded.  Say "No" to the question about downloading sources from the Nvidia's website, just as Cresho noted.  After install, reboot and... get back to us...  :)

---

### Post by Sarvatra on 2008-02-24
So I installed the driver 169.09 again after removing the nvidia-kernel-common. During the installation, it said: 

"unable to create /lib/modules/2.6.22-14-generic/volatile/nvidia.ko for copying" 
"unable to restore /lib/modules/2.6.22-14-generic/volatile/nvidia.ko"

BUT the driver was installed successfully.  I rebooted. At the CLI, I typed "startx" which

produced yet another error:  "Nvidia could not open device file /dev/nvidiact1/ (no such device or address)"

SO  I am still stuck in the CLI.

---

### Post by mahuyar on 2008-03-02
Still having the problem? Sorry I've been away for the past week.  I've come across a couple of threads with similar problems:

[Here]("http://ubuntuforums.org/archive/index.php/t-546607.html"), [here]("http://ubuntuforums.org/showthread.php?t=657035") and [here]("http://ubuntuforums.org/showthread.php?t=657798").

Any luck?

---

