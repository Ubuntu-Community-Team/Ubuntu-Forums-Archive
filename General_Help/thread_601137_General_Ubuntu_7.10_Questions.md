---
title: "General Ubuntu 7.10 Questions"
date: 2007-11-02
forum: General Help
---

### Post by lferree on 2007-11-02
I just want to start off by saying, Ubuntu is amazing!  I'm a Linux noob, but a fast learner.  I hope to have all my PCs and notebook running Ubuntu by month's end.

My first computer ran DOS 3.x.  Back in the day, I used to know how to do everything from the prompt, then came Windows and I became too lazy to move my hand from the mouse.

I didn't really give much thought of moving to Linux until Vista.  Vista is a hog.  Even with a kick-butt setup, it eats up too many resources IMO.  I've been a hardcore Media Center fan for years.  The straw that broke the camel's back was problematic DRM protection on my Vista Media Center.  If I can't watch the content I pay for on the Media Center I purchased, to heck with MS!  It bothered me too that new games require Vista, when I know it's just a way for MS to push this piece of bloat-ware out the door.  I mean seriously, they could offer DirectX 10 or whatever for XP.  Gimme a break.  Oh, 
did I mention I'm a hardcore gamer!  Lucky for me my passion is World of Warcraft, which can run happily under Linux.  I will admit that MS has stepped it up for security.  I think it's a great idea to offer this stuff built-in for the novice user.  Personally, I turn all that stuff off, as I use third-party apps that I find much more secure.

On another note, there's very little keeping me from making a complete switch over.  I can export my mail to Thunderbird and then into Evolution.  My MS Office documents all seem to work just fine under Open Office.  My MSN Messenger contacts, TeamSpeak, Ventrilo Server all work without a hiccup.  I can stick a thin install of Windows 2000 in VMWare to run the Ventrilo client.  With a little tweaking, I can have a way better Media Center with MythTV.  Been using Firefox for years and it's already in Ubuntu.  Woot!  Videos, Music and Pics are all available.  The network sharing is great, and with the new update I can now write to NTFS partitions.

I am having a few problems however.  I was running World of Warcraft great in 7.04 using CrossOver.  I was also using Beryl, which apparently isn't even offered thru the Synaptic Package Manager any more.  I now get "[COLOR="Red"]World of Warcraft was unable to start up 3D acceleration.[/COLOR]"  I think this has something to do with the new Compiz.

I tried the following, but it didn't fix the problem:
  Ctrl-Alt-Backspace
  sudo apt-get install nvidia-glx-new
  Reboot

I also downloaded Wine thru the Synaptic Package Manager, Warcraft didn't like that either.

I did notice the update fixed a problem I was having with Beryl...  I didn't have window borders, and when I opened terminal, it was all white.  I could still mouseover the menu text, but couldn't actually see the text that was there.

Also wanted to mention all my Gnome applet error messages are now fixed since the latest update.

Another strange problem I'm having is with [COLOR="Red"]XVID videos[/COLOR].  Some of them work fine with the codecs I downloaded when prompted by Movie Player, but some of the newer ones show a green line vertically on the right side, and one horizontally towards the bottom.  The video looks scrambled like you would get when tuning into a cable channel you didn't pay for.

I was also wondering...  Can I install software in Ubuntu that isn't available thru the Synaptic Package Manager or Add/Remove...?  I've noticed a few formats out there like RPM, .sh and pkg2.run.

Any suggestions for a good Nero Burning ROM alternative and some sort of simple invoicing software?

Anyhow... any help would be greatly appreciated.  I built a second system just for Ubuntu and I find myself using it more than my "Windoze" machine.

---

### Post by seshomaru samma on 2007-11-03
Hello and welcome to Ubuntu

> .Another strange problem I'm having is with XVID videos. Some of them work fine with the codecs I downloaded when prompted by Movie Player, but some of the newer ones show a green line vertically on the right side, and one horizontally towards the bottom. The video looks scrambled like you would get when tuning into a cable channel you didn't pay for.
which player are you using to view these videos, are you sure you have all the codecs?
> I was also wondering... Can I install software in Ubuntu that isn't available thru the Synaptic Package Manager or Add/Remove...? I've noticed a few formats out there like RPM, .sh and pkg2.run.
yes you can. check out[ this link]("http://monkeyblog.org/ubuntu/installing/")
> Any suggestions for a good Nero Burning ROM alternative and some sort of simple invoicing software?
don't know about invoicing but there is Nero for linux. It is not free. I use k3b which is an excellent programme. 
I don't know the answers to the rest of your question but using the search funtion in this forum is likely to bring some of the answers. I would also suggest opening several threads for your questions
Many people (like me) scan the thread titles for areas with which they are familiar. If I see a thread about SCIM I will answer it, if it's about WOW I wont. 

