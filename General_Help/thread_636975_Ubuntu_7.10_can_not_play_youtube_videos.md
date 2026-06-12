---
title: "Ubuntu 7.10 can not play youtube videos"
date: 2007-12-10
forum: General Help
---

### Post by athreyavc on 2007-12-10
Hi All,

I have installed the Ubuntu 7.10, I have been using the Fiesty since long time. But on Gutsy,

I am not able to play youtube videos. I have installed the flash player plugins . then when I try to open the youtube the system goes into hung mode every time.

Then I need to kill the X server and relogin again . The same problem appears again 

Please help me on the same ,

Regards,

Athreyavc

---

### Post by Jeanpaul145 on 2007-12-10
I had this problem as well. Since then I've reinstalled my Gutsy system due to some other problems.
Now I don't know yet, because after I've installed flash I still get the message that I don't have flash installed, with the question if I'd like to install it.

---

### Post by PrinceArithon on 2007-12-10
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

I suggest you guys go to the link I just posted there for you and see if that helps.  If you were there and it didn't help then please forgive me.

The only other thing I can think of is that if youtube still isn't working.  Turn off all other programs you got running like messengers or media players.  When I first started with Ubuntu I was using Dapper Drake and flash videos weren't working.  Then one day I just decided to turn off everything else that was running and they worked...I'm still not sure why, but it worked for me.

So I hope something works for you.

---

### Post by daradib on 2007-12-10
Jean Paul, see this for more information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by fragos on 2007-12-10
When someone says I installed a package that can mean many things from compiling source code to geting a binary from a 3rd party or idealy using Ubuntu repositories.  Your problem may stem from using a 64bit distribution -- IMHO switch to 32.  I can't know which problem each of you has but can say if you just install the package "ubuntu-restricted-extras" you should get a working flash and most of the other bits you want.

---

