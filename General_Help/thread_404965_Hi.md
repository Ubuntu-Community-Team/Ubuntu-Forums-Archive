---
title: "Hi"
date: 2007-04-09
forum: General Help
---

### Post by Kizilbas on 2007-04-09
Hi I'm a newbie on Xubuntu, I'm using 6.06 & I have a few problems.
Well with no knowledge at all i managed to install xubuntu from a .iso file i downloaded

When I try to adjust the date & time it says 'you are not allowed to access the system configuration' but I was able to adjust the time and date before I updated Xubuntu from the update menu.

2. The Second problem is with the sound of my computer, I can't hear any audio. How will I get it to work?

3. How can I use Msn Messenger on Xubuntu? (Installation and use)

4. How do I set my screen resolution? Currently I am using 640x430 or something like that, not sure.

:) help this newb lol

thank you

---

### Post by Kizilbas on 2007-04-09
Oh and I have something else to say, I currently have 18gb on the partition I've installed the OS Xubuntu on. 
Would 18gb be enough just to get around Xubuntu & work with it? (Simple operations such as Word Processing, Using the browser i.e. Firefox etc.

---

### Post by sam81 on 2007-04-09
I'm sorry I won't be able to give you much help on some of the problems, but I'll have a go

- 18 GB is enough, actually it's a lot of space for Ubuntu

- for the audio try to install the alsamixergui package, once installed you can run it just typing its name on a terminal, and see if you can get the sound changing the settings there. It might not work if there was a problem with your hardware detection, in that case, try to post your audio card technical specs

- for the screen resolution, you'll have to fiddle with a file called xorg.conf in the directory /etc/X11. You should be able to open it with
 sudo gedit /etc/X11/xorg.conf
look for a section called screen, and try to set the resolution there, again, if you have problems try to post your screen and video card settings, and someone might be able to help!

---

### Post by Kizilbas on 2007-04-09
Thank you for your reply sam81, I have fixed these problems by myself:

Date & Time
Screen Resolution (On the menu, duh?) lol

Problems left:
Msn Messenger on Xubuntu
Audio - Sorry as for being a beginner on Ubuntu I don't know where I could find the package you recommended. 

Thanks in advance :)

---

### Post by Kizilbas on 2007-04-09
I know this is going to sound very silly, but also how can I check the connections on Xubuntu.

i.e. on Windows via Command.com netstat [-a] [-n] etc..

ty very much all

---

### Post by Outrunner on 2007-04-09
For MSN you can use the GAIM client(soon to be renamed to Pidgin IM for legal reasons, I beleive). You can find it by going to Applications -> Internet -> Gaim Internet Messenger (-> Add-> -login details-)

---

### Post by Kizilbas on 2007-04-09
> **Outrunner said:**
> For MSN you can use the GAIM client(soon to be renamed to Pidgin IM for legal reasons, I beleive). You can find it by going to Applications -> Internet -> Gaim Internet Messenger (-> Add-> -login details-)

Outrunner I tried that, but I couldn't really get it to work
I am using @googlemail.com for my net passport and I must of misconfigured it so it didn't connect.

I'll try again & if there is no hope I'll play :guitar:  back to you

---

### Post by Outrunner on 2007-04-09
If you can't get it to work, you might want to check this out [http://gaim.sourceforge.net/faq.php](http://gaim.sourceforge.net/faq.php) - maybe you'll find something about your problem.

---

### Post by sam81 on 2007-04-09
for installing the package, from a terminal

sudo apt-get install alsamixer

or you can search it using the synaptic package manager. You might have to add the universe repository to actually download it

for the connections, I'm not sure in Xubuntu, but in gnome there are some gui tools to do that, in Xubuntu there should be also a panel applet for the connections (try rigt-clicking on the panel and add applet and see what comes out)
otherwise from the command line, I don't really know, the netstat command is there, try
man netstat 
to get more info

---

### Post by Kizilbas on 2007-04-09
For the network monitoring (connections etc..)

I right-clicked near the Applications menu on an empty spot and chose; 

+Add New Item, & from the list I selected Network Monitor (shows network traffic).
& I think it has a functionality to show the IP address & connectings Incoming - Outgoing. So for now I'm okay with that.

I tried that in the terminal it displayed this message:

**E: Invalid operation installer**

---

### Post by lerox on 2007-04-10
This might help you with your sound problems , seeing that xubuntu can only play .ogg files in it's native format ,you will have to install non free codecs for audio and video ,installing automatix is about the easiest way to get these problems sorted out follow this link ,find xubuntu installation matching your distro ie. dapper or edgy ,using the terminal copy and paste line by line till succesfuly installed.

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)

if this doesn't sort out your sound problem atleast you will have a very handy tool to save you time and frustration.

---

### Post by Kizilbas on 2007-04-10
> **lerox said:**
> This might help you with your sound problems , seeing that xubuntu can only play .ogg files in it's native format ,you will have to install non free codecs for audio and video ,installing automatix is about the easiest way to get these problems sorted out follow this link ,find xubuntu installation matching your distro ie. dapper or edgy ,using the terminal copy and paste line by line till succesfuly installed.

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)

if this doesn't sort out your sound problem atleast you will have a very handy tool to save you time and frustration.

Thank you very much lerox, I'll try this too :)

my regards.

---

