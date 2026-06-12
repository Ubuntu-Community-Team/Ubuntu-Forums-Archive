---
title: "FL Studio"
date: 2006-12-20
forum: General Help
---

### Post by xenoalien on 2006-12-20
I downloaded FL Studio for windows and installed it. Wine seemed to emulate it very well. But had some direct sound and video problems. Could someone check this out and see what I would need to emulate this awesome program better. Thank You!

---

### Post by majoridiot on 2006-12-20
i've got FL studio on my list of things to get working.  i'll post any progress at it occurs.

---

### Post by holdinout on 2006-12-20
Either way, it could come down to Wine simply not supporting a certain function yet.

---

### Post by xenoalien on 2006-12-20
If anyone can get FL studio to work well on Ubuntu I will no longer use windows :D yay!

---

### Post by xenoalien on 2006-12-22
If anyone knows anything new about FL studio and Ubuntu post it.

By the way, the error I get when starting FL studio says:

"Couldn't create the DirectSound main object"

Does wine not emulate windows DirectSound? 
Anyone know how to fix this?
Thanks

---

### Post by majoridiot on 2006-12-22
FL studio under wine is the weekend project if all goes as planned.  we'll see if we can't get it
running.  what a great program.  the only thing i miss about windows, really.

---

### Post by majoridiot on 2006-12-22
ok... got a little underway this afternoon installing FL studio 5.02 (the only one i have handy)
with wine 0.9.27 on dapper.  working only in demo mode, as geting right into it was more
important than figuring out how to copy my registration keys to the registry correctly.

i got it installed with no problem and messed around with config a little.  i was able to get
sound out from the one (handclap) sample that would load with the default loop.  trying to
load a .flp file crashed wine and i could not get samples to load into the sequencer.

i found out after i upgraded wine (which started this process) that winehq recommends a
complete uninstall beforehand- which i did not do, so this might be the cause of some of the
errors.  i need a fresh wine install from scratch to tell for sure.  in the meantime:

i started out by copying the .dll files from /windows/system and /windows/system32 on
my XP partition to the corresponding folders in wine's c drive.  there are 4 .dll files you do
**NOT** want to copy over, as wine will choke.  the four not to copy are in /windows/system32
and are:

kernel32.dll
gdi32.dll
user32.dll
ntdll.dll

i hoped to avoid a LOT of .dll problems by moving all of these M$ .dlls over at the beginning,
as wine will go looking for them if needed.

next, i config'd ALSA as the the sound driver with full hardware accel.  wine nagged a LOT about
sound issues, but stopped (for the most part) when i installed the following (some were already
installed, but i did it to make sure i had the lastest):

```
sudo apt-get install libartsc0 libesd-alsa0 libjack libaudiofile0
```

after that, wine errored with "open /dev/snd/seq failed" or something similar, which i fixed with:

```
sudo modprobe snd-seq
```

and by adding snd-seq to /etc/modules.

FLS seemed to run best as an XP app and ALSA was best on my box, (OSS would marginally function)
although i got sound out correctly, there are significant sound issues- e.g. major buffering problems
requiring pre-buffering of at least 230ms and continual nagging from wine.  it does compain a bit about
not finding a jack server, so that is the next step in the process.

i'm encouraged by the small progress so far, as i haven't seen *any* progress on getting this to run under
wine anywhere else- and i keep googling.  the next course of attack will be to completely uninstall wine,
make sure everything is cleaned out and start from scratch.  i planned to back-up/format/restore my
main drive this weekend, so i'll get to it right after.  the logical steps from here seem to be:

fresh wine install
get jack running and playing nicely with alsa
get wine running with jack
installing FLS
moving forward from there...

suggestions, etc.  encouraged.  please post all progress you make and how you made it in this thread.

:D

---

### Post by xenoalien on 2006-12-23
There are 2 major problems that I can see when running FL Studio 6. I get two errors and some things do not display right. Instead there are black areas.

I attached some pictures of what it looks like and the error that shows.

---

