---
title: "[SOLVED] No embedded website sound (youtube, flash)"
date: 2008-02-28
forum: General Help
---

### Post by iheartubuntu on 2008-02-28
I started a thread [here]("http://ubuntuforums.org/showthread.php?t=708405") with no luck. If I may, I would like to try this thread. Thanks....

I was having [problems with my sound card]("http://ubuntuforums.org/showthread.php?t=564972"), so I decided to swap in an older sound card which works fine now, although I dont get sound in any embedded video in websites like youtube, msnbc, etc. I tried the "MediaPlayerConnectivity" add-on to control video/sound through VLC but that didnt help.

Do I have to somehow re-install some sound files? I have Flash 9 and the video works, but no sound.

I have sound working everywhere else.

Ive checked and tried several "no youtube sound" threads with no help. I did come across one "how-to" on purging flash (or something like that) and it sounded promising, but I cant find the thread now

Any tips? Thanks!

---

### Post by iheartubuntu on 2008-02-29
Is there any way I can re-install all sound drivers? Maybe this would help. I dont know what to do now :|

Thanks for any advice.

---

### Post by iheartubuntu on 2008-03-01
* BUMP *

This is one of the few problems I have left, and its on my main work system. Can anyone please offer some guidance? Im not quite sure how to fix the sound in streaming flash videos. I get sound everywhere else. I originally had this problem with a different soundcard on this computer (most sound didnt work then) so I swapped in an older PCI sound card and almost everything works, minus the streaming video sound like youtube and MSNBC (basically anything thats embedded flash). I do get embedded WMV videos to play with sound, so Im guessing this is a flash problem. Ive tried uninstalling flash and re-installing, tried gnash, and no luck.

I have a feeling that if I re-install Ubuntu on this system with my older soundcard I have in now, all will work great, but, Ive already go so much installed and working great now on this system, it seems like a re-install is a bit much to solve this prob. Any tips?

---

### Post by CanonKen on 2008-03-01
I had a problem with youtube sound, sound worked in all other applications but not youtube etc when played through Firefox, i had built in sound on my motherboard, put a sound card in and it solved the problem - don't ask why, I've no idea

---

### Post by iheartubuntu on 2008-03-01
Unfortunately, I have no idea either :) I swapped in an older sound card and got almost all my sound working now, but cant figure out getting sound to work in flash like on youtube. Ive researched and tried all the suggestions in the "no sound in youtube" threads, but no luck.

---

### Post by wh33t on 2008-03-01
Odd, I would have to say it's a firefox problem most likely. Can you get sounds from embedded wav files etc? or it just swf audio you can't get to work? and can you get swf video to work?

---

### Post by iheartubuntu on 2008-03-01
> **wh33t said:**
> Odd, I would have to say it's a firefox problem most likely. Can you get sounds from embedded wav files etc? or it just swf audio you can't get to work? and can you get swf video to work?

I do get embedded WAV and I do get the youtube video, just no sound. Im also getting other embedded video, like WMV... seems like this is more or less a Flash prob, but cant seem to pinpoint it. Ive tried Gnash, and uninstalling, then installing flash too.

---

### Post by Sixdown on 2008-03-02
I have the exact same problem.  I am able to get sound from anywhere but firefox.  The video works perfectly, yet there is no sound coming from flash.

Any ideas?

---

### Post by iheartubuntu on 2008-03-03
I thought I would update this a bit...

I was  trying to figure out a way to watch the show LOST from the ABC website, but their new LOST episode player doesnt work in linux. It says I need XP or Mac. Well, checking the threads here, I found a work around which was to install XP Firefox through Wine and then I am able to watch LOST episodes, no problem. This works.

So, I tried to watch youtube videos in my Wine Firefox, and guess what? I can hear the sound there no problem.

So, this seems to be a linux Firefox problem I am having. Can anyone recommend any settings or changes I can do in Firefox to get my sound working in youtube??

Thanks!

---

### Post by ubuntu-freak on 2008-03-03
I'm surprised you haven't received much help on this. 

Try tip no.7 in the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=661833), the second paragraph after the purge command. That should fix it. I recommend you do part 1 of my how-to also, it will skip anything you already have.
 
Nathan

---

### Post by iheartubuntu on 2008-03-03
> **reassuringlyoffensive said:**
> I'm surprised you haven't received much help on this. 

Try tip no.7 in the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=661833), the second paragraph after the purge command. That should fix it. I recommend you do part 1 of my how-to also, it will skip anything you already have.
 
