---
title: "Flash Sound Sync"
date: 2006-10-14
forum: General Help
---

### Post by Naralas on 2006-10-14
When i watch anything powered by flash (especially my animes on youTube) the sound seems to get behind the video. They both START at the same time but slowly sound moves out of sync. Eventually I pause and the sound continues for a few seconds to catch up with the video then I press play again. Doing this I keep myself sane, but I can still hardly just watch all 51 episodes of FMA like this :(

I did not use EasyUbuntu to install flash. I downloaded Flash for Linux from Adobe, put it into my home folder, then clicked the "install missing plugins" thingy in firefox and thats how I got flash.

(Note: before i put flash for linux into my home folder i got a "cannot find plugin, please install manually" thing which for Firefox and Flash I found verrry odd.)

Anyone know how to fix this? I can't convert my friends to Ubuntu if this type of thing plagues them.

---

### Post by catlett on 2006-10-14
Install alsa-oss and then have firefox use alsa-oss for sound 
```
sudo apt-get install alsa-oss
```
Then change the firefox file 
```
gksudo gedit /etc/firefox/firefoxrc
```
Change this line
> FIREFOX_DSP=""
To this
> FIREFOX_DSP="aoss"
Save the file and close. Then restart firefox. The problem should cease.

That came from here. [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by Naralas on 2006-10-14
I have that wiki in my favorites too. Gosh I am stupid.

Sowwy!!

---

### Post by pstewart on 2006-10-15
I'm having this problem too.

I've installed alsa-oss, but I'm using Swiftfox and can't find the equivilant of the firefoxrc file.

Anyone know where it is?

---

### Post by Hemmer on 2006-11-06
Try installing Flash 9 (beta) - they have fixed the sync problems finally. :D

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

