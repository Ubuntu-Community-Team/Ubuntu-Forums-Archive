---
title: "problems after gutsy/7.10 upgrade"
date: 2007-11-01
forum: General Help
---

### Post by nex9 on 2007-11-01
Hello All -

I recently upgraded my Feisty install to Gutsy / 7.10. The upgrade has screwed up sound on my box - it doesn't recognize my sound card at all, apparently. I think I'm running into bugs 157730, 130559, and/or 144882. Anyway, I was able to get sound working again by reverting back to the old 2.6.20-16-generic kernel. Unfortunately during the process I screwed up my nvidia display drivers, and despite trying several things, I can't get resolutions higher than 1024x768. 

So at this point I need some advice. I'm thinking of doing a fresh install on Feisty, at least until the sound issues are fixed. To complicate things though, I'm running dual boot with windows XP. Is there anything I need to be aware of (so that I don't screw up my XP install) when I re-install? 

Thanks in advance.

---

### Post by Crafty Kisses on 2007-11-01
You might want to post the following output:
```
lspci
```

---

### Post by Pumalite on 2007-11-01
When you erase Ubuntu, you'll end up without MBR. But upon reinstall you'll have a brand new Grub that'll give you again dual boot.
If you want to try to fox your Gutsy; here are a few links and tips that might serve you:
sudo apt-get install linux-backports-modules-generic (possible solution, not sure)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you

After fiddling with the sound settings trying various suggestions in the Comprehensive Sound Problem Solutions Guide thread, I totally buggered up my sound. Oh well, a fresh install of Feisty never hurt anyone and I had my /home directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of .config file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a .asoundrc file and another similarly named file. After doing some research here about what the file is for (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

---

### Post by nex9 on 2007-11-01
Thanks Codename & Pumalite:

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Doing a search here on the forums for "82801H", I turned up this,:

[http://ubuntuforums.org/showthread.php?t=594287&highlight=82801](http://ubuntuforums.org/showthread.php?t=594287&highlight=82801)

I have to agree with that poster's comments that it's very frustrating that this was removed from the kernel - this seems to be a very common sound chip!

seems very promising - I probably won't have time to try it out for a few days, but hopefully that'll do the trick.

---