### Post by majoridiot on 2006-12-24
didn't have much of a chance today, but DID get it to load existing .flp files and some of my 
own... probably checked 20 or more.  they seemed to play flawlessly and i didn't find any
errors with plugins with the ones i checked.  screen updates seemed to have a major lag, 
but it's probably due in part to the wine window spanning two monitors.  all in all, it looks 
VERY encouraging.

the load/save error seems to be linked somehow with the step sequencer.  if you minimize it
(F6) before loading or saving files, it doesn't seem to crash.  i didn't have the time to check
loading new samples or adding tracks.  changing patterns in the step sequencer and playlist 
functioned fine, although i didn't test exhaustively.

there were still a load of fixme and other warnings from wine.

what audio settings are you using in winecfg, xenoalien?  yours looks to be a config problem.

---

### Post by xenoalien on 2006-12-25
default settings

---

### Post by majoridiot on 2006-12-25
> **xenoalien said:**
> default settings

make sure you have only one audio driver enabled in winecfg.  mine defaulted to 3 and had
serious problems.  i disabled OSS and the third one (forget which) and left ALSA as the only
active sound driver for wine.  had to ramp-up the prebuffer in FL to compensate for serious
latency issues, but i get great sound.

---

### Post by sk8dork on 2007-01-23
just like to let you know that i'd be greatly interested in any progress made with this.

---

### Post by majoridiot on 2007-01-24
honestly, i have been off on other projects and hadn't had a chance to get at this lately...
however, i just installed the latest wine (.29) and have good news to report-

the mouse problems that previously made it unusable have been fixed!  the bug with the stepper
window still exists, so and file operations still crash it, but this can be gotten around by F6 to 
close it before opening/saving files.  i did a quick check on functions, plug-ins, etc. and everything
seemed to be functioning fine.  this was by no means a thorough check- i just loaded files
with multiple plug-ins and they seemed to be playing ok.  the speech synthesis function also
work fine when i did help-->about

this was tested on 5.02 demo, as it's what is installed.  i'm assuming that copying my registration
info into the registry would completely activate it, but i have not tested that.  based on my limited
tests i would rate its functionality at silver (by wine standards) now that the mouse problem is fixed.

---

### Post by sk8dork on 2007-01-24
i have the issue where the default track that loads up has 3 red instruments and one good one (hi hat). did you get that working?

---

### Post by majoridiot on 2007-01-25
the default does load like that on mine too.  but, other tracks work fine and there doesn't 
seem to be a problem building, running and saving new tracks. the pre-packaged projects
load and play fine as do the personal projects i tested.

---

### Post by Rmorris84 on 2007-01-25
Why not just use an open source alternative? I had a friend that I was trying to get to move to ubuntu and ditch windows, but his big thing was that he uses Ableton, which is way better than FL by leaps and bounds... So I knew if i was going to get him to switch I was going to have to find something that he could use in Ubuntu....

First I found Jokosher, [www.jokosher.org](www.jokosher.org) ... Which seems like it has its crap together and could actually turn out to be a cool project.

Another is Ardour, [www.ardour.org](www.ardour.org) ... Looks nice, alot closer to FL style and seems like it could get things done.

Also Sweep, [www.metadecks.org/software/sweep/](www.metadecks.org/software/sweep/) ... Potential also, but didn't look much into it.