Nathan

Nathan, thanks. Ive come across your howto already and have tried this but it didnt work. So, I tried it all over again right now and rebooted and it still didnt help.

I get sound everywhere but Firefox Flash videos. I even get sound in embedded WMV files not a prob. This may not be all Firefoxes problem. Could be Flash too.

This wouldnt be such a big deal for me, but I make youtube videos from time to time for my biz. so it would be great to get this working and teach myself the software to make the videos over here in Ubuntu instead of XP.

I have Ubuntu on 4 or 5 other computers now and dont have this problem as I do on my main work system.This might have something to do with my original sound card didnt work, so I swapped it out for an older one. Which plays all sounds now except this youtube videos (or any flash videos).

---

### Post by ubuntu-freak on 2008-03-03
Did any older version of flash work? That's so odd, the fix has worked for many, many users. 
 
Nathan

---

### Post by iheartubuntu on 2008-03-03
> **reassuringlyoffensive said:**
> Did any older version of flash work? That's so odd, the fix has worked for many, many users. 
 
Nathan

No. I originally had a Audigy sound card and could never get it configured to work with Ubuntu... no sound anywhere no matter what I tried. I then found an older PCI sound card, plugged it in and Im getting all sound now, just not the youtube sound.

I wonder if uninstalling Firefox and re-installing might help? Same with Flash?

---

### Post by ubuntu-freak on 2008-03-05
> **shirteesdotnet said:**
> No. I originally had a Audigy sound card and could never get it configured to work with Ubuntu... no sound anywhere no matter what I tried. I then found an older PCI sound card, plugged it in and Im getting all sound now, just not the youtube sound.

I wonder if uninstalling Firefox and re-installing might help? Same with Flash?

 
You could try that. Do a complete removal in Synaptic. Did you try any wikis? Try searching "no sound flash firefox wiki ubuntu" in Google.
 
Nathan

---

### Post by paulphillips on 2008-04-02
All I did was to remove ".asoundrc" and ".asoundrc.asoundconf" files from my home directory.  Fixed the sound problems immediately.

---

### Post by iheartubuntu on 2008-04-03
> **paulphillips said:**
> All I did was to remove ".asoundrc" and ".asoundrc.asoundconf" files from my home directory.  Fixed the sound problems immediately.

This solves the no sound in youtube problem? Where do I find .asoundrc?

---

### Post by ubuntu-freak on 2008-04-03
> **shirteesdotnet said:**
> This solves the no sound in youtube problem? Where do I find .asoundrc?

 
Open your home folder, then go to "View" in the file browser, then select to show hidden files.
 
Nathan

---

### Post by iheartubuntu on 2008-04-03
> **reassuringlyoffensive said:**
> Open your home folder, then go to "View" in the file browser, then select to show hidden files.
 
Nathan

I guess this wouldnt apply to me since they arent in my home folder then.

---

### Post by ubuntu-freak on 2008-04-03
> **shirteesdotnet said:**
> I guess this wouldnt apply to me since they arent in my home folder then.


You don't have a hidden folder called asoundrc? 
 

Nathan

---

### Post by ubuntu-freak on 2008-04-03
Actually, create a new user in System>Aministration, login as that user and see if sound in flash works. If it does, transfer your personal files to the new account and delete the old account, then you can rename the new account.
 
Nathan

---

### Post by iheartubuntu on 2008-05-22
Nathan, Thank you so much for all your help with this. I finally backed up all my data (500GB) and did a fresh install of Ubuntu 8.04, still was without sound in Youtube so I ran your fix and it works great now! I have flash sound! Woohoo!!! Thank you so much.

---

### Post by lusepuster on 2008-05-22
A somewhat less radical solution was for me to simply reset my Firefox settings but keep my bookmarks etc. by the following steps:
[LIST]
[*]Quit Firefox
[*]rename the folder .mozilla to something else, e.g. .mozilla-old
[*]Restart Firefox
[*]open the newly generated .mozilla in a new window
[*]go to the "firefox" folder in both folders
[*]In the .mozilla-old folder, there's a folder called [something].default. An identical folder plus another, named [something-else].default, are in .mozilla. Copy (Shift-drag) the content of [something].default in .mozilla-old into [something-else].default in .mozilla, and clock 'overwrite' when prompted.
[/LIST]

This did the trick for me, anyway. If it fails, you can just remove .mozilla and rename .mozilla-old back to .mozilla, and your settings will be back to what they were.

---

