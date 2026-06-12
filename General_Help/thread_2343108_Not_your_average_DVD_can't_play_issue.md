---
title: "Not your average DVD can't play issue"
date: 2016-11-13
forum: General Help
---

### Post by goemonburo on 2016-11-13
Running a fairly fresh install of Ubuntu 16.04.1 LTS, updated.  Xenial.  I've run many flavors of Linux and have always preferred Ubuntu's ease of use of things like DVD playback.

For whatever reason, I have been completely unable to get DVDs to play.

I have tried installing libdvdcss, tried the 32 bit versus 64 bit version of VLC, tried for several weeks (not solidly, but off and on) to track down threads that might solve this.  

VLC gives a consistent error that the DVD may be encrypted.  This seems to be the case because I can play other DVDs and older, non-encrypted ones.

I've tried installing extras, I've tried installing aptitude and using that rather than apt-get.  

It seems like this should be far simpler than it is.  Anyone out there know what steps I need to take to get this working again?  

Ideally this would be via command line, but at this point, I'll try GUI solutions too.

Thank you!

---

### Post by T.J. on 2016-11-14
> **goemonburo said:**
> 
For whatever reason, I have been completely unable to get DVDs to play.

I have tried installing libdvdcss, tried the 32 bit versus 64 bit version of VLC, tried for several weeks (not solidly, but off and on) to track down threads that might solve this.  

VLC gives a consistent error that the DVD may be encrypted.  This seems to be the case because I can play other DVDs and older, non-encrypted ones.

Thank you!

I'm sorry, but as far as I know, no one on the forums is allowed to help you with this.  The terms of the board prevent it.

---

### Post by wildmanne39 on 2016-11-14
Please do:
```
sudo apt-get install libdvd-pkg
```
Then
```
sudo dpkg-reconfigure libdvd-pkg
```
after you have removed all other codecs you have installed that did not work.

---

### Post by goemonburo on 2016-11-15
@Wild Man, thank you, this gives me some hope.  Can you possibly suggest what steps to take to identify the other codecs?  For instance, is there a way to list all the codecs that have been installed in the past 3 weeks?  I assume "sudo apt-get remove _____" will get them gone, but I don't remember the various things I've tried.  I suppose the .bash_history might have some.

Thank you again.

---

### Post by T.J. on 2016-11-16
If you can play unencrypted DVDs normally, but not commercial ones, it is because you are probably lacking an up-to-date CSS decoder.  As I mentioned before, I cannot help you with that.  In some jurisdictions, it might be illegal, as most Linux CSS decoders are unlicensed.

I do not know if it is still offered, but Canonical and Fluendo used to sell a licensed DVD player.  You might check with them.

---

### Post by mc4man on 2016-11-16
> **goemonburo said:**
> @Wild Man, thank you, this gives me some hope.  Can you possibly suggest what steps to take to identify the other codecs?  For instance, is there a way to list all the codecs that have been installed in the past 3 weeks?  I assume "sudo apt-get remove _____" will get them gone, but I don't remember the various things I've tried.  I suppose the .bash_history might have some.

Thank you again.
There are no other codecs involved that would be relevant & vlc installs anything else needed like libdvdread, ect. 
css encrypting has not changed in many years nor will it ever change going forward.

There is an outside chance you have some structure protected titles where the protection is also interfering with playback though those are fairly rare. (structure protection is used to prevent copying, not playback
In those cases you could attempt just playback of the main title, in vlc that would be Media > Open disc > enable the 'No disc menus' option, see screen.
(- In extremely rare cases even that doesn't work, one would have to determine the correct title number & use that. 

If still issue do some libdvdcss debugging, described here, make sure to delete ~/.dvdcss folder 1st.
[https://ubuntuforums.org/showthread.php?t=1440147&p=9037249&viewfull=1#post9037249](https://ubuntuforums.org/showthread.php?t=1440147&p=9037249&viewfull=1#post9037249)

---

### Post by goemonburo on 2016-11-18
So I just did the two libdvd-pkg steps above, still getting this error:

Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

I'm running a regular DVD, one that I own, a Ghibli anime that my 6 year old is dying to watch.  We don't have a DVD player.  

Oddly, the cd-rom drive makes a lot of weird scraping sounds.  But it will play other things.  I don't think it's the drive or the disc...

---

### Post by Autodave on 2016-11-19
I am probably no help here, but since nothing else has worked, make sure that libdvdread4 is installed.

---

