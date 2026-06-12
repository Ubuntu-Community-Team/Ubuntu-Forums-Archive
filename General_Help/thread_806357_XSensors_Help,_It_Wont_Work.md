---
title: "XSensors Help, It Wont Work"
date: 2008-05-24
forum: General Help
---

### Post by kevo214 on 2008-05-24
I'm trying to get XSensors working so I can see all of the temperature information (I have overheating problems) but I can't seem to get it to work.

I installed XSensors from the Add/Remove Application
made sure lm-sensors were installed via synaptic
ran "sudo sensors-detect"answered yes to everything, and rebooted
tried to run XSensors and nothing happens
then I ran "sudo sensors-detect" again and answered no the very last question (write to files or something) and then rebooted, and still - couldn't get anything to happen

Anyone have any ideas?

"sensors" just returns the 2 cpus and "lm-sensors" returns "bash: lm-sensors: command not found"

---

### Post by linuxwizard on 2008-05-25
Look over this > [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto) > did you copy and save script ?

Read over > [http://www.lm-sensors.org/](http://www.lm-sensors.org/) > their maybe some notes on your motherboard or computer for specific configurations on setting up the lm sensors.

---

### Post by kevo214 on 2008-05-28
Unfortunately, I'm still not getting much working. XSensors wont boot up, and sensors only returns the temps for the two cores.

---

### Post by Dlizard on 2008-06-29
> **kevo214 said:**
> Unfortunately, I'm still not getting much working. XSensors wont boot up, and sensors only returns the temps for the two cores.

I had Xsensors working untill yesterday, when I had to reinstall Hardy due to a crash. Now it doesn't work anymore. The Xsensor icon is a dead icon. The only difference I can see between the previous situation and the one I have now is that the first Hardy was an upgrade from 7.10 while this one was installed from a CD. 

BTW, after having the message,  

> Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.

I gave up and installed ksensors instead (according to the instructions provided in [https://help.ubuntu.com/community/SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto"). It was not what I wanted, but it seems that there is no alternative.

---

### Post by waapwoop1 on 2008-06-29
x-sensors doesn't work for me.

What i worked out, was taht onthe panel, i could add the HDD and CPU temps. Which is much better so i can keep a constant eye on them because of the heat issues with Hardy on laptops.

if you have installed x-sensors and lm-sensors, you should be able to add to the panel. the program "x-sensors" doesn't work for me at all.

---

### Post by Weidbrewer on 2008-06-30
> **Dlizard said:**
> I had Xsensors working untill yesterday, when I had to reinstall Hardy due to a crash. Now it doesn't work anymore. The Xsensor icon is a dead icon. 


Ditto.  *click*  Nada.  I was figuring it was a Hardy issue as well.   If anyone has alternative programs or work-arounds, I'm all ears.

---

### Post by Elfy on 2008-06-30
I had to edit the launcher in the menu - right click to edit menu - navigate to system tools - right click the xsensors launcher - properties

add this to the launcher and see if it works for you

>  -c /etc/sensors3.conf

---

### Post by waapwoop1 on 2008-07-01
i tried that, it opens up a blank window with x-sensors 0.50. It does more now that it opens something. Still does nothing in the end.

---

### Post by Elfy on 2008-07-01
Run sensors-detect again - when it get's to the end it tells you wher it's going to write the information - check the file it is writing to - if it's different change the end of the launcher to suit.

---

### Post by wpshooter on 2008-12-21
> **forestpixie said:**
> Run sensors-detect again - when it get's to the end it tells you wher it's going to write the information - check the file it is writing to - if it's different change the end of the launcher to suit.

I do not see any prompt for a file that it is writing to.

Am I missing something here ???

Thanks.

---

### Post by Elfy on 2008-12-21
/etc/modules

But I believe that was a bug in hardy

---

### Post by wpshooter on 2008-12-21
> **forestpixie said:**
> /etc/modules

But I believe that was a bug in hardy

/etc/modules ???

Where and when during sensors-detect is a prompt for this location found ?

I have never seen any such prompt when running sensors-detect.  Again, am I missing something ?

Thanks.

---

### Post by Elfy on 2008-12-21
It doesn't prompt - but at the end, at least for me I get

>  will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to [COLOR="Red"]/etc/modules[/COLOR]:

#----cut here----
# Chip drivers
w83627hf
#----cut here----

But as I said that was I believe an old bug.

If you are having a problem - what is it?

---

### Post by wpshooter on 2008-12-21
> **forestpixie said:**
> It doesn't prompt - but at the end, at least for me I get



But as I said that was I believe an old bug.

If you are having a problem - what is it?

The problem that I am having is that Xsensors works just **GREAT** on every Ubuntu version up to and thru Gutsy but will not work with any version above Gutsy.

Thanks.

---

### Post by businessjeff on 2009-02-03
Im having the same sort of problems, when I load the app Xsensors its just a blank window with "xsensors 0.50" at the top.

I got the app with add/remove
I ran the sudo sensors-detect command
When prompted at the bottom, this is what it was determined.

To load everything that is needed, add this to /etc/modules:
> 
#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
it87
k8temp
#----cut here----

Do you want to add these lines automatically? (yes/NO)

So whats that mean? Is this not compatible with my mobo? or what, idk much about any of this.

From here, I added the string
> 
-c /etc/modules

to the command line of the xsensors app. However, what is this about it being a bug? Im running ubuntu 8.10. Ive seen people saying your supposed to add this,
> 
-c /etc/sensors3.conf

that didnt work either. Ive opened that file it is on my comp, idk if you need to know that or not.
One last thing, Ive read that you should run this command,
> 
sudo modprobe XXXX

XXXX being the code you get from running the detect command...? says it should be something like, w83627hf. As seen above in the results of my detect command, I see nothing of the such. Heres the thread im talking about

[http://ubuntuforums.org/showthread.php?t=812859]("http://http://ubuntuforums.org/showthread.php?t=812859")

---

### Post by zuerston on 2009-06-13
mine not work either.

trrminal says [CODExaaxa@xaaxa-laptop:~$ -c /etc/sensors3.conf 
bash: -c: command not found
xaaxa@xaaxa-laptop:~$ /usr/bin/xsensors -c /etc/sensors3.conf 
Sensor 'k8temp' not supported by xsensors!

][/CODE]

means not much to me ,do you know?

---

### Post by Amilo1718 on 2009-06-14
[COLOR="DarkGreen"]**This worked for me**[/COLOR]

**Using Sudo to install lm-sensors**

Open a terminal window.

Enter the command:

sudo apt-get install lm-sensors

Enter your root password and away you go.
[B]
Configuring lm-sensors[/B]

In the terminal window, enter the command:
sudo sensors-detect

It will as you a bunch of questions that you enter YES to and then shows you a summary of the probes and the findings. It will offer to update /etc/modules automatically and you might as well let it do so otherwise you have to type it in yourself.

**[COLOR="DarkGreen"]Then enter in the terminal: sensors[/COLOR]**

---

### Post by qbee42 on 2009-06-24
XSensors is blank for me as well. I can see CPU temperature sensor information by typing sensors at the command prompt, but running the graphical application XSensors yields nothing but a very very small blank screen. I recall that XSensors worked a few Ubuntu versions ago, but it's not working with my 9.04 (jaunty) system.

Tom

---

### Post by Objekt on 2010-01-17
> **qbee42 said:**
> XSensors is blank for me as well. I can see CPU temperature sensor information by typing sensors at the command prompt, but running the graphical application XSensors yields nothing but a very very small blank screen. I recall that XSensors worked a few Ubuntu versions ago, but it's not working with my 9.04 (jaunty) system.

Tom

Having the same problem with Ubuntu 9.10 on my system.  All I can get sensors to show is the CPU core temps.  I would like to see fan speeds as well as any other temperatures available.  Is there a fix?

Xsensors shows nothing for me as well.

---

### Post by HectorG on 2010-01-30
still having same problem here

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
#----cut here----


Intel i7 920 on an Asus p6x585 Premium board

Any ideas?

---

### Post by Objekt on 2010-02-09
Well...rats.

I thought Xsensors and/or lm-sensors was just broken at first, but I think maybe my hardware just isn't supported.

The only thing I can get is temperatures of the 2 CPU cores.

Apparently, my motherboard has a Winbond W83627DHG chip, which is only the CPU temp sensors.  Whatever other stuff my motherboard has, for detecting bus voltages and so on, doesn't seem to be handled by lm-sensors.

For Windows, Asus supplies an application that shows you all that stuff.  I guess they're using some kind of microcontroller with proprietary code or undocumented features for monitoring voltages.

FWIW, I have an ASUS P5E3 WS Pro motherboard.

Are there any alternatives to lm-sensors?

---

### Post by Sand Lee on 2010-02-18
[LIST]
[*]Please try the new xsensors 0.70 package in debian unstable: [http://packages.debian.org/sid/xsensors](http://packages.debian.org/sid/xsensors)
[*] Here's the changelog since 0.50: [http://packages.debian.org/changelogs/pool/main/x/xsensors/xsensors_0.70-1/changelog](http://packages.debian.org/changelogs/pool/main/x/xsensors/xsensors_0.70-1/changelog)
[*] Lucid will have this new release as well.
[/LIST]

---

### Post by Objekt on 2010-02-18
.deb package and all eh?  Thanks, I'll give it a try.

Well, that isn't going to work.  The Xsensors 0.7 .deb keeps saying I'm missing a required dependency (Error: Dependency is not satisfiable: libfontconfig1 (>= 2.8.0)).

It gets worse from there.  Trying to install the .deb for libfontconfig1_2.8.0 doesn't work either.  It has its own dependencies it complains about.

I could spend all day going down this rabbit hole and STILL not have it work.  Not going to do it.

---

