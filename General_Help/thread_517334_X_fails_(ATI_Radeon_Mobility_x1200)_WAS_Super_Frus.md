---
title: "X fails (ATI Radeon Mobility x1200) WAS: Super Frustrated"
date: 2007-08-04
forum: General Help
---

### Post by rederic4 on 2007-08-04
Purchased a new Toshiba A215-S4697 laptop last week. It comes with an ATI Radeon Mobility x1200 card. I wiped the the drive and now would very much like to install ubuntu 7. I try and try but keep getting Server X failure screen. looked at forums and then tried to install with alternate CD......same result. All the help forums show I should "update" how can I possible do this when the program won't open or set up. Please remember I have NO OS currently on laptop.

Thank you for your help and please keep things simple for this newbe!

---

### Post by sab0403 on 2007-08-04
You get this error during installation, when booting with the LiveCD, or after you've installed?

---

### Post by Brunellus on 2007-08-04
Thread titled changed to something more relevant and/or helpful, in the hopes that knowledgeable eyeballs will see it.

If you have already installed Ubuntu and X keeps failing:

1) log in.  the black screen is not death--that's the command line, where the real work is done. Your username and password are the same.

2) execute

```
 sudo dpkg-reconfigure xserver-xorg
```

3) follow the prompts.  If you are in doubt as to the video driver to use, select VESA.  That will not be pretty, but should work.

4)  Reboot.

5) you should see some sort of GUI now.

The GUI however is not *strictly* necessary.  While still in the command line, you can update the system by executing 

```

sudo aptitude update

```

and then

```

sudo aptitude upgrade

```

---

### Post by rederic4 on 2007-08-04
Not sure how to answer but here goes. When I put in the first CD I burned which I beleive you are refering to as a live cd I clicked on test cd then install, as it was at what I presume was the end of the install I got the server x failure message. I then downloaded, tested and installed the alternate CD. It went through all it's setup (though it could not find aand setup a network). Install told me to remove CD and it would reboot. When it rebooted it attempted to load and then gave me the server x failure. Does that tell you what you want to know?

Sorry if that's not clear

---

### Post by rederic4 on 2007-08-04
okay I get that you want me to update but where is it updating from? I am not connected to the internet as I use a wireless card and that isn't configured yet is it? In case it isn't obvious I am using another computer to ask these questions

---

### Post by sab0403 on 2007-08-04
Yep, that pretty much answers my question. Please try the suggestion on the post above yours (#3). What you'll be doing is reconfiguring the X server, so (as Brunellus said) you'll have a functional, if ugly, GUI (graphical user interface). Once you have that basic GUI you can start troubleshooting it more easily.

And yes, the black screen is not death! It's just the command line. You'll have to use the command line from time to time in Linux, but it's pretty easy to use (particularly when following a tutorial or something). Good luck!

---

### Post by w4ett on 2007-08-04
From Grub, boot  into recovery mode.  This will get you to a command line.  From there type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will get you to an interface to select your video driver and resolutions.  scroll through the driver selections and select the 'vesa' driver, then select the resolutions that you want.  The cursor keys move the cursor, <spacebar> makes selections and <enter> confirms the selections.  Save and quit the interface, then type:

```
startx
```

this should get you into a GUI Desktop

OOPS----too late

---

### Post by Brunellus on 2007-08-04
> **rederic4 said:**
> okay I get that you want me to update but where is it updating from? I am not connected to the internet as I use a wireless card and that isn't configured yet is it? In case it isn't obvious I am using another computer to ask these questions
you didn't say you had no internet connection.  we're nerds, not mind readers, after all....

You could configure the wireless interface from the command line.  what is the output when you execute

```

ifconfig -a

```

and 

```

iwconfig

```

?

---

### Post by rederic4 on 2007-08-04
Brunellus - Thanks, got it, not mind readers, okay you need all info.

When I run iwconfig I get 
lo   no wireless extensions
eth0  no wireless extensions

if config-a gives me a page of information that at my typing level would take me a day to enter is there something you are looking for in particular?

---

### Post by Brunellus on 2007-08-04
it would appear your wireless card is not supported in the kernel;  to get it up and running, we'd need some ndiswrapper-fu.

Does/did the Live CD run on this machine?

---

### Post by rederic4 on 2007-08-04
Again I do not believe so. I never been anywhere but the black screen (which I am no longer afraid of).

---

### Post by rederic4 on 2007-08-04
BTW the vesa driver had the same result

---

### Post by Brunellus on 2007-08-04
I'm moving this to the general help forum;  I'm not terribly familiar with the ins and outs of X with this graphics card.  

The LIVE CD, by the way, is NOT THE ALTERNATE CD.  Again, did you use the DESKTOP CD to install Ubuntu the first time?

---

### Post by rederic4 on 2007-08-04
Yes I did use the Desktop CD when it didn't work (or gave me the server x failure) I then used the alternate CD.

---

### Post by rederic4 on 2007-08-05
Struggled with this for about 12 hours today. Then after reading a few more forums decieded to load program again using 6.06 LTS. Everything loaded fine and I am now installing to my hard drive. Thanks for all the help and advice. Ubuntu ROCKS!!!!!

---

### Post by rederic4 on 2007-08-05
I've had a couple of private messages so I thought I would give an update.While the Dapper 6.06 Live CD ran fine it would not install on my hardrive and kept hanging. Remember I had wiped my hardrive, this was not dual boot. I downloaded the Alternate CD (which wasn't easy, more later) and the install went smooth, I am still updating drivers and trying to get wifi to work but am generally pleased to have made the switch (after getting some sleep that is!)

The download page won't let you auotmaticlly download the alternate CD for dapper, whether you check the alternate CD box or not you get the desktop (or LIVE) CD file

To download alternate CD of Dapper go the the download page
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and at the very bottom of the page (below the start download button and check this box) is a link that says "complete list of downloads"  click this and find a site near you and enter the site to find the appropriate alternate CD download in this case 6.06. Good luck!

---