And last but not least, Wired, [http://wired.epitech.net/](http://wired.epitech.net/) ... also nice, and worth checking out

Hope this helps you out some, and mainly the reason im posting these are to get the word out so hopefully projects like this can compete with the big names like Ableton, Reason, and FL that arent available for linux. :D

---

### Post by sk8dork on 2007-01-25
i am ALL about getting open source options to replace my proprietary apps. thing is that i paid for fruity loops way back when it was still called fruity loops, i think it was a 4x version, and i really like it. truth be told i've looked at ardour and it appeared to be more like a powerful alternative to audacity. i want a sequencer with piano roll abilities and real time fx and support for all kinds of synths and stuff like that. fl studio has come soooooo far with its current version. adding all kinds of stuff i can't be bothered to spell out here. i'll check out the projects  you mentioned, so thanks for that. some of them i have not heard of.

as for flstudio in wine, i looked more into the red instrument thing and this is what i noticed. some samples play, some don't. i noticed that the samples that would not play in flstudio would also not have a preview when browsing the directories. all of them can be opened up in audacity and played fine, and i can save a copy that then plays in flstudio as well as listen to the preview from nautilus. this makes me think it's something to do with a codec maybe or something like that. yeah, a lot of songs load up with everything working, but not all songs, and there are a lot of samples that don't work cuz of this. it seems that the separation of the windows don't play nice in wine so you can't drag things between, which is annoying but most things are doable by right click menus.

---

### Post by m666 on 2007-02-03
[http://appdb.winehq.org/appview.php?iVersionId=4304]("http://appdb.winehq.org/appview.php?iVersionId=4304")

I got it working (with some small issues though, as described on wine web page, link above)
I use Kubuntu 6.10 + wine 0.9.29 + FL Studio 6.0

---

### Post by xenoalien on 2007-02-24
Any more news about FL studio? Has anyone got it to work near perfect on Ubuntu?

Thanks

---

### Post by christhemonkey on 2007-02-24
> **sk8dork said:**
>  i want a sequencer with piano roll abilities and real time fx and support for all kinds of synths and stuff like that.


Something like muse or rosegarden will do all these things (and more).

---

### Post by sk8dork on 2007-02-25
FL Studio 7 is now out, and following the tips in that winehq page got me working exactly how the page says, which is tolerable. note: the person that did the testing on that page reports success in kubuntu. i am experiencing the same success running fluxbuntu edgy. awesome!

p.s., i did not think rosegarden could do the things i wanted...but i guess i'll check it out again.

---

### Post by xenoalien on 2007-02-25
Anyone have success with Ubuntu 6.10?

---

### Post by sk8dork on 2007-02-25
well, there's little different between my fluxbuntu and regular ubuntu edgy (6.10). you should just give it a try, even with the freely available demo copy. you don't really need to do much, just what's listed on that [winehq page]("http://appdb.winehq.org/appview.php?iVersionId=4304").

---

### Post by m666 on 2007-02-27
FL Studio version 6 is working on my system, version 7 not :( 

(Kubuntu Edgy)

---

### Post by sk8dork on 2007-02-27
be more specific about how it is not working. i just fresh intalled fls7 on my work pc (dell optiplex gx520 - Pentium D, 512MB RAM, integrated video and sound) and could not get it to recognize the sound device until i changed from oss to alsa in winecfg. i then had to turn the sound buffer in fls7 to full, 371ms, and set polling on and hardware buffer off. i can now listen to the 'new stuff' track almost without a hitch, but my cpu monitor in fls7 gets to about 53%.

---

### Post by m666 on 2007-02-27
FLS7 seems to take over my whole workspace, the KDE panel is hidden (behind), I can't switch (alt+tab) between applications, and no button in FL is working, I can't even close/quit application, so eventually I need to ctrl+alt+backspace or kill process from tty1. I think I'll stay with FLS 6, and in april I'm going to fresh install fluxbuntu 7.04, then I try FLS 7 again

---

### Post by sk8dork on 2007-02-27
weird. it sounds like you don't have winecfg set to emulate a desktop, but i would think that fls6 would go fullscreen and cover everything in the same way as fls7. you should try setting the emulate desktop option in winecfg, i have mine set to 1024x768 with my monitor resolution being 1280x1024.

---

### Post by m666 on 2007-02-28
I set virtual desktop in winecfg
IT WORKS!
thanx a lot for advise!

btw:
I upgraded to 7.04 yesterday, installed VMWare Player + Windows XP + FLS7 and I must say I was surprised by relatively  good performance !
[https://help.ubuntu.com/community/VMware/Player]("https://help.ubuntu.com/community/VMware/Player")

---

### Post by sk8dork on 2007-02-28
really...hmm, i may have to try that. glad the virtual desktop trick helped you out.

---

### Post by xenoalien on 2007-03-03
Anyone know where I could download FL Stuidio version 6?

---

### Post by m666 on 2007-03-04
I have fl studio 6 installer on my disk. If you still want it, send me private message with your email address

---

### Post by m666 on 2007-03-04
...or try to find  flstudio608_install.exe in google, I found many links!

---

