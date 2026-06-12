---
title: "cant install ROS on virtualbox / ubuntu 12.04"
date: 2013-08-26
forum: General Help
---

### Post by Kevin_Henningsen on 2013-08-26
[COLOR=#525252][FONT=Arial]Hello.[/FONT][/COLOR]
[COLOR=#525252][FONT=Arial]I've tried to install ROS for the last two days, followed a few guides, tried to type in the installation commands in the ubuntu terminal a thousand times.[/FONT][/COLOR]
[COLOR=#525252][FONT=Arial]I have virtualbox installed I have the extension packages installed I have installed ubuntu 12.04 I have checked: mail, universe, restricted and multiverse in the software sources and unchecked the installable cd/dvd. I have updated in terminal by executing the sudo apt-get update command[/FONT][/COLOR]
[COLOR=#525252][FONT=Arial]everytime I enter this command: sudo sh -c 'echo "deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) precise main" > /etc/apt/sources.list.d/ros-latest.list'[/FONT][/COLOR]
[COLOR=#525252][FONT=Arial]Nothing happens, just a new line with: ubuntu@ubuntu:~$ starts.

some of the tutorial is from here:

[https://www.robotappstore.com/Knowledge-Base/ROS-Installation-for-Windows-Users/137.html](https://www.robotappstore.com/Knowledge-Base/ROS-Installation-for-Windows-Users/137.html)

[http://nootrix.com/2012/09/virtualizing-ros/](http://nootrix.com/2012/09/virtualizing-ros/)

[http://nootrix.com/2012/05/ros-installation/](http://nootrix.com/2012/05/ros-installation/)


[/FONT][/COLOR]
[COLOR=#525252][FONT=Arial]Another isues I also have is my keyboard has all the special signs like: _/(=&/¤*^" etc. swicted around, so I have to guess where they know are hidding even through I have my own country keyboard layout configurated, so what can that be all about?[/FONT][/COLOR]
[COLOR=#525252][FONT=Arial]Im so frustrated right now, so hope somebody can help me, I have tried google alot without any concrete help.[/FONT][/COLOR]
[COLOR=#525252][FONT=Arial]Best regards.[/FONT][/COLOR]

---

### Post by Azdour on 2013-08-26
Hi,

> 
sudo sh -c 'echo "deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) precise main" > /etc/apt/sources.list.d/ros-latest.list'


Hopefully by breaking down the above command you will see why nothing is output in your terminal even though it seems to have run successfully.

Ubuntu uses a list of repositories to know where to download a list of available software that you can install via 'apt-get install <softwarename>'.

Your command adds the [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) repository to Ubuntu to a file called ros-latest.list (by echoing/outputting the text in double quotes to a file that comes after the '>' symbol).  This files lives in the directory /etc/apt/sources.list.d/. This directory can contain one or more files that specify different repositories.

When you run:

sudo apt-get update

Ubuntu will search through /etc/apt/sources.list.d and pick up the files that contain repositories and from them obtain list of software that is available to install.

When you run your command it will not output anything to screen and it will return you to the terminal prompt as you have noted.

I would then suggest you continue on with the ROS installation guide @ [http://nootrix.com/2012/05/ros-installation/](http://nootrix.com/2012/05/ros-installation/) from step 2.

I hope that helps.

---

### Post by Kevin_Henningsen on 2013-08-26
Thanks a ton! Im at step further the goal now. but my problem is that I doenst have enough free space availble on my disk now. I have tried to clean and autoclean and autoremove. but still the problem is there. is it possible to add more space in virtualbox? or do I need to reinstall ubuntu in virtualbox and set the storage higher even through I have it a 1000 mb and 8 gb.. Im a noob, so im sorry for any confusions!

---

### Post by Azdour on 2013-08-26
Hi,

I know there are ways to increase the VirtualBox HDD but I've never tried it.  And having just Googled it - from what I've read so far it maybe easier to reinstall and create a bigger HDD.  Or maybe someone else in the forum may pop along with a solution you could follow easily.

---

### Post by Kevin_Henningsen on 2013-08-26
Thanks again. I've also runned some google pages through, but can't find a specific solution. I'll wait and see if somebody else have a solution or I might reinstall or find another pc to install ubuntu on without the virtualbox.

---

### Post by Azdour on 2013-09-10
Were you able to find a solution or did you reinstall?

---

