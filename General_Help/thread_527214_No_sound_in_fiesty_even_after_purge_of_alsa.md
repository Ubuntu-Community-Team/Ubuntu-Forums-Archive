---
title: "No sound in fiesty even after purge of alsa"
date: 2007-08-16
forum: General Help
---

### Post by speirint on 2007-08-16
I upgraded from edgy (where sound and everything was working fine) to feisty and I've been fighting with my distro ever since.  My computer is a somewhat high-tech Frankenstein, as such, I don't really know what it's got other than an integrated intel motherboard and pentium D.  Soundcards are recognized though.  

ian@primo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ian@primo:~$ 



Anything selected under alsa won't work, I'll certainly get the audiotestsrc wave=sine freq error.
I've been able to get the oss sound to work sporadically and briefly once in a while, during sound tests, I'll either get the errors:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

Or something else that says something along the line of resource may be busy

Right now, I can see the testing button for oss when I click it under sound preferences, but I hear no sound.  All sound is not muted (checked alsa in terminal and double clicked speaker icon by clock).

My sound will work temporarily once in a while-it sometimes won't work at all from the gdm all the way through.  Rebooting doesn't change much either.  I've looked through at least eight threads (including the one ultimate sound resource guide that has a detailed update history and directions for purging alsa) and the most common problems seem mentioning an error in the alsa or kernal* (I'm an absolute beginner) that require the user to either purge and reinstall alsa, or kill a specific line of code.  I've also posted responses in a couple (as a matter of fact, the bulk of my bean count comes from sound error responses)  I've tried purging already to no avail, and my understanding of terminal is not yet enough to try killing the suggested lines of code (putting kill in front of /usr/... doesn't work)-I'll post them here in a little bit so that someone may be able to give it a shot in explaining to me what I should try to do.

Also, I'm not sure if this is a separate problem altogether or if it could be another symptom, if I try to run more than one media program or run rhythmbox and have something like youtube with sound up at the same time, the sound stops too.

Any suggestions if what I've been trying doesn't seem like the right way to go about fixing it?

It's been annoying me very much for a while since I'm taking a class that has online homework that requires sound.

Here are some similar posts by other people that look like they have similar problems:
2 sound cards, alsa, sound, gnome, ubuntu, problems.  	Kallewoof  	General Help  	9  	December 4th, 2006 04:56 AM

Ubuntu sees Sound Card, no sound.... (ALSA)  	khyberkitsune  	Multimedia & Video  	1  	October 20th, 2005 07:04 PM

I'll be editing this post later for more details.

---

### Post by ddrichardson on 2007-08-16
> **speirint said:**
> Also, I'm not sure if this is a separate problem altogether or if it could be another symptom, if I try to run more than one media program or run rhythmbox and have something like youtube with sound up at the same time, the sound stops too.

OSS only supports one device access at a time - one tof the main reasons we moved towards ALSA.

What steps have you tried and what version of ALSA - the C-Media cards are very well supported. Not having looked through these posts I'm assuming they said to recompile ALSA and to alter alsa-base.

---

### Post by yowshi on 2007-08-17
it seems whatever ubuntu uses by default cant handle motre then  one device accerssing the sound drivers at a time.

i am useing fiesty amd64 and any time firefox actually manages to access the sound drivers i have to use the system monitor to shut it down (so i can restart with all my pages up again) so i can listen to music on xmms. i hate amarok cant seem to get it to play mp3's

---

### Post by speirint on 2007-08-18
Thanks for your prompt replies.  This is about as detailed as I can get for now:

This was what used to work for me, but the sound would work only about 30% of the time, and now (possibly since I'm also running off of an older kernal) doesn't work at all though the test sound doesn't always show an error:
> **devapea said:**
> Ok I may have a tiny kernal of help for you guys.  Ive had the same problem with the same error messege when I tried playing dvds in totem.  A setting that you should look at is in system>preferences> sound.  I changed my music and movies sound  playback from Alsa to the older OSS.  try it and press the test button and see if ya hear a test  sound. I get one with OSS but not with Alsa.  good luck

Names of available sound cards:CMI8738MC6, ICH5

I've also tried something else I read in the forums which resulted in this:
> kill /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
bash: kill: /usr/bin/esd: arguments must be process or job IDsbash: kill: -terminate: arguments must be process or job IDsbash: kill: -nobeeps: arguments must be process or job IDsbash: kill: -as: arguments must be process or job IDsbash: kill: (1) - Operation not permittedbash: kill: -spawnfd: arguments must be process or job IDsbash: kill: (24) - No such process



Here are some more things I tried, but I don't have the capacity yet to actually input into terminal correctly.  This was another suggestion on the forums, and I don't recall what the result was when I hit enter for each part:
> 
/etc/asouund.conf
rename asouund.conf


Here's a description of some of the errors I'd get in the preferences sound tests:
> **speirint said:**
> Alright, last night I was running the rythmbox media player and sound worked fine (albeit quieter than before when I used the ALSA) as well as in streaming internet (youtube, etc.) audio.  Suddenly, the songs (all of my audio files, I tried several other songs saved in different places, tried playing them individually through the places menu, even in different media players and I'd still get no sound) would no longer be playable, I'd get this pop up message:

Couldn't Stop Sound Playback
unknown playback error

Checking the sound settings in the system, everything was still set to the OSS players, which as I posted before did give me sound during the tests and made everything work out honky dory.  Now when I test them I get this:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.  

Was Bob Dylan's nasal voice too much for my computer?  What's going on now?

So in recap, I've got issues with media and sound (no sound) on the computer unless I play something from streaming media off of the internet.  Is this still the same problem as well?


Edit:7/24/07
The test sounds work again, as well as the normal rythmbox stuff now.  Strange indeed.

Edit:7/26/07
Test sounds do not work now.  Back to saying 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.


Very recently, I purged alsa mixer and then re-installed it, the version is v1.0.13 , nothing is muted, volumes are on decent levels.
> 
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils


Finally, the most recent event (as of this morning) was this-I'm not sure if this is a bigger problem than just sound, but if you go to the original topic (titled what happened to my x-server!?) there's a fair description of what happened to someone else's computer as well as mine.  I believe it may explain why my sound doesn't work too since it mentions the Alsa sequencer:
 > **kramer65 said:**
> thanks for the tips. I have a slight problem though. I never get to any command line. It just says:

Timidity is not yet configured
Enable alsa sequencer first by editing /etc/default/timidity.

And then only black. I can type something, but it doesn't do anything when hitting enter, only showing another black line.

Any ideas..?
> **speirint said:**
> I just now got the same problem when I was trying to restart my computer to select a different kernal after already being taken to the gdm.  I however, have been using this computer under ubuntu consistently for quite some time now (several months).

  Try running ubuntu off of a different (older) kernal until we figure it out.  I'm completely new to ubuntu, so I'm still trying to figure out how to edit anything with /etc ...

Here's what I got:
A list of things are being checked-the last two lines say:
Checking battery        [OK]
Running local boot scripts (/etc/rc.local)           [OK]
Timidity is not yet configured.            [OK]
Enable Alsa Sequencer first by editing /etc/default/timidity.

By the way, have you been having any problems with sound on your system?  I've been trying to get alsa to work for a while and having seen this makes me think that it may have something to do with why I'm hearing sound sporadically if at all.  Also, I'm using fiesty fawn, is that what you're using as well?

---

### Post by yowshi on 2007-08-19
ok you lost me---adnd then i find myself.hehehe

---

### Post by speirint on 2007-09-29
Can someone please help or move this to absolute beginner talk?  I've had no sound for several months (close to five now).  I'm tired of having to reboot to use Windows every time I need to use the sound.

---

### Post by yowshi on 2007-09-29
kuse the alsa sound stuff instead of the OSS stuff

---

### Post by Elderlygent on 2007-10-01
> **yowshi said:**
> kuse the alsa sound stuff instead of the OSS stuff

You have my deepest sympathies. My sound quit a couple of days ago, I think after I had installed an update, but anyway it just quit. I posted a query and got a very patronising reply suggesting I should find out if I have a sound card and whether my sound was switched on etc. etc. Newish to Ubuntu I may be but I am still able to do a few basic things myself!!!!!!!!!!!!!!!!

---

### Post by yowshi on 2007-10-02
i wasnt trying to be patronizing. i mysel;f am rather new but from what i have seen and what my friend who isnt new to linux has told me alsa seems to be superior to oss. but when i installed ubuntu oss seemed slightly defaulted to.

---

### Post by speirint on 2007-11-14
For those of us still trying to figure out the sound, I believe I found another thread that discusses a simillarly described issue with sound. There is a suggested solution there as well.

Go here:[http://ubuntuforums.org/showthread.php?t=462857]("http://ubuntuforums.org/showthread.php?t=462857")

Thanks Elderlygent and yowshi, if you're still having sound problems I'll see you guys there.

---

