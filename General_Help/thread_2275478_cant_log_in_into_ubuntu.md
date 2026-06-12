---
title: "cant log in into ubuntu"
date: 2015-04-26
forum: General Help
---

### Post by ariel8 on 2015-04-26
hi!
today after restarting my PC it brought me straight to the login screen (which is unusual because i have it set to automatically log in)
and when i tried to login the screen went black for a sec and brought me back to the login screen, i tried other users and they didn't work either
guest user doesnt work, i tried.

---

### Post by ariel8 on 2015-04-26
anyone?

---

### Post by danny47 on 2015-04-27
I am slso having this issue after a full system freeze.

---

### Post by danny47 on 2015-04-27
Just fixed this using this article. [http://idiallo.com/blog/ubuntu-infinite-login-loop](http://idiallo.com/blog/ubuntu-infinite-login-loop)
hope this is of help. Seems like my nvidia drivers were causing the trouble.

---

### Post by ariel8 on 2015-04-27
> **danny47 said:**
> Just fixed this using this article. [http://idiallo.com/blog/ubuntu-infinite-login-loop](http://idiallo.com/blog/ubuntu-infinite-login-loop)
hope this is of help. Seems like my nvidia drivers were causing the trouble.
didnt work for me :/

---

### Post by Vladlenin5000 on 2015-04-27
> **ariel8 said:**
> didnt work for me :/

That's why Doctors exist... One man's medicine may not do any good for other person even if the symptoms are similar. danny47's advice, albeit quite well intentioned, may have led you into the wrong path.
There are multiple causes for the same symptom.

Do you even have nvidia hardware?

---

### Post by Bashing-om on 2015-04-27
ariel8; Hey ;

As a sanity check, can you boot to a console ?
At the login screen  key combo ctl+alt+F1 yields a console interface to the operating system.
Do you have authority to access your /home directory ?
```

ls -al .Xauthority
ls -al .ICEauthority

```
for reference; My outputs:
```

sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Feb  4 15:15 .Xauthority
sysop@1404mini:~$ 

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 1304 Apr 27 10:19 .ICEauthority
sysop@1404mini:~$

```
where I am 'sysop'

maybe the answer
[INDENT][INDENT][INDENT]maybe we hunt elsewhere
[/INDENT][/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-27
> **Bashing-om said:**
> ariel8; Hey ;

As a sanity check, can you boot to a console ?
At the login screen  key combo ctl+alt+F1 yields a console interface to the operating system.
Do you have authority to access your /home directory ?
```

ls -al .Xauthority
ls -al .ICEauthority

```
for reference; My outputs:
```

sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Feb  4 15:15 .Xauthority
sysop@1404mini:~$ 

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 1304 Apr 27 10:19 .ICEauthority
sysop@1404mini:~$

```
where I am 'sysop'

maybe the answer[INDENT][INDENT][INDENT]maybe we hunt elsewhere
[/INDENT]
[/INDENT]
[/INDENT]

i get the same thing but with my session name on both
and different dates

---

### Post by ariel8 on 2015-04-27
> **Vladlenin5000 said:**
> That's why Doctors exist... One man's medicine may not do any good for other person even if the symptoms are similar. danny47's advice, albeit quite well intentioned, may have led you into the wrong path.
There are multiple causes for the same symptom.

Do you even have nvidia hardware?
no i dont, i use AMD  radeon card

---

### Post by Bashing-om on 2015-04-27
ariel8; Well;

Having that return on the .Xauthority and .ICEauthority files is a good thing .

Let's poke at the GUI a bit more and see what bites back:
At the F1 console, what returns:
```

sudo service lightdm stop

```
"Assuming" here that you are running ubuntu with the unity (D)esktop (E)nvironment.
I do expect the system to tell you that you are nuts, the service is stopped/waiting or some such.

Now what does result when you start the desktop ?
```

sudo service lightdm start

```
post that output, as I do anticpate it telling you that a display can not be found.
In that case then we look at the graphic situation.

[INDENT][INDENT]admittedly, there is that path that seems logical, but
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-27
> **Bashing-om said:**
> ariel8; Well;

Having that return on the .Xauthority and .ICEauthority files is a good thing .

Let's poke at the GUI a bit more and see what bites back:
At the F1 console, what returns:
```

sudo service lightdm stop

```
"Assuming" here that you are running ubuntu with the unity (D)esktop (E)nvironment.
I do expect the system to tell you that you are nuts, the service is stopped/waiting or some such.

Now what does result when you start the desktop ?
```

sudo service lightdm start

```
post that output, as I do anticpate it telling you that a display can not be found.
In that case then we look at the graphic situation.
[INDENT][INDENT]admittedly, there is that path that seems logical, but
[/INDENT]
[/INDENT]

it said ```
lightdm stopp/waiting
``` when i ran the first command, when i ran the second command it brought me to the login screen with this output: ```
lightdm start/running, process 3647
```, tried to login, no diffrence from befor

---

### Post by Bashing-om on 2015-04-27
ariel8; Hummm ..

The display manager (lightdm) starting with no complaints blows that thought process.

When all else fails, read the instructions .
What have we got in the display log file ?
```

cat ~/.xsession-errors

```What graphics driver is in use ? and did it build ?
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]there is rhyme and reason
[INDENT][INDENT][INDENT][INDENT]just have not seen it yet
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-04-27
ariel8; My apologies ,

A lack of consideration that you may not be familiar with some tools at your disposal to relay the log files:
Ubuntu maintains a 'paste' site !
do this:
```

sudo apt-get install pastebinit
pastebinit ~/.xsession-errors
pastebinit /var/log/Xorg.0.log

```
these will result in a URL back to your terminal. ([http://paste.ubuntu.com/10916679](http://paste.ubuntu.com/10916679) , for example)

Pass these 2 URLs back here to the thread.

[INDENT][INDENT]so simple a Cave Man can do it
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-27
> **Bashing-om said:**
> ariel8; Hummm ..

The display manager (lightdm) starting with no complaints blows that thought process.

When all else fails, read the instructions .
What have we got in the display log file ?
```

cat ~/.xsession-errors

```What graphics driver is in use ? and did it build ?
```

cat /var/log/Xorg.0.log

```[INDENT][INDENT]there is rhyme and reason[INDENT][INDENT][INDENT][INDENT]just have not seen it yet
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

k, first 1:```
X Error of failed request: BadRequest (invalid request code or no such operation)
  major opcode of failed request: 155 (GLX)
  Minor opcode of failed request: 19 (X_GLXQueryServerString)
  Serial number in output stream: 22
openConnection: connect: No such file or directory
cannot connect to brltty at :0
script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
upstsart: at-spi2-registryd man focus ended, respawning
upstsart: at-spi2-registryd man focus ended, respawning
upstsart: at-spi2-registryd man focus ended, respawning
upstsart: at-spi2-registryd man focus ended, respawning
upstsart: at-spi2-registryd man focus ended, respawning
upstsart: gnome-session (Unity) main process (4524) terminated with status 1
upstsart: unity-setting-daemon main process (4510) killed by TERM signal
upstsart: at-spi2-registryd man focus ended, respawning
upstsart: logrotate main process (4393) killed by TERM signal
upstsart: update-notifier-crash (/var/crash/_user_lib_ibus_-ui-gtk3.1000.crash) main process (4424) killed by TERM signal
upstsart: upstart-dbus-session-bridge main process (4439) terminated with status 1
upstsart: update-notifier-release main process (4441) killed by TERM signal
upstsart: xsession-init main process (4505) killed by TERM signal
upstsart: hud main process (4507) killed by TERM signal
upstsart: disconnected from notified D-bus bus
upstsart: unity-panel-service main process (4529) killed by TERM signal
upstsart: unity7 main process (4519) killed by TERM signal
```
i am using an AMD radeon HD 6530D card with the fglrx driver

---

### Post by Bashing-om on 2015-04-27
ariel8; ....

I do not mind saying I am now getting into my learning mode .. and donning the thinking cap:
> 
upstsart: at-spi2-registryd man focus ended, respawning
upstsart: unity-setting-daemon main process (4510) killed by TERM signal

and others.
I have never encountered these before; presently I do not know where to go from here.
Maybe the Xorg.0.log will shed a bit of light my way ?

[INDENT][INDENT]I love it when this happens
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-27
> **Bashing-om said:**
> ariel8; ....

I do not mind saying I am now getting into my learning mode .. and donning the thinking cap:

and others.
I have never encountered these before; presently I do not know where to go from here.
Maybe the Xorg.0.log will shed a bit of light my way ?
[INDENT][INDENT]I love it when this happens
[/INDENT]
[/INDENT]

no offence but the xorg.0.log file is so long it would take me a few days to write it, any specific lines you are looking for?

---

### Post by Bashing-om on 2015-04-27
ariel8; oopps;

My post #13 must have got buried .
See if 'pastebinit' is not that answer.

[INDENT][INDENT]where there is a will there is a way - that is the 'buntu way
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-27
> **Bashing-om said:**
> ariel8; oopps;

My post #13 must have got buried .
See if 'pastebinit' is not that answer.
[INDENT][INDENT]where there is a will there is a way - that is the 'buntu way
[/INDENT]
[/INDENT]

FIRST COMMAND!:
[http://paste.ubuntu.com/10917177/](http://paste.ubuntu.com/10917177/)
SECOND COMMAND!
[http://paste.ubuntu.com/10917176/](http://paste.ubuntu.com/10917176/)
enjoy reading them
btw thx for helping me

---

### Post by Bashing-om on 2015-04-27
ariel8; Hey ;

"btw thx for helping me" No problem in doing that - open source -> we are all in this together. You will pass it on .

as to the "problem" give me a bit of time, do not despair .. I will return.
I know Ii have homework to do on this before I can ask an intelligent question.

[INDENT][INDENT]it is a thing , it is it is
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-27
> **Bashing-om said:**
> ariel8; Hey ;

"btw thx for helping me" No problem in doing that - open source -> we are all in this together. You will pass it on .

as to the "problem" give me a bit of time, do not despair .. I will return.
I know Ii have homework to do on this before I can ask an intelligent question.
[INDENT][INDENT]it is a thing , it is it is
[/INDENT]
[/INDENT]

okay :P i have my laptop so i can do most things i usually do

---

### Post by Bashing-om on 2015-04-27
ariel8; Welp;

A work in progress .
Looks like we do as a matter of fact have a graphics driver issue here:
From the xorg.0.log file:
> 
Good : (--) PCI:*(0:0:1:0) 1002:964a:1025:061d rev blah blah
Bad   : [  2199.583] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013
Bad   : [  2199.583] (EE) Unable to initialize PCS database
[  2199.583] (EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
[  2199.583] (EE) No devices detected.

Bad  : [  2199.619] (EE) No supported AMD display adapters were found
[  2199.620] (II) [KMS] drm report modesetting isn't supported.
[  2199.620] (EE) open /dev/dri/card0: No such file or directory

Bad  : [  2199.621] (**) FBDEV(2): claimed PCI slot 0@0:1:0 <- last resort driver ????

???  : 2199.635] (EE) GLX error: Can not get required symbols.

???  : [  2199.660] (EE) FBDEV(0): FBIOBLANK: Invalid argument


"Creating default Display subsection in Screen section " that should happen, I see no evidence of it !

Think what we have here is no driver available for the GUI .

Let's do purge FGLRX and install open source (radeon) and rebuild, Then see what we have:
```

sudo service lightdm stop ##stop the X display
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```
where here '##" and after are my comments, not to be entered into terminal .

Reboot, and tell me that all workie now. IF so then we consider installing the proprietary FGLRX driver.

[INDENT][INDENT][INDENT]looks like a plan to me
[/INDENT][/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-28
> **Bashing-om said:**
> ariel8; Welp;

A work in progress .
Looks like we do as a matter of fact have a graphics driver issue here:
From the xorg.0.log file:


"Creating default Display subsection in Screen section " that should happen, I see no evidence of it !

Think what we have here is no driver available for the GUI .

Let's do purge FGLRX and install open source (radeon) and rebuild, Then see what we have:
```

sudo service lightdm stop ##stop the X display
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```
where here '##" and after are my comments, not to be entered into terminal .

Reboot, and tell me that all workie now. IF so then we consider installing the proprietary FGLRX driver.
[INDENT][INDENT][INDENT]looks like a plan to me
[/INDENT]
[/INDENT]
[/INDENT]

OMG THANK YOU! IT WORKED! :D
now for the  proprietary FGLRX driver?
and should i update ubuntu to 15?

---

### Post by Bashing-om on 2015-04-28
ariel8; Outstanding !

OK, now ask yourself what function/ability you need that is not provided by the open source driver ?
What do you expect to gain from installing a proprietary driver ?

As You have experienced, installing the proprietary driver is not with out some maintenance overhead. If we stay within the ubuntu package management system for installing a proprietary driver that impact is lessened .

[INDENT][INDENT]is the risk worth the gain ?
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-28
> **Bashing-om said:**
> ariel8; Outstanding !

OK, now ask yourself what function/ability you need that is not provided by the open source driver ?
What do you expect to gain from installing a proprietary driver ?

As You have experienced, installing the proprietary driver is not with out some maintenance overhead. If we stay within the ubuntu package management system for installing a proprietary driver that impact is lessened .
[INDENT][INDENT]is the risk worth the gain ?
[/INDENT]
[/INDENT]

i mainly use my PC for 3d modeling, gaming, movies and basically anything, and there is an issue of the screen being bigger than what is displayed and it seems as the proprietary driver solves it, oh and my computer has fps issues without it
id say the risk is worth it, since we have a solution now.
and should i update ubuntu to the latest version?

---

### Post by Bashing-om on 2015-04-28
ariel8; Well ...

Release 15.04 does in deed have better hardware support. As to whether it is applicable to your hardware/situation ... beats me .
Best answer is try it and see.

OK, stepping up the ladder of graphics drivers:
What devices are identified :
```

ubuntu-drivers devices

```
 now list the proprietary video drivers available for your graphic card from the software repository:
```

ubuntu-drivers list

```

OK, you like what you see:
```

ubuntu-drivers autoinstall

```
to install the standard available proprietary video driver; This will install the latest proprietary video driver.

Now use the system, see that if now it is up to your use-case expectations.

else; well, there are 2 other rungs on this ladder that I am aware of .. Go further only on a need to go there basis .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-28
> **Bashing-om said:**
> ariel8; Well ...

Release 15.04 does in deed have better hardware support. As to whether it is applicable to your hardware/situation ... beats me .
Best answer is try it and see.

OK, stepping up the ladder of graphics drivers:
What devices are identified :
```

ubuntu-drivers devices

```
 now list the proprietary video drivers available for your graphic card from the software repository:
```

ubuntu-drivers list

```

OK, you like what you see:
```

ubuntu-drivers autoinstall

```
to install the standard available proprietary video driver; This will install the latest proprietary video driver.

Now use the system, see that if now it is up to your use-case expectations.

else; well, there are 2 other rungs on this ladder that I am aware of .. Go further only on a need to go there basis .
[INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]

okay i ran these 3 commands it solved the screen issue, i am upgrading the system now, thanks alot for helping me!
ill ask you if i need help with anything

---

### Post by Bashing-om on 2015-04-28
ariel8; OK .... BUT ->

An online upgrade requires that the system be as close to default as possible . That does mean reverting that proprietary driver back to open source for best results . ( and disabling ALL 3rd party software sources) ( disable any running screen saver)

It is probable that the installer will have no problem with the repo installed driver .. but

keep the installer within ubuntu's package management system for best result.

[INDENT][INDENT]not a problem
[/INDENT][/INDENT]

---

### Post by ariel8 on 2015-04-28
> **Bashing-om said:**
> ariel8; OK .... BUT ->

An online upgrade requires that the system be as close to default as possible . That does mean reverting that proprietary driver back to open source for best results . ( and disabling ALL 3rd party software sources) ( disable any running screen saver)

It is probable that the installer will have no problem with the repo installed driver .. but

keep the installer within ubuntu's package management system for best result.
[INDENT][INDENT]not a problem
[/INDENT]
[/INDENT]

just finished upgrading, it had no issues
ill mark the thread as solved, have a good day!

---

### Post by Bashing-om on 2015-04-28
ariel8; Good DeaL !

enjoy :)

[INDENT][INDENT]who said it could not be done ?
[/INDENT][/INDENT]

---

