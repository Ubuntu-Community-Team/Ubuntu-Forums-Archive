---
title: "Command line ripping to ISO"
date: 2007-07-23
forum: General Help
---

### Post by 56seeker on 2007-07-23
Hello all;

Can any one walk me through the process of ripping a DVD to ISO and burning it to DVD *via command line tools*?

I'm well aware that there's a wealth of free tools available in a standard Ubuntu desktop; but firstly I'm working on a server system without any form of GUI; and secondly I'd like to learn techniques that are applicable on any 'nix installation.

So... for argument's sake; how exactly would I rip the Ubuntu CD to iso, and then, burn that generated iso to disk?

---

### Post by Svictor on 2007-07-23
What do you mean by "ripping": simply copying or converting to some other format? In the first case, this is what I would try (just a guess, since I can't try it right now):
You mount the dvd as usual, say in /mnt/my-dvd. So you should see two folders in /mnt/my-dvd: AUDIO_TS and VIDEO_TS.
Then you
```
mkisofs -dvd-video -o /I/want/my/iso/here.iso /mnt/my-dvd
```the -dvd-video option is important to get DVD-video compliant udf filesystem for your iso. 
Then, once you have your .iso file:
```
growisofs -dvd-compat -Z /dev/dvd=your.iso
```/dev/dvd must point to your dvd device. I am not quite sure what the -Z option stands for (but the man pages say it should be there). 

I used these commands some time ago, to do more or less the same thing... Although not quite. Hope it works for you too.

---

### Post by 56seeker on 2007-07-23
Thanks for the quick reply!

By ripping I mean making an exact copy.

Some background:

I'm making a dedicated Ubuntu server to host VMware server as it's only application and the virtual machines that VMware server supports.

Virtual machines can be installed from an iso image of the instalation media; they don't need a physical disk.

So I want to convert my Windows CD's; my SQL CD's, my Ubuntu CD's etc to iso.

But then knowing how life goes it'd be sensible to know how to burn the iso's to disk again.

Making the iso went just fine with your help; but I got this error trying to burn the iso:

[PHP]seeker@fd-portable:~$ growisofs -dvd-compat -Z /cdrom=il-2.iso 
:-( unable to open64("/cdrom",O_RDWR): Is a directory
[/PHP]

---

### Post by Svictor on 2007-07-23
Ok, so it is not a video DVD you are copying. I thought of that because of the word "ripping", which I'm used to reading in such contexts... Never mind: the process is more or less the same, but you don't need the -dvd-video option for mkisofs, neither -dvd-compat for growisofs .

I think you should have a look at the man page of growisofs. There are some examples there. I don't know which ones suit best your needs. You may be able to burn several CD iso-s on one DVD with a ```
growisofs -Z /dev/dvd -R -J /some/files.iso 
```.

Anyway, regarding the error, you should try and use something like /dev/dvd/ for the device. /cdrom is probably your usual mountpoint for DVDs but your media isn't (yet) one.

If /dev/dvd/ doesn't work neither, find out the name of your device: insert a proper DVD, mount it, then issue a ```
df
``` It will tell you which /dev/etc. is mounted and where.

---

