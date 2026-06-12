---
title: "google earth 4.3"
date: 2008-04-16
forum: General Help
---

### Post by rfruth on 2008-04-16
works good but integrated graphics makes it painfully slow :mad: 

 New! in Google Earth 4.3 (beta)

    * Photo-realistic buildings from cities around the world
    * Dawn to dusk views with the Sunlight feature
    * Swoop navigation from outer space to street-level

---

### Post by unimatrix on 2008-04-17
Doesn't work for me. There is no earth, just space. Also I can't see any controls and I can't edit the Settings.

---

### Post by olzak on 2008-04-17
> **unimatrix said:**
> Doesn't work for me. There is no earth, just space. Also I can't see any controls and I can't edit the Settings.
Same here, but when I launch Google Earth as root it works.

It is something to do with installing Google Earth .bin package and some parts need administrator privileges.

---

### Post by Chilly_Willy on 2008-04-17
It installed fine on my hardy install. But when I start it the gui fonts are to small, unreadable.

---

### Post by EfChou on 2008-04-23
Alrighty,

Here's how I made google-earth work as user and not root:

First run the uninstaller in the directory you installed to (mine was /opt/google-earth)

so it was

```
sudo /opt/google-earth/uninstaller
```

then 

```
rm -rf /opt/google-earth/
``` 

and after that

```
cd ~/.config 
```

then do a 

```
rm -f Google/
```

finally, 

```
rm -rf .googleearth/
```

rerun the installer as root, and install to the default locations, after it is done installing **DO NOT** click start, click **QUIT** and then start google earth as your user, it worked for me. I guess the initial run is a setup of the files, so if you run it as root, it sets permissions for root only! :)

---

### Post by olzak on 2008-04-24
Starting Google Earth directly after install register ~/.config/Google folder as administrators privileges.

If You can't see Earth after install just change user rights of ~/.config/Google/ folder and .conf files inside it from root to yours.

---

### Post by ghob on 2008-04-24
"If You can't see Earth after install just change user rights of ~/.config/Google/ folder and .conf files inside it from root to yours."

Please mention how exactly am i supposed to do that?

---

### Post by olzak on 2008-04-26
> **ghob said:**
> "If You can't see Earth after install just change user rights of ~/.config/Google/ folder and .conf files inside it from root to yours."

Please mention how exactly am i supposed to do that?

Using the chown command.

In your home folder make follow

$ sudo chown username: .config/Google/*

where username=your home folder name.

Make notice that Google Earth 4.3 is now  included Medibuntu repository of Ubuntu 8.04. So You can install GE 4.3 with Synaptic or command: "sudo apt-get install googleearth"

How add medibuntu for Hardy see 
[http://ubuntuforums.org/showthread.php?t=713009](http://ubuntuforums.org/showthread.php?t=713009)

---

### Post by sartic on 2008-04-28
> **rfruth said:**
> works good but integrated graphics makes it painfully slow :mad: 

 New! in Google Earth 4.3 (beta)

    * Photo-realistic buildings from cities around the world
    * Dawn to dusk views with the Sunlight feature
    * Swoop navigation from outer space to street-level

I have dual core notebook and it is not problem in (slow) internal intel vga... it takes almost 100% of 1st cpu core. Old GE works great in Feisty on same machine...

---

### Post by frafu on 2008-04-29
Hello, 

The Accessibility Forum is intended for discussions about software that helps disabled people to use a computer. 

As the General Help forum contains other threads about google earth, I decided to also move this thread to the General Help forum. 

Cheers

Francesco

---

### Post by jonbriggs on 2008-04-29
I tried the above but still the same problem. MASSIVE FONTS 
[www.jonbriggs.dyndns.org/ge43.jpg](www.jonbriggs.dyndns.org/ge43.jpg)
Ugly Hey
Any thoughts?
Thanks in advanced
Jon

---

### Post by revelationman on 2008-05-01
I have installed it but when I launch it and It flashes black and grey so I have to shut it down. 

I have submitted a screen shot

---

### Post by jesse c on 2008-05-02
like ChillyWilly google 4.3 seems to be installed ok except the font is unreadably small,and actually if i zoom in they arent really letters at all,yet some font in help windows seems correct.Is this a beta bug that i should wait out or is there a fix?I went to google earth forums but i dont follow their file change fix being that i am a linux nube

---

### Post by dcstar on 2008-07-05
> **jesse c said:**
> like ChillyWilly google 4.3 seems to be installed ok except the font is unreadably small,and actually if i zoom in they arent really letters at all,yet some font in help windows seems correct.Is this a beta bug that i should wait out or is there a fix?I went to google earth forums but i dont follow their file change fix being that i am a linux nube

4.3.7204.0836 (beta) seems a lot better than some previous versions - I am impressed by the better resolution!

---

### Post by dr.phees on 2008-07-05
> **dcstar said:**
> 4.3.7204.0836 (beta) seems a lot better than some previous versions

That's true. I can't understand the still existent problems with the config file's privileges, though. The setup could have been fixed for some time now!

---

### Post by oscarmeyer51 on 2008-07-14
For those of you that are having difficulty viewing Google Earth (graphics issues), there is another post that suggests different video drivers and/or setting Atmosphere off. For the latter, open Google Earth (be pattient), then select the View menu option and deselect Atmosphere. That should speed things up considerably, even if it does not make things perfect. Unfortunately, I did not copy the link for the other post, but it is in the Newbie section (I believe) and can be found with the search keys of "GoogleEarth" "slow". Perhaps the forum moderators could supply those links when they get the opportunity.

---

### Post by oscarmeyer51 on 2008-07-14
Sorry, the url is here:

[http://ubuntuforums.org/showthread.php?t=833179&highlight=google+earth+slow](http://ubuntuforums.org/showthread.php?t=833179&highlight=google+earth+slow)

---

### Post by rogerdean on 2008-11-28
Hello all

Here's how I work around my GE probs (missing letters etc) on a Thinkpad X60s (Intel 945 graphics, 2gb RAM). It's probably very messy and with unnecessary steps, but this was what worked for me [insert general disclaimer here]

Install the old Intel i810 driver

```
sudo apt-get install xserver-xorg-video-i810
```

The I changed my xorg.conf file so the bottom bit reads like this -

```
Section "Device"
        Identifier 	"Intel Graphics Adapter"
        Driver     	"i810"
	VideoRAM 128000
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier 	"Default Screen"
        Device 		"Intel Graphics Adapter"
EndSection
```

Replace Google Earth 4.3 with 4.2 - not sure if this is necessary but I read somewhere that 4.2 has fewer graphics issues

Log out and in again or restart

Of course compiz is off, and after this change won't go on again, but GE works slowly (with atmosphere off) but correctly

Now, if anyone out there can refine the above I'd be very grateful!

Cheers
Roger

---

