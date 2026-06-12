---
title: "Geforce2 Ultra, Compiz Fusion, Hardy"
date: 2008-05-01
forum: General Help
---

### Post by converted on 2008-05-01
I'm trying to help out my nephew as he tiptoes towards linux.  It should be noted that I'm not myself a linux expert, but I'm not quite a noob, either.

The whole thing that has attracted him to Linux is Compiz-Fusion.  At 11 years old, I suppose it's not surprising that the eyecandy is the first thing to grab his attention.  (Hell, I'm 36 and love CF.) :)

Anyhow, he's running a GeForce2 Ultra (64MB), which I gave to him, and which I am *mostly* sure I've used with Compiz or Beryl in the past.  (It's been in a bag for awhile, so I'm not positive about that.)  In any case, given some of the low end hardware that I *have* run CF on, it seems intuitive to me that this card would have no problem with it.

I have not yet been able to get over to his house to help troubleshoot his problem, but I'm expecting to get over there this weekend.

He's running Gutsy, though he was planning to upgrade to Hardy yesterday.  When I helped him to install Gutsy, I know that we enable the restricted Nvidia driver.

He tried to turn on CF a couple of days ago (enable desktop effects), and receive the error that desktop effects could not be enabled.

I've googled and searched this forum, and although I did find at least one thread regarding a GF2 Ultra and Compiz, I did not see a solution anywhere.

As my time with him this weekend will probably be brief, can anyone give me general suggestions regarding what steps I should take in trying to troubleshoot this issue?

Thanks!

---

### Post by Zorael on 2008-05-01
What is the terminal output of the following command?
```
$ compiz --replace &
```

---

### Post by starcannon on 2008-05-04
Drivers for that card can be had here:
[http://www.nvidia.com/object/linux_display_x86_96.43.05.html]("http://www.nvidia.com/object/linux_display_x86_96.43.05.html")

And a guide on how to install:
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) sudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) sudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.



```



I wrote that install guide for an nvidia 8400gs but it will work for the geforce2 as well, just use the geforce2 drivers instead.

GL

---

### Post by converted on 2008-05-17
Nice, thanks very much!  I've not seen my nephew since the original post, and have been reluctant to try to ask him to try anything from the command line just yet -- so we hadn't even taken the step from the first response.

I'll try to jump right into the driver install this weekend if we get over to see him.

Thanks!

Edit:  **Actually, it looks like you pasted the same link in twice.**  I'm googling for other info now, but if you've got a known good procedure I'd like to use that.

---

