---
title: "Install Juno Dial up"
date: 2007-02-19
forum: General Help
---

### Post by amdalex on 2007-02-19
At my house we have dial up internet and on my computer I have Ubuntu 6.10. I want to know how I could install Juno on this computer so I can get on the internet. Juno is a windows program too. And if there is a way to get connected to the internet with out installing the application could you tell me? Also I am typing this from a different computer.:confused:

---

### Post by djheadley on 2007-02-19
Does Juno offer a Linux version of their program?  If not it will probably be impossible to connect using Ubuntu.  I have Netzero and am "lucky" that they have a Linux version of the software needed to connect.  I don't know if anyone here has succeeded in connecting with Juno but you could do a forum search for "juno".

---

### Post by amdalex on 2007-02-19
Is there a program I could use to run windows based programs on Ubuntu?

---

### Post by amdalex on 2007-02-19
Guys I just found out they have a deb file. So I downloaded it now how would I install it. It is on the desktop. (I am setting this computer up at my house to take to my dad's house)

---

### Post by hikaricore on 2007-02-19
Try double clicking it?  That should bring up an installation dialog.  But this does not mean for sure that the debian package you downloaded will work with ubuntu, just be aware of that.  Personally I would never use a dialup service that required special software to connect to the internet, because that is ridiculous.

---

### Post by amdalex on 2007-02-20
I double clicked on the deb. file and it brought up an installation diolog. It said it installed fine but I can't find the shortcut on the desktop or in the applications menu. When I double click on the deb. file it asks me if I would like to reinstall Juno. If you could help me in any way that would be great. Also is there a program (preferbably free) that would let me run the windows version on ubuntu. Thanks for your help.

---

### Post by hikaricore on 2007-02-20
> **amdalex said:**
> I double clicked on the deb. file and it brought up an installation diolog. It said it installed fine but I can't find the shortcut on the desktop or in the applications menu. When I double click on the deb. file it asks me if I would like to reinstall Juno. If you could help me in any way that would be great. Also is there a program (preferbably free) that would let me run the windows version on ubuntu. Thanks for your help.

Not all software installs application icons.  You will need to read the documentation for the software to find out where it is located and how to run it.  If you can give me a link to where you got it, I might be able to help you out.

As far as software to run the windows version?  You could try Wine, but I doubt that would work.  For now lets try and get the native linux software for Juno woking and worry about the windows version if your not able to.

--Aaron

---

### Post by bionnaki on 2007-02-20
what's the name of the deb?

---

### Post by amdalex on 2007-02-21
Guys I logged in as root and the icon was on the desktop. So I just copied it to everyone else's desktop. I started it up and it worked. I have one question before trying to dial up. When I go to settings/network and I click on my modem it says that it is not enabled and if I try to enable it it want the ISP phone number and user name and password + other things like that. I just wonder if when I try to dial up with Juno will it automatically set up my modem or will I have to do that manually to make that modem work?

---

### Post by dmizer on 2007-02-21
it's impossible to say without reading the documentation.  i don't want this to sound like a rtfm post, but you're talking about proprietary software that juno developed.  this is not common software, and it is not supported by the linux community.

also ... since you are required to have an account at juno in order to even download the software, none of us can actually look at the documentation for you, and give you pointers.  google isn't yeilding much either.

so, you will most likely have to rely on juno for your support on this one.

try this:
```
man juno
```
and see if that shows you the documentation for the software.

---

### Post by amdalex on 2007-02-21
Well first I opened up the application and tried to dial up. It said "your modem is not defined make sure the file /dev/modem exists, so I enabled the modem and set it up to be in the port /dev/modem and Juno still gives me the same message. Also when I type /dev/modem into the file browser it says the file can't be found. Do you guys have any suggestions?:confused:

---

### Post by amdalex on 2007-02-21
Okay guys I investigated a little bit farther. I went into device manager and found the modem. I is listed for what type of device and ubuntu says it is unknown. So maybe I should try a different modem? Also I am still stumped about why I set it to make a port /dev/modem but the file is not there. Could you guys please help because I need this to work for my dad because his other computer died. And I don't want to let him down.:oops:

---

### Post by dmizer on 2007-02-21
try here: [http://www.ubuntuforums.org/showthread.php?t=308098](http://www.ubuntuforums.org/showthread.php?t=308098)

---

### Post by amdalex on 2007-02-22
bump

---

### Post by amdalex on 2007-02-22
Bump Bump Bump

---

### Post by hikaricore on 2007-02-23
Did you read the howto on setting up a dialup modem?  If not, Juno is not going to work, go set up your modem and stop bumping your thread.

---

### Post by Workinman57 on 2007-02-25
Refer to this link for more info on Juno 

[http://www.ubuntuforums.org/showthread.php?t=342189&highlight=Juno](http://www.ubuntuforums.org/showthread.php?t=342189&highlight=Juno)

---