Good luck

---

### Post by lferree on 2007-11-03
Thank you for the response.

I'm using "Movie Player" that came with Ubuntu.  I also got "MPlayer Movie Player".  Both have the same problem with certain XVID videos I have, most of which are newer ones.

I'm not sure how to check which codecs I have installed, as it doesn't ask me anymore when opening videos.  I installed 2/3 of the ones offered.  The program stopped asking after that.  I know the first one I installed was highly recommended by users, then I installed one of the other two.

Thank you for the link on installing apps, k3b and posting tips.

---

### Post by lferree on 2007-11-03
Here's a screenshot showing what the video output is like

[IMG]http://alltech-computers.net/Screenshot.png[/IMG]

---

### Post by seshomaru samma on 2007-11-04
To be honest I am not an expert on codecs because I usually install all the possible codecs after installation and rarely have any problems
please follow this guide : [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)
This site has all the information about playing different formats, it is written for ubuntu Feisty but should work the same for Ubuntu Gutsy. However, if while following the guide you are required to change or modify your sources list _**be careful,**_ adding Feisty sources to a Gutsy system will break your system,.

---

### Post by der_joachim on 2007-11-04
> **lferree said:**
> 
I am having a few problems however.  I was running World of Warcraft great in 7.04 using CrossOver.  I was also using Beryl, which apparently isn't even offered thru the Synaptic Package Manager any more.  I now get "[COLOR="Red"]World of Warcraft was unable to start up 3D acceleration.[/COLOR]"  I think this has something to do with the new Compiz.


The gaming subforum has a sticky for WoW players. Additionally, I've always understood that Compiz/Beryl/Fusion do not play nice with games.

> 
I also downloaded Wine thru the Synaptic Package Manager, Warcraft didn't like that either.


(...)

> 
I was also wondering...  Can I install software in Ubuntu that isn't available thru the Synaptic Package Manager or Add/Remove...?  I've noticed a few formats out there like RPM, .sh and pkg2.run.


There is a number of ways:
- Add more repositories. [wineHQ]("http://winehq.org/site/download-deb") has its own repository. 
- Alien is a program to convert .rpm to .deb . Be very careful though: you may miss or even break dependencies. 
- .sh files are just dumb shell scripts which merely dump a new app in a subdirectory. Nothing wrong with that, as long as you don't bother with app management. Applications installed this way don't show up in Synaptic. You must manually update/ remove them.

> 
Any suggestions for a good Nero Burning ROM alternative (...)?


KDE users really love K3B or K9copy.

---

### Post by Soarer on 2007-11-04
And you could try VLC (from the repositories) to playing videos. It seems to play anything.

---

### Post by lferree on 2007-11-04
Well, I solved the problem I was having with scrambled XVID videos.

I removed totem-gstreamer and installed totem-xine. The videos seem to play fine now.

For anyone else having this problem, do the following:
```
sudo apt-get remove totem-gstreamer
sudo apt-get install totem-xine
```

The only problem is that xine won't play my video from Samba shares. I have to copy the video to my Ubuntu PC before playback.

[B][COLOR="Red"]Totem could not play 'smb://pc-name/shared-folder/movie.avi'.
There is no input plugin to handle the location of this movie[/COLOR][/B]

If anyone knows a way around this, I'd love to hear from you, as I have a ton of video stored on a separate media server.

VLC also plays the video fine (tried this after xine).  When trying to play thru a Samba share, the player bar opens with no video window.  There is no error message, but nothing else happens.  I plan on investigating this further. After all, VLC stands for Video '**LAN**' Client. :D

---

### Post by Persianelfster on 2007-11-04
I was also using beryl in 7.04, and i upgraded to 7.10
and beryl has become obsolete in 7.10 now its compiz- fusion which comes with it on default.  to customize it further and be able to do what beryl did, need to insall compiz settings manger.  install this by typing this in terminal 

```

sudo apt-get install compizconfig-settings-manager

```

