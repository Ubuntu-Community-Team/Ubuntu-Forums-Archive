---
title: "sane backend from cvs"
date: 2005-10-06
forum: General Help
---

### Post by Denis on 2005-10-06
Hi

I've got a scanner that is supported by the CVS version of SANE. Unfortunately it is not supported by the current version in hoary. 
I tried to install SANE CVS from the official (debian) repositories (added them to my sources.list). But I couldn't install it, because of dependency problems (with libc for example). 
Is there a way to install the backend anyway? If not, will Breezy have a newer version of SANE? 
My scanner is a Canon CanoScan Lide 25. 

Thanks in advance.

---

### Post by Denis on 2005-10-10
Is there no one who can help me?

---

### Post by RandomGeek on 2005-10-10
Hey, I'm afraid I can't help but I may be able to soon.  I also have a Canoscan LiDE 25 and am in the process of trying to get it to work with Breezy.

Unfortunately breezy comes with sane v1.0.15 which doesn't yet support the 25.  To support our scanner we need to manually compile/install the latest nightly sane builds.

So far I've got the scanner detected and passing a test but not actually got a front end connected so no scans yet! Will post instructions if I suceed :)

---

### Post by danelb on 2005-10-10
Unfortunately breezy comes with sane v1.0.15 which doesn't yet support the 25.  To support our scanner we need to manually compile/install the latest nightly sane builds.

how do you go about manually compiling?  I have an epson cx 4600 which is not supported at this point, but there is a package - libsane-epson.a -  do i need ot do something with it? how do i know if the package has what i need, and how do i get it all hooked up?

thanks
dan

---

### Post by ChrisTheGeek on 2005-10-11
Hmm, according to the SANE website here:

[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

You're scanner is supported in version 1.0.16 so you should be able to find a deb package and update yourself without manually compiling.  There is some pretty good help on the site.

Unfortunately to get my scanner going I need a deb package for the very latest code (which will become 1.0.17 eventually) but I got dependency problems when I tried to install it.  Hopefully 1.0.16 won't have that problem for you.

I will post here again if I manage to get my self-compiled version going. Good luck!

---

### Post by bonjun on 2005-10-13
[QUOTE=ChrisTheGeek]Hmm, according to the SANE website here:

[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

You're scanner is supported in version 1.0.16 so you should be able to find a deb package and update yourself without manually compiling.  There is some pretty good help on the site.

Unfortunately to get my scanner going I need a deb package for the very latest code (which will become 1.0.17 eventually) but I got dependency problems when I tried to install it.  Hopefully 1.0.16 won't have that problem for you.

I will post here again if I manage to get my self-compiled version going. Good luck![/QUOTE]

how to "compile manually",,, sorry newbie here

---

### Post by ChrisTheGeek on 2005-10-13
Hey bonjon,

If you are new to compiling programs I hope this guide will help:

[http://www.linuxforums.org/tutorials/1/tutorial-19957.html](http://www.linuxforums.org/tutorials/1/tutorial-19957.html)

Also, it's worth knowing that most source files you download come with a README file that lists any extra instuctions specific to that program.

---

### Post by davmac on 2005-10-24
[QUOTE=RandomGeek]
So far I've got the scanner detected and passing a test but not actually got a front end connected so no scans yet! Will post instructions if I suceed :)[/QUOTE]

Hi,

Did you get any joy with this? I too have a Canon Canoscan LiDE 25 and am about to start trying to build from the Sane CVS source.

Dave Mac

---

### Post by ChrisTheGeek on 2005-10-24
Yeah, I got it scanning ok from the command line with a self-compiled copy.  Had trouble with the front-end not picking up the device.  Also, had to be root to scan due to the hotplug permissions script not working correctly.

I have a couple of ideas left but I've been short on time lately.  I will try and have another go this evening or tomorrow.

Chris

---

### Post by ChrisTheGeek on 2005-10-25
I had another go last night. Still no joy.  Basically I just compiled the cvs sane over the installed sane and tried the following:

sane-find-scanner

Which reported the scanner correctly

scanimage -L

Which found the scanner correctly once I had manually set the permissions on the usb device (otherwise it would only find it when using sudo).  I was able to scan a picture on the command line at this point.

I then tried loading XSane from the main Applications menu and it told me there were no supported devices.  So I tried calling xsane from the terminal like this:

xsane plustek:/proc/bus/usb/001/002

And it complained about a very vague IO error.  I have a couple more ideas but I was hoping this would have worked.  I'm going to try looking at the plustek.conf file tonight to see if there is something I need to change.

---

### Post by ChrisTheGeek on 2005-11-08
I still can't get xsane to work but have perfect scanning from the command line.  I also tried Kooka but again it didn't detect the backend.

I can get a full A4 scan using 'scanimage' setting l/t to 0, x/y to max and resolution to 125. (type scanimage -h to see the options and what they do).

I'm not sure what the next step is really.  If anybody knows why no front-end is detecting a scanner that seems to work fine then please let me know - it's driving me mad!

Thanks,
Chris

---

### Post by ChrisTheGeek on 2005-11-22
Sussed it.

Since no frontend seemed to be able to detect the updated backend I got back to basics and challenged the assumptions I'd been labouring under.  The main assumption was that when you compiled your own version of sane it overwrote the ubuntu one... nope.  Not with the default ./configure anyway.  Doing 'whereis sane-find-scanner' gave the problem away since there were two copies of that program installed.

Anyway, here's what I did to make it all ok:

- Make sure sane and xsane are installed in synaptic
- Install the package libusb-dev  (This is very important!)
- Download the lastest nightly sanebackend file from their cvs snapshots
- untar the file to a directory somewhere e.g. /home/you/Desktop/sanebackend
- Go to a terminal and type the following:

cd ~/Desktop/sanebackend
./configure --prefix=/usr --sysconfdir=/etc
make
sudo make install

Now the updated backends should be there. To test it try the following:

sudo sane-find-scanner

sudo scanimage -L

Both should show your scanner detected.  If you run xsane as root at this point it should all work.

Obviously running as root sucks so you need to fix the permissions.  I had to edit the mapping file under /etc/hotplug to add an entry for the canoscan.  The line I added was:

# cannon scanner
libusbscanner             0x0003      0x04a9   0x2220  <the rest are all 0s>

After editing the file I restarted hotplug with:

sudo /etc/init.d/hotplug restart

Now unplug your scanner, plug it in again and you should be able to see it when you type 'scanimage -L' as a regular user.

I hope this helps somebody out.  Let me know if I haven't made anything clear.

Chris

---

### Post by Denis on 2005-11-23
Great that you've figured this out!

I will try it when I have some more time (as I may want to update to Breezy too). I'll remember to post some feedback then. 

By the way: I've read some thinks about checkinstall (it generates a deb file and shows the package in synaptic), would it be possible to use it here instead of just install?

Great work ;)

---

### Post by ChrisTheGeek on 2005-11-28
Hi, yes, checkinstall should work here.

Checkinstall is most useful when the provider doesn't give you a 'sudo make uninstall' option.  Sane does provide this though so it's easy enough to uninstall.

Hopefully it won't be too long before there is a new official version of the sane package for Debian/Ubuntu.  Version 1.0.17 is due to be released this December.

Good luck getting your scanner going!

Chris

---

### Post by M4VE on 2005-12-26
Could you explain to me where I get the info for the usb.handmap line?  I'm guessing you're referring to Vendor and product id, but adding just those two hex codes does'nt work, where did you get the zeros from?  Any help would be appreciated.  Oh, and if it helps, I have an X1185 recognized as an X1100 series by Sane.  Also, running Xsane as root doesn't seem to perform a scan, it starts making a few noises, but never moves anywhere, or scans, and then xsane locks up, any advice on that?  Thanks A bunch for your help.

---

### Post by marnom on 2005-12-28
Actually, I had to edit /etc/hotplug/usb/libsane.usermap to make it work...

---

### Post by almalaci on 2007-10-16
I have tried this before and it didn't work but with the newest sane-backends it does!!
Thanks a lot, it was helpful. Although I don't seem to have a usb hotplug folder anywhere, so I can't put my modified libsane.usermap file to make it work for normal user. 
Could anyone help with that?

---

