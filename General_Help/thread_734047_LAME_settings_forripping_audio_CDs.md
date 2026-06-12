---
title: "LAME settings forripping audio CDs"
date: 2008-03-24
forum: General Help
---

### Post by andrewk8 on 2008-03-24
I am trying to set up CD ripping to MP3 through Sound Juicer in Ubuntu 7.10.  I've installed the ubuntu-restricted-extras to add MP3 support.  I've configured Sound Juicer to output in CD Quality MP3.  I'm trying to change the LAME settings of the "CD Quality MP3" profile.  I opened a terminal window to get help on LAME configuration and got this:
[INDENT]xxx-desktop:~$ lame --help
The program 'lame' is currently not installed.  You can install it by typing:
sudo apt-get install lame
bash: lame: command not found[/INDENT]
I checked the Synaptic Package Manager in Multimedia (multiverse), it says that lame isn't installed.  If I do a search in Synaptic for "lame", it shows that "ubuntu-restricted-extras" and "liblame0" are installed.

So I've got a couple of questions:

[LIST=1]
[*]Is the LAME content in the "ubuntu-restricted-extras" just the codec and not the full version of LAME?
[*]If I install the full version of LAME from multiverse, does this somehow disable / replace the LAME that was included in the "ubuntu-restricted-extras"?
[*]Do I need to configure Sound Juicer differently to use the full version of LAME instead of the "extras" version?
[*]What benefits do I have of installing the full version of LAME vs. leaving things just the way they are?
[*]Is there any reason I shouldn't install the full version of LAME?  (Please, no lectures on closed / proprietary formats.  I need MP3 because of my iPod.)
[/LIST]
Thanks.

---

### Post by stchman on 2008-03-24
> **andrewk8 said:**
> I am trying to set up CD ripping to MP3 through Sound Juicer in Ubuntu 7.10.  I've installed the ubuntu-restricted-extras to add MP3 support.  I've configured Sound Juicer to output in CD Quality MP3.  I'm trying to change the LAME settings of the "CD Quality MP3" profile.  I opened a terminal window to get help on LAME configuration and got this:
[INDENT]xxx-desktop:~$ lame --help
The program 'lame' is currently not installed.  You can install it by typing:
sudo apt-get install lame
bash: lame: command not found[/INDENT]
I checked the Synaptic Package Manager in Multimedia (multiverse), it says that lame isn't installed.  If I do a search in Synaptic for "lame", it shows that "ubuntu-restricted-extras" and "liblame0" are installed.

So I've got a couple of questions:

[LIST=1]
[*]Is the LAME content in the "ubuntu-restricted-extras" just the codec and not the full version of LAME?
[*]If I install the full version of LAME from multiverse, does this somehow disable / replace the LAME that was included in the "ubuntu-restricted-extras"?
[*]Do I need to configure Sound Juicer differently to use the full version of LAME instead of the "extras" version?
[*]What benefits do I have of installing the full version of LAME vs. leaving things just the way they are?
[*]Is there any reason I shouldn't install the full version of LAME?  (Please, no lectures on closed / proprietary formats.  I need MP3 because of my iPod.)
[/LIST]
Thanks.

I prefer the MP3 format.  Most every device accepts them.  I also need then as my car stereo will only recognize .mp3 and .wma audio files.  I will warn you that some devices may have problems with VBR mp3s and LAME is a VBR encoder.

I cannot personally tell a difference between .ogg and .mp3 so it is a non factor.

I have a tutorial that will get you ripping VBR MP3s.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by andrewk8 on 2008-03-25
I was looking for a more technical answer on Ubuntu's inner workings w.r.t. packages & package conflicts.  "Expert" Windows user, but 1st Linux experience.  The response is appreciated, but didn't answer any of the original questions I had.  I'd like to get answers to these specific questions, so I can begin to understand Linux.

Thanks.

---

### Post by shirilover on 2008-03-25
> **andrewk8 said:**
> I
So I've got a couple of questions:

[LIST=1]
[*]Is the LAME content in the "ubuntu-restricted-extras" just the codec and not the full version of LAME?
[*]If I install the full version of LAME from multiverse, does this somehow disable / replace the LAME that was included in the "ubuntu-restricted-extras"?
[*]Do I need to configure Sound Juicer differently to use the full version of LAME instead of the "extras" version?
[*]What benefits do I have of installing the full version of LAME vs. leaving things just the way they are?
[*]Is there any reason I shouldn't install the full version of LAME?  (Please, no lectures on closed / proprietary formats.  I need MP3 because of my iPod.)
[/LIST]
Thanks.

1. I believe that to be the case.
2. No, the lame package should just install the lame executable and related files.
3. AFAIK, sound juicer does not use lame to encode audio. It uses the gstreamer backend, which fails miserably at creating decent audio. I prefer using Grip/LAME instead.
4. The benefit of installing the lame package is that it allows you more control of the output audio file.
5. I don't see any reason why you shouldn't, it only takes up a small amount of drive space.

---

### Post by Zimmer on 2008-03-25
Grip for what you want. As for LAME and MP3 have a look at these links , Audacity can help you in many ways...
[http://audacityteam.org/wiki/index.php?title=MP3](http://audacityteam.org/wiki/index.php?title=MP3)
[http://audacityteam.org/wiki/index.php?title=Lame_Installation](http://audacityteam.org/wiki/index.php?title=Lame_Installation)

---

