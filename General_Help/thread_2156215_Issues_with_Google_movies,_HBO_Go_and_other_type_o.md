---
title: "Issues with Google movies, HBO Go and other type of authenticated flash video player"
date: 2013-06-20
forum: General Help
---

### Post by k-laminero on 2013-06-20
Hi!

I have searched extensively on the internet for an answer to this and no guide i followed helped.

When I rent movies from google play store (aka youtube) the video does not start. Recently, I got an HBO Go subscription. The videos used to play and within the same session it stopped working and now exhibits the same behavior as the google play rented movies, the video does not start at all. I just formatted and re-installed ubuntu from scratch and it did not help.

Here is my config:
Ubuntu 13.04 64bit
Chrome [COLOR=#303942][FONT=Ubuntu]Version 28.0.1500.52
[/FONT][/COLOR]I also have firefox version 21.

Chrome://Plugins returns:
[COLOR=#000000][FONT=Ubuntu]Adobe Flash Player (2 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202
Name:	Shockwave Flash
Description:	Shockwave Flash 11.7 r700
Version:	11.7.700.203
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)
   Enable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flash-plugin/libflashplayer.so
Type:	NPAPI
   Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Disable   Always allowed[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]

[/FONT][/COLOR]
I have tried different combinations of libflashplayer versions, enable and disable the pepper version etc.
It does not work regardless of whether i use chrome or firefox.

I have followed the tutorials below:
[http://ubuntuguide.net/install-adobe-flash-plugin-in-ubuntu-12-04both-3264-bit](http://ubuntuguide.net/install-adobe-flash-plugin-in-ubuntu-12-04both-3264-bit)
[http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html](http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html)

Didnt help.

Thank you for your time in helping me out! I have been struggling with this for a few months now.

---

### Post by k-laminero on 2013-06-20
Doing a couple more tests, I found something that might be a symptom (or not, who knows....)

Given my 2 flash plugins in chrome:
[COLOR=#000000][FONT=Ubuntu][INDENT]Description:	Shockwave Flash 11.7 r700
Version:	11.7.700.203
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)[/INDENT]
and
[INDENT]Version:	11.2 r202
Location:	/usr/lib/flash-plugin/libflashplayer.so
Type:	NPAPI[/INDENT]

[COLOR=#222222][FONT=Verdana]If I enable the first one and disable the second one, I get nothing when clicking on a HBO video. Just the black screen with arrows on each side. The behavior is the same if i enable both plugins. If I right click on the black screen, I get the adobe flash player menu drop down, with version 11.7... in "About"[/FONT][/COLOR]
[/FONT][/COLOR]
If I disable the first one and enable the second, I get the "Optimizing video quality" message  but it is buggy and doesnt do anything and I cannot right click.

---

### Post by niriksha on 2013-06-21
I am having the same issue...I've tried uninstalling and renistalling Flash, the web browsers and ubuntu...nothing is working.

---

### Post by k-laminero on 2013-06-25
Up

---

### Post by k-laminero on 2013-06-27
Up.
Does nobody know? or is this so obvious that nobody wants to answer my stupid question?

---

### Post by suphawk on 2013-06-29
Bump.. I'm also having this issue, hoping someone has found a solution.

---

### Post by CaptainMark on 2013-06-30
Read this, [http://askubuntu.com/questions/166760/how-do-i-play-movies-on-google-play](http://askubuntu.com/questions/166760/how-do-i-play-movies-on-google-play) worked for me (I believe you may also need some codecs included in the package ubuntu-restricted-extras)

---

### Post by coldraven on 2013-06-30
I'm guessing that your problem is similar to trying to watch 4OD in the UK.
I think that you have to install hal and disable pepper in Chrome. This from memory so do a search.
Install hal by "sudo apt-get install hal"

---

### Post by k-laminero on 2013-07-02
Thanks to all for your answers.
I disabled pepper in chrome, installed hal, deleted the content of the flash_player folder

Now I get consistent behavior on firefox and chrome, I get the 
HBO GO cannot play this show at this time. Please try again later. [Code D-1006]

I tested my players on the adobe drm test player

[COLOR=#333333][FONT=myriad-pro-1][FONT=inherit][h=2]Test protected video content playback using the demo player[/h][/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=myriad-pro-1][FONT=inherit]
[LIST=1]
[*]First, launch the Adobe demo video player container: [http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html](http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html)

Note the Adobe Flash Player version in the lower left of the demo video shell. Make sure that indicate 11.2 or higher
[*]Play sample protected content.

Enter the following URL in the field "Input the video URL: (case-sensitive)
[http://drmtest2.adobe.com:8080/Content/anonymous.f4v](http://drmtest2.adobe.com:8080/Content/anonymous.f4v)
[/LIST]
[FONT=inherit]
I get a device binding error (3322)

Starts to get video metadata at Mon Jul 1 23:24:36 GMT-0700 2013
DRMContentData received on Mon Jul 1 23:24:36 GMT-0700 2013
authenticationMethod = anonymous
ServerURL = [http://drmtest2.adobe.com:8080](http://drmtest2.adobe.com:8080)
license ID = 43345AEF-52FF-3F20-90FF-ABDC98A2E3E4


DRMErrorEvent dispatched by DRMManger received on Mon Jul 1 23:24:37 GMT-0700 2013
event type = drmError
Error Code = 3322 [DeviceBindingFailed]
Sub Error Code = 1107296263
Error Details = 
drmUpdateNeeded = false
systemUpdateNeeded = false


[/FONT]
[/FONT]
[/FONT][/COLOR]
I have read elsewhere that deleting the content of the ~/.adobe/Flash_Player folder resolves that. It hasnt for me. I am admin, I used sudo, and used dir afterwards to verify the content of the folder and the folder itself were deleted.
No dice.

Anybody's got a clue?

Thank you! :)

---

### Post by k-laminero on 2013-07-05
up

---

### Post by chaosrecords on 2013-07-05
> **k-laminero said:**
> up

I found this post surprisingly, by accident.

My HBO go is through TWC
I have the exact same issues as you, **only on win8 x64 and not Ubuntu.**
I could not get it to run in chrome for the life of me, tried beta chrome, dev chrome, flash plugins on and off....
Incognito mode wont work ( Error 8)


Then tried IE10, same thing- only it wouldn't take my login unless i put it into compatibility mode, then it wouldnt play in compatibility mode.
I thought maybe it was an authentication issue like I have had with Silverlight and Netflix in the past, but this was different.

I found a workaround that worked for me...
I just went and downloaded Firefox, then went to HBOGO.com, it told me i needed flash ( again) so i followed the link to flash and installed it.
Went back to Firefox and everything worked, i had it pull all my info from chrome upon install.

These are my running plugins/add-ons in Firefox

Citrix Online Web Plugin 1.0.0.97
Foxit Reader 2.2.3.402
Google Update 1.3.21.145
Java Deployment Toolkit 7.0.250.17
Java SE U25 10.25.2.17
Picasa 3.0.0.0
Shockwave Flash 11.7.700.224
Silverlight 5.1.20125.0
VLC 2.0.6.0

If the issue has something to do with the plugins, I wanted to at least share what I did to fix on Win8.. I know its not Ubuntu, but if its a flash/browser issue  maybe this can help you put the puzzle together if its plugin related.
Only other thing i can think of is checking the time/date of your computer to make sure its correct. 

Good luck, I was about 2 minutes away from ripping my tv off the wall in my office until I tried this. Its only working in firefox right now, which is ok for me[B]. Im on V22- you mentioned v21 earlier.. see if there is a beta for linux or update past v21 and give a try with firefox and those flash/shockwave versions.
[/B]

---

