---
title: "LightDM with XFCE4 does not log in"
date: 2017-02-16
forum: General Help
---

### Post by avidichard on 2017-02-16
NOOB alert!

OK, so I just don't like the whole application package that Ubuntu ships with it's minimal or standard ISO so I decided to install the server distro and build everything from ground up. BUT before starting anything, I want my desktop back and I fell in love with XFCE so, I install the server with no additional packages besides the samba server. Once my installation is done, I do the following installations:


[LIST]
[*]sudo apt-get install xfce4
[*]sudo apt-get install lightdm
[/LIST]

Once that is done, I simply reboot. The lightdm screen appears and when I attempt to login, I get a"Failed to start session" message. The solution from this page does not work: [http://unix.stackexchange.com/questions/138995/xfce-session-fails-to-load-when-launched-via-lightdm](http://unix.stackexchange.com/questions/138995/xfce-session-fails-to-load-when-launched-via-lightdm)

I tried to change permissions on some of the XFCE folders but then again, no results. The best I got was no more messages but a black screen pops and I'm straight back to the login screen. BUT, when I run startsfce4, I get to the destop under sudo but cannot run it under my user. So the desktop is installed and lightdm also but for some reason, I can't get anything to work in harmony for only these 2 first installations as I did not install anything else besides these 2 packages.

For your info if needed, this is v16.10.

---

### Post by pqwoerituytrueiwoq on 2017-02-16
This should make it work as the normal user, given the username is avidichard 
```
sudo chown avidichard:avidichard -R /home/avidichard
```
you may want to delete ~/.Xauthority ([FONT=courier new]rm ~/.Xauthority[/FONT]) from a login shell (ctrl+alt+f1)

You may prefer the xfce Debian version
[https://www.debian.org/CD/live/](https://www.debian.org/CD/live/)

there is also a ubuntu mini.iso that lest you install just the stuff you want from the command line
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by avidichard on 2017-02-17
[FONT=courier new](rm ~/.Xauthority) says folder does not exist
And after ([/FONT]sudo chown {username}:{username} -R /home/{username})
Still the same problem. I also tried the minimal CD and LibreOffice and a few other softwares come with it without letting you disable these. That's why I chose the server version. Clean and no softwares, just the OS.
I'm still stuck with the same problem, Good password but same "Failed to start session" message.

---

### Post by avidichard on 2017-02-17
OK! I reinstalled everything AGAIN. I decided to not install lightdm yet. I installer xorg and xfce4 and tried to run xfce4 with "startxfce4". It does not boot and I see at the end of the xorg log file that I have a permission denied in tty0.

---

### Post by pqwoerituytrueiwoq on 2017-02-18
[https://xubuntu.org/news/introducing-xubuntu-core/](https://xubuntu.org/news/introducing-xubuntu-core/)
tried this?

---

### Post by avidichard on 2017-02-18
> **pqwoerituytrueiwoq said:**
> [https://xubuntu.org/news/introducing-xubuntu-core/](https://xubuntu.org/news/introducing-xubuntu-core/)
tried this?

No, I saw xubuntu and others but I wanted to learn from ground up how to install ubuntu for my personal education and to be able to solve my problems without the need of installing all-in-one packages. I'm a professional Windows technician but a total noob on linux. Of course I know a few things like using vim and navigating in command line but that does not help in resolving issues.

I've read in a forum that the best way to get an ultra clean ubuntu is to start by installing ubuntu server then the rest which is why I chose to do the installation. I tried xubuntu but it comes with other programs, even the slimmed down version and I wanted to install these manually to make a list of my own with a distribution that fits who I am and how I use it.

I tried OpenSuse and Mint but there's too much to get lost in with not very much possibilities to modify anything as I needed to uninstall stuff I did not need. And I also ran into problems with uninstalling applications, when deleting applications, well, the applications were removed from the applications list and then, when I rebooted, they were still installed. I got tired of this little game so I want to install what I need manually. But I've seen MANY posts using xubuntu and if there's nothing to do with my problem, I might try it as a last and only hope solution.

I just cannot believe that there's almost no solution to my problem. There seems to be a permission problem somewhere but I can't seem to find which folder and files. I'm still searching even though I posted this problem, I'm not relying only on this community, but you people seem very fun to deal with and I look into each of your solutions and take everything into consideration. But I want to find out why I cannot install that lightdm package to login my xfce4 desktop. I need to find out...

---

### Post by pqwoerituytrueiwoq on 2017-02-18
have you tried installing only lightdm and xfwm4? you will probably want to add the xfce4-panel if it is not included automatically i think something like this once, i seem to recall editing the startup script xfce uses for what i forget

you may want to look at the lubuntu-minimal package, if i recall the only gui software this includes is a terminal emulator, unless you count the window manager and panel i found this to be more practical

the server install does include a lot of useful command line utilities the mini.iso does not and will produce a install a fraction of the size (for example the package that lets you use the tab key to auto complete commands)

---

### Post by avidichard on 2017-02-22
OK so here is what I have done so far and the results but first, let me explain the problem in a simple sentence: Desktop shows up with no icons, no task bar and no possibities to right click anywhere, basically, just a background image.

These are the steps of my installation:
> 1 - Install Ubuntu Server on a Dell Inspiron 530 with a 160Gb hard drive
2 - Install the server with the following partitions:
  #1 300Mb ext4 "/boot"
  #2 6.4Gb Swap "/"
  #3 30Gb btrfs root
  #4 max btrfs "/home"
3 - Install no other softs besides Samba File Server
4 - Once installed and logged in, run the following commands
[B]  &#8226; sudo apt-get update
  &#8226; sudo apt-get install xfce4[/B]
5 - Add my user to the tty uuser group using this command
**  &#8226; sudo usermod -a -G tty username**
6 - Create the Xwrapper config file
**  &#8226; sudo vim /etc/X11/Xwrapper.config**
7 - Add these 2 lines while in vim in the empty Xwrapper.config file presently opened
  &#8226; allowed-users=anybody
  &#8226; needs-root-rights=yes
8 - Save and quit vim using by doing the following:
  &#8226; Press "Esc" key
  &#8226; Type ":wq!"
9 - At this point, running "**startx**" as my user will open up without any problems my xfce4 desktop (YAY!) but I'm not done
10 - Install lightdm using this command
**  &#8226; sudo apt-get install lightdm**
11 - reboot by executing this command
**  &#8226; sudo reboot**
12 - First login attempt, I get the "Failed to start session" message of death
13 - I then install this package using the following command
**  &#8226; sudo apt-get install ubuntu-session**
14 - Reboot again
**  &#8226; sudo reboot**
15 - 2nd attempt at loggin on but this time, no messages and I can actually loggon but on an empty desktop that does not have the same background as my initial "**startx**" 
So, can somebody tell me what I'm missing? It's been 2 weeks and I still cannot use lightdm which is supposed to be light weight and easy...Yeah right!

---

### Post by avidichard on 2017-02-22
I FINALLY found the solution!!! So here is how to install lightdm with xfce4 on a ubuntu server freshly installed:
*NOTE: I wanted a very light and basic ubuntu setup. My Ubuntu server is installed with ONLY the Samba Server Package, nothing else. This setup is basically a starter setup without the many different packages of full desktop distro.*

**1.** Install Ubuntu Server
**2.** Install the following packages using the following commands:
[B]  &#8226; sudo apt-get update
  &#8226; sudo apt-get install xfce4
  &#8226; sudo apt-get install lightdm
  &#8226; sudo apt-get install ubuntu-session[/B]
**3.** Add your user to the "tty" group using this command
**  &#8226; sudo usermod -a -G tty username**
**4.** Create the file "Xwrapper.config" using the following command
**  &#8226; sudo vim /etc/X11/Xwrapper.config**
**5.** Insert thes lines in the "[COLOR=#ff0000]Xwrapper.config[/COLOR]" file:
[COLOR=#ff0000]  &#8226; allowed-users=anybody
  &#8226; needs-root-rights=yes[/COLOR]
**6.** Create the file "lightdm.conf" using the following command
**  &#8226; sudo vim /etc/lightdm/lightdm.conf**
**7.** Add the following lines in the "[COLOR=#ff0000]lightdm.conf[/COLOR]" file (the allow-guest line is optional):
[COLOR=#ff0000]  &#8226; [SeatDefaults]
  &#8226; allow-guest=false
  &#8226; user-session=xfce[/COLOR]
**8.** Reboot using the following command:
**  &#8226; sudo reboot**

You should now be able to login your newly installed XFCE4 session using LightDM. It worked for me at least! Finally!!!

Small note for vim usage when wanting to add text, type "i" to enter the insert mode, then simply write your text. When you want to close the file and save simply hit the "Esc" key, which will place you in command mode and type these 4 characters ":wq!". "w" means that you want to write to the file and then "q" to quit. You want to write these in order as you want to write first then quit and not the opposite "qw" will simply quit without saving any changes as quiting and saving afterwards is not very logical.

*******NOTE:** If you are running nVidia Graphics Cards or others, its a good Idea to ONLY install XFCE4 WITHOUT LightDM and ubuntu-session first, then install your graphics driver, THEN, run the LightDM and ubuntu-session installation WITHOUT creating the Xwrapper.config file. In my case, I had an old 512 Mb nVidia GeForce 9600 GT and after installing the drivers, I had a conflit with my Xwrapper file so I deleted it and the system ran like a charm afterwards.

** **TIP:** Just a few recommendations for this minimal setup, I install "synaptic" for easy software installations and "alien" for repackaging "deb" files for special installations that only come packaged in a DEB format. I think that with these, you are pretty much covered with the basic installation and even the "synaptic" package is not THAT much necessary as you can just do everything in command line but I love the fact that synaptic tells you which packages to install in the case of dependancies, it can save you some time. But again, I'm just a new ubuntu commer and some people mught have some advice to give concerning this presented installation.

That being said, I never found any answers to my initial problem and had to do all the searching myself. When I searched...Well noone had any other solutions than to install a desktop package of Ubuntu which comes with hordes of softwares even with the minimal ISOs. I had to build up my own solution using answers like "Make sure that these lines are inside this file". I had no clue where these files were and which software actually creates these files so I had to find deep in where these files were located and of course, noone really gave any example of what these files contain SO, I decided to create them from ground up with, crossing my fingers that it would work and I'm happy to see that it did. I decided to create my desktop from ground up for my customers that feel that 150$ is too much for a Windows operating system and to lend my PCs to people without the fear of having them leave with expensive material without waranty of seeing them back. Turns out that this setup permit me to have an interface that resembles the one of Windows as XFCE4 is pretty neat in terms of customisation and you can actually recreate a full taskbar and environnement with ease and without too much tampering.

---

### Post by alexey2baranov on 2018-02-10
Great work!!

I have the same problem. And I was very surprising why nobody guide this regular workflow. Your post is the one all over whole internet! 

My addition is to use nano instead of vim. it is windows user frendly much more))

---

### Post by coffeecat on 2018-02-10
Old thread closed.

---

