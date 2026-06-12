---
title: "Audio doesn't work"
date: 2007-12-02
forum: General Help
---

### Post by Untame_Zerg on 2007-12-02
I cant seem to get my speakers to work at all. I have Philips speakers and a sub. I have to plug them into the headphone jack in the front of the computer because my main out jack from the Motherboard is fried. I am just wondering how I can get an audio driver? I want my speakers working ](*,)

If it helps, I have a Foxxconn motherboard, but I'm not sure what model it is...

---

### Post by Untame_Zerg on 2007-12-02
Anyone? Anyone? Bueller? Bueller? This is driving me crazy!

---

### Post by matthewcraig on 2007-12-02
It's fried?  Doesn't sound good for your chances getting it working.

---

### Post by Untame_Zerg on 2007-12-02
Audio works fine through the headphone jack in Windows XP... Ubuntu just doesnt work with audio for me...

---

### Post by Untame_Zerg on 2007-12-03
Bumpage. The problem still persists.

---

### Post by ferdostar on 2007-12-03
Please post the output of 
```
sudo lshw -C sound
```

---

### Post by Untame_Zerg on 2007-12-03
```

sudo lshw -C sound
Password:
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: IXP SB400 AC'97 Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.5
       bus info: pci@00:14.5
       version: 80
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=64 mingnt=2
       resources: iomemory:fdff8000-fdff80ff irq:21

```
That?

---

### Post by ferdostar on 2007-12-03
Yes, 
Could you please chek alsamixer in terminal if everything is ok
```
alsamixer
```

---

### Post by Untame_Zerg on 2007-12-03
```
alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```
Uhh........ What the--

---

### Post by ferdostar on 2007-12-03
Hmm, ok
Try this
```
sudo apt-get install linux-backports-modules-generic
```

And after that try the alsamixer

---

### Post by Untame_Zerg on 2007-12-03
```

.....................

The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic but it is not installable
E: Broken packages

```
No workie... aslamixer gets me the same result as last time.

---

### Post by ferdostar on 2007-12-03
Can you look at the System > Preferences > Sound what is your device selected?

---

### Post by Untame_Zerg on 2007-12-03
Its all on ALSA...

---

### Post by ferdostar on 2007-12-03
It's a little bit strange, maybe alsamixer is not suported by your sound card :confused:
Can you try ```
asoundconf list
``` to see the names of avaible sound cards

---

### Post by Untame_Zerg on 2007-12-03
Nothng is listed... So does that mean I can't use audio until I get a supported card?

---

### Post by ferdostar on 2007-12-03
Maybe :)
In fact you can try to compiling the alsa-driver for your sound card [http://www.alsa-project.org](http://www.alsa-project.org) 
Otherwise you can take a look of others similar posts to see if someone else had the same problem as you:
[http://ubuntuforums.org/showthread.php?t=616846](http://ubuntuforums.org/showthread.php?t=616846)
[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.p...light=no+sound](http://ubuntuforums.org/showthread.p...light=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php...21&postcount=5](http://ubuntuforums.org/showpost.php...21&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.p...olutions+guide](http://ubuntuforums.org/showthread.p...olutions+guide)
[https://help.ubuntu.com/community/De...gSoundProblems](https://help.ubuntu.com/community/De...gSoundProblems)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/200...work-in-gutsy/](http://linuxtechie.wordpress.com/200...work-in-gutsy/)
[http://linuxtechie.wordpress.com/200...tsy/#comment-6](http://linuxtechie.wordpress.com/200...tsy/#comment-6)
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469](https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469)

On the other hand you can try to 
1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above. :)

Finally if nothing works and everything fails.....use a hammer :)

---