you may already have it
then when you right click on a spot on your desktop and select change desktop preferences 
OR
go to System--> Preferences --> Appearance 
select the visual effects tab there should be a custom bullet and then the preferences button, from there you can configure 3d cube rain effects etc....
hopefully this should work if it doesn't you may need to either reinstall your nvidia driver or add the 
argb visuals again, which you probably had to do to install beryl.

---

### Post by strabes on 2007-11-04
Gnomebaker is a great free not-bloated alternative to nero. For a CLI program look up cdrecord. It's great.

---

### Post by lferree on 2007-11-04
OK, so I started having problems streaming MP3 audio over Samba shares as well.

Did some digging and realized I needed to mount these shares.

Here's what I did:

Installed: smbfs, smbclient
```
sudo apt-get install smbfs
sudo apt-get install smbclient
```

Then I edited fstab.
```
sudo gedit /etc/fstab
```

Added the following lines:
```
//Win-Server/Music /mnt/music smbfs rw,username=James,password=Bond,auto,user 0 0
//Win-Server/Video /mnt/video smbfs rw,username=James,password=Bond,auto,user 0 0
```
After a while, shares stopped working and wasn't able to even browse network. I have disabled them until I can figure out the problem.

---

### Post by lferree on 2007-11-05
WoW is working again.  Come to find out, XGL was still loaded from when I was running 7.04.

```
sudo apt-get remove xserver-xgl
```

I can run in both CrossOver and Wine, but I'm still getting very low FPS and my mouse seems to be lagging.

Here's what I have in my WoW Config.wtf file:

```
SET gxApi "opengl"
SET gxWindow "1"
SET ffxDeath "0"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET shadowLevel "0"
SET alphaLevel "0"
SET trilinear "1"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET movie "0"
SET Gamma "1.300000"
SET realmName "Dragonblight"
SET readTOS "1"
SET readEULA "1"
SET SoundVolume "1"
SET MasterVolume "0.69999998807907"
SET gameTip "26"
SET AmbienceVolume "1"
SET uiScale "0.78999996185303"
SET mouseSpeed "1.25"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET profanityFilter "0"
SET guildMemberNotify "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET useUiScale "1"
SET autoSelfCast "1"
SET UnitNameNPC "1"
SET MusicVolume "0.90000003576279"
SET locale "enUS"
SET soundMaxHardwareChannels "12"
SET SoundSoftwareChannels "128"
SET expansionMovie "0"
SET timingTestError "0"
SET minimapInsideZoom "0"
SET CombatLogRangeParty "2000"
SET CombatLogRangePartyPet "2000"
SET CombatLogRangeFriendlyPlayers "2000"
SET CombatLogRangeFriendlyPlayersPets "2000"
SET CombatLogRangeHostilePlayers "2000"
SET CombatLogRangeHostilePlayersPets "2000"
SET CombatLogRangeCreature "2000"
SET scriptMemory "98304"
SET patchlist "us.version.worldofwarcraft.com"
SET showToolsUI "1"
SET EnableErrorSpeech "0"
SET weatherDensity "3"
SET cameraView "4"
SET EnableMusic "0"
SET coresDetected "2"
SET Sound_VoiceChatInputDriverName "Analog Devices AD1986A"
SET Sound_VoiceChatOutputDriverName "Analog Devices AD1986A"
SET Sound_OutputDriverName "Analog Devices AD1986A"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableErrorSpeech "0"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "1"
SET Sound_AmbienceVolume "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET readTerminationWithoutNotice "-1"
SET PushToTalkButton "MiddleButton"
SET checkAddonVersion "0"
SET Sound_ZoneMusicNoDelay "1"
SET Sound_ListenerAtCharacter "0"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxCursor "0"
SET accountName "OB1FoShoB"
SET lastCharacterIndex "1"
SET gxMaximize "1"
SET gxMultisample "1"
```

I also wanted to mention that this fixed a problem I was having with MythTV.  When I would select "Watch TV", I would get logged out of my Ubuntu session.  I could only get TV going with Tvtime.

---

### Post by Persianelfster on 2007-11-06
sharing files, you should be able to accomplish with 
System --> Administration --> Shared Folders. Add what you want to share and click the general properties tab, and name what workgroup/domain you want the files.   You may need to edit file permissions to play your mp3s,  i wish i could help you with you WoW problem, but i do not play WoW =(

---

### Post by lferree on 2007-11-09
I need to map a share from the Windows system.

---

