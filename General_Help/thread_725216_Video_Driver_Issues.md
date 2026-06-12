---
title: "Video Driver Issues?"
date: 2008-03-15
forum: General Help
---

### Post by MikeLX on 2008-03-15
system: AMD Duron 1gig, 512 ram, 32 shared S3 Prosavage KM133 onboard video, Ubuntu GG 7.10, 40 gig hd

my video playback is horrendous, firefox is very slow (not speed of internet, just slows down the computer in general) in general my gnome runs like crap. ive tried some other sessions xcfe icewm etc and they arent much better. this thing used to run xp and was fairly quick, so im assuming i have a video driver issue. i searched via's website for drivers with no luck, i also looked around for help with this card and ubuntu and havent found anything. i cant load the restricted drivers manager and when i try to change the card in the screens and graphics window i cant click ok after making changes. anyone have any ideas? and please make em simple, i am just getting the hang of ubuntu.


thanks,
Mike

__________________

---

### Post by por100pre1 on 2008-03-15
First, please remove your email address from the post. We don't want spam in your inbox.

Second, the system memory is too low for Gutsy, in my humble opinion. Go to **System> Preferences> Sessions**, and uncheck Tracker, a program that uses too much RAM.

Third, Verify the driver used by your card in **System> Administration> Screens and Graphics**.

---

### Post by MikeLX on 2008-03-15
> **por100pre1 said:**
> First, please remove your email address from the post. We don't want spam in your inbox.

Second, the system memory is too low for Gutsy, in my humble opinion. Go to **System> Preferences> Sessions**, and uncheck Tracker, a program that uses too much RAM.

Third, Verify the driver used by your card in **System> Administration> Screens and Graphics**.


thanks for the tip on the email.


ok, i didnt realize my sys was too slow for gutsy, it ran xp decently for a few years.  regardless if thats the problem then ok.

also the driver used by my vid card is :
"savage - S3 Savage, SuperSavage,..."

i have no idea whether thats the right one or not, lol heres how i can usually tell in xp if my graphics driver is installed right, i pick any window and drag it around, if it is choppy and leaves copys of the window as i drag it behind the driver is not right or not installed, this is what its doing in ubuntu.  normally it should drag nice and smoothly.  i can play mp3s and stuff perfectly and program load times dont seem too bad.

anyways thanks for the advice i shall try it and repost.

---

### Post by undecisive on 2008-06-06
Hi,

I have exactly the same problem. I'm running Xubuntu, and the time taken to render an application was appalling.

Your system is not too slow for linux. The reason I'm installing this is because linux should have performed far better than XP, however having tried kubuntu, ubuntu, vector linux and now Xubuntu, none of these gave a very good showing.

As you guessed, it's the video card that's to blame, or at least the linux drivers for it. We have an issue because this is now a "Legacy" system, and so all the conversations go back to (at least) 2002, and it doesn't sound like they were very well addressed even then. Via, who took over S3, apparently used to provide drivers for our system, however seem to have taken them down now - apparently they were shoddy anyway. 

Following advice from a few forums including [http://ubuntuforums.org/showthread.php?t=332025&highlight=Prosavage+KM133]("http://ubuntuforums.org/showthread.php?t=332025&highlight=Prosavage+KM133"), below the driver section of my /etc/X11/xorg.conf file. The improvements are noticable, but still not great - hope it helps.

```
	
	# The following must correspond with your Screens section
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"savage"
	# If this doesn't work, change the following to PCI -
	# apparently some cards don't like it
	Option 		"BusType" 	"AGP"
	# You may have to change Any to None if you experience lockups
	Option 		"DmaMode" 	"Any"
	VideoRam 	32768 # 32 x 1024, i.e. 32M 

	Screen	0

```

You may find you have to do 
```
modprobe savage
```
The link above may have more tips not covered here.

---