### Post by strabes on 2007-12-10
Like fragos said, install ubuntu-restricted-extras. It's the easiest way:```
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras
```

---

### Post by carlos1992 on 2007-12-10
go to the adobe flash website there is an option right there for [ubuntu]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") 
if you are done you should mark the thread as CLOSED, please

---

### Post by daradib on 2007-12-11
> **carlos1992 said:**
> go to the adobe flash website there is an option right there for [ubuntu]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") 
if you are done you should mark the thread as CLOSED, please

An option for Ubuntu would be new. But I don't see an option for Ubuntu.

Please see [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

This will show you how to fix this problem. Installing ubuntu-restricted-extras will NOT work right now, since the change in Adobe's flash installer file fails the md5 checksum, and therefore the flash player will not be installed (though it is marked as such in apt-get/dpkg/Synaptic).

---

### Post by Afkpuz on 2007-12-12
Don't know if this could cause crash, but the synaptic version of adobe is broken.  see my link here to fix the flash player.  It might fix your problem

[http://ubuntuforums.org/showthread.php?t=639029](http://ubuntuforums.org/showthread.php?t=639029)

---

### Post by daradib on 2007-12-12
The [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669) (which has been updated) has information about the fixed packages which have been uploaded to all supported proposed repositories (6.06-7.10). The binary packages should soon be built, but you can use the provided binary packages in that thread, which are compiled versions of the uploaded source packages.

That means the fixed binary packages should soon be available on the repositories (although you can use the my compiled versions of the source packages that are now availabe).

---

### Post by ozone702 on 2007-12-13
For days now I've been trying to fix this problem myself with no success.  I've finally got it working.

Here's what I did:

I went to System / Preferences / Sound.
I went to Sounds tab.
I changed Log in: to No sound.
I changed Log out: to No sound.
I re-booted.

When I went to YouTube.com, Firefox did not lock up when I played videos anymore.

NOTE:  Prior to this I tried everything I could find on these forums and others to resolve the issue with no success.  I'm new to Linux and Ubuntu but not to software development and I now know I did not fail to install necessary plug ins or drivers.  As a matter of fact, I turned the Log in back to what it was and re-booted to test whether videos locked up and as suspected they did.  So I'm certain this solved my problem.  Furthermore, I have had no problems for 2 days playing dozens of videos on YouTube and Break.com

I'm hoping this is a bug that can be identified and made known to everyone so this can be resolved and the community can move on.  Because this was a major hindrance to me using Ubuntu but not any longer.

Good luck,
  ozone

---

### Post by Lostincyberspace on 2007-12-13
That is interesting what prompted you to do that? Just pure curiosity?

---

### Post by ozone702 on 2007-12-13
The sound was too loud and choppy which annoyed me.  So I shut it off completely.

I'll bet there's a conflict when Ubuntu plays the sound it also tries to load the driver at the same time.

BTW, can someone respond to my post about a problem with VPN.  Its killing me that I can't use my wireless card now.

---

### Post by kaervos1024 on 2007-12-13
I had a similar problem on a Toshiba Satellite a105-s2081 (ATI sb450 HDA Audio). I ended up resolving it with the sound setup as well, but my solution involved changing all the sound playback options to OSS... I may have disabled ESD as well.

Its odd if you've just turned off the login and logout sounds and it started working.

---

### Post by athreyavc on 2007-12-17
Hi All,

Sorry for the delay in reply. I was out of town and away from my comp. I tried the steps as mentioned in the bug report . But it did not solve the prob, inturn now my comp gets hung if i try playing videos from youtube and hard reboot is the only option. 

Thanks and sorry again for the delay 

Regards,

Athreya VC

---

### Post by athreyavc on 2007-12-17
[FONT="Trebuchet MS"]Hi All , I am on the work again and bingo !! 
[http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669) this link solved it for me. I am an ardent fan of Ubuntu and I never wanted my PC not having Ubuntu on it.Now I am happy and releived. next work is to watch youtube videos. This issue as for me is closed. Thanks a million to all of you for guiding me here 
Best Regards,

Athreya [/FONT]

---

### Post by daradib on 2007-12-18
Happy to help. :-)

---

### Post by Milambar on 2008-01-14
This is giving me grief as well. Nothing I do will persuade it to play flash applets. Whenever I try, firefox just prompts me to download and install flash.

I have installed it directly from adobe.
I have installed it via synaptic.
and I have even tried installing it via apt-get and aptitude.

And still... "Additional plugins are required....."

Its been like this since I installed gutsy, and I'm guessing its going to be like this for a long time yet.

---

### Post by fragos on 2008-01-14
Check if you have the following file /usr/lib/firefox/plugins/libflashplayer.so

---

### Post by Jeanpaul145 on 2008-01-14
> **Milambar said:**
> This is giving me grief as well. Nothing I do will persuade it to play flash applets. Whenever I try, firefox just prompts me to download and install flash.

I have installed it directly from adobe.
I have installed it via synaptic.
and I have even tried installing it via apt-get and aptitude.

And still... "Additional plugins are required....."

Its been like this since I installed gutsy, and I'm guessing its going to be like this for a long time yet.

Have you tried removing flash with synaptic **before** installing it from the flash website?
Next to that, is your Gutsy x86 or x86_64 (32 bit or 64 bit)?

---

### Post by rekanoell on 2008-02-15
i tried the terminal and typed  the one for helix player  and then it asked for a linux password. i tried 1234 which is the default password in the start-up but it didnt work.

what do i do now?

aside from youtube. ubuntu 7.10 also cannot play sonific songspots and free movies in the internet. pls help!

---

### Post by fragos on 2008-02-15
install "flashplugin-nonfree" and Firefox will play Youtube .flv videos.

---

### Post by Ginsly on 2008-02-18
I know its an old post, but thankyou ozone702... I too was trying everything to make youtube work.... Your solution worked for me also....  Cheers!!!

---

### Post by akleck on 2008-02-21
> **ozone702 said:**
> For days now I've been trying to fix this problem myself with no success.  I've finally got it working.

Here's what I did:

I went to System / Preferences / Sound.
I went to Sounds tab.
I changed Log in: to No sound.
I changed Log out: to No sound.
I re-booted.

When I went to YouTube.com, Firefox did not lock up when I played videos anymore.

NOTE:  Prior to this I tried everything I could find on these forums and others to resolve the issue with no success.  I'm new to Linux and Ubuntu but not to software development and I now know I did not fail to install necessary plug ins or drivers.  As a matter of fact, I turned the Log in back to what it was and re-booted to test whether videos locked up and as suspected they did.  So I'm certain this solved my problem.  Furthermore, I have had no problems for 2 days playing dozens of videos on YouTube and Break.com

I'm hoping this is a bug that can be identified and made known to everyone so this can be resolved and the community can move on.  Because this was a major hindrance to me using Ubuntu but not any longer.

Good luck,
  ozone
ozone702 - Did you ever find out more on the strange sound problem (logon / logoff sounds) freezing up your system?

I am having the same problem.  In my case my problems seemed to start after I tried setting up my sounds on System/preferences/sound [sounds tab] to play custom WAV files.  I also messed with System/administration/login window/ [accessibility tab] Login screen ready: (tried to make it play a WAV file of my choosing).

Sometime after this (note my system startup sound never worked) any application that tried to play a file with sound (flash, totem, xine, etc...) hung up and had to be killed.

I followed your post:
   "went to System / Preferences / Sound.
   I went to Sounds tab.
   I changed Log in: to No sound.
   I changed Log out: to No sound.
   I re-booted."
and I aslo unchecked the System/administration/login window/ [accessibility tab] Login screen ready: sound check box.

Now everything seems to work fine, but what the heck is going on here?

---

### Post by daradib on 2008-02-22
Well I know that the System -> Preferences -> Sound is buggy and generally unreliable. It has given me problems when I change the devices and I then do not have sound. Even if I put the original settings back in place, I would still not have sound. The solution would be to delete .asoundrc.conf in the home directory, which appears to be some incorrectly made configuration. The delete would cause the default system-wide settings to take place.

If possible, look for a file called .asoundrc or.asoundrc.conf in your home directory (it will be hidden, so press Ctrl-H to view hidden files in Nautilus).

You can also try creating one manually. Try the command “asoundconf list” to list your soundcard names, then “asoundconf set-default-card NAME” should create the files.

---

### Post by Aries786 on 2008-02-24
Visit this link and follow the instructions it worked a treat for me

[http://www.lazytechguy.com/2008/01/installing-flash-plugin-in-firefox-on.html](http://www.lazytechguy.com/2008/01/installing-flash-plugin-in-firefox-on.html)

---

### Post by fragos on 2008-02-24
Having installed the flashplayer, you will find that Epiphany also has access to it.  Epiphany is the Gnome alternative to Firefox which can be installed by synaptic.  It also uses a version of the Gecko rendering engine used by Firefox.  Not as many features as Firefox but it's much faster.  One plus over Firefox is that viewing source comes up in gedit rather than a generic viewer. To be honest I've finally left Firefox and moved on with Epiphany. It's faster and doesn't crash.

---

