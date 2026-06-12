---
title: "[SOLVED] alsa/oss?"
date: 2007-07-19
forum: General Help
---

### Post by leo_rockway on 2007-07-19
hello. i was having some problems w/ sounds: choppy sound when running some apps (ie. glest) or no sound at all w/ some other apps (pidgin) so i thought it was a good idea to update the alsa drivers.

it worked like a charm, now glest or pidgin play sounds perfectly. the problem is that my system sounds (along w/ wine sounds) won't play.

if i change the audio devide to alsa, then i get pidgin and glest sounds. if i change it to oss i get system sounds but no video sounds or mp3 sounds or game/pidgin sounds. i tried to use autodetect but that didn't work either (it works as if i'd pick alsa)
also, no matter what audio device i pick, all my flash sounds won't play (ie. youtube) which played w/o a problem before.

amarok was working before and after the driver updates, but now amarok won't open (i run from terminal and get no warnings or errors or anything, it just won't open). i tried restarting the comp, but that didn't work either.
[edit]amarok works now, so apparently amarok not working before was not related to the sound problem[/edit]

my sound card according to lspci is:

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

and it is called sigmatel intel hda in M$.

any help would be appreciated

TIA
Leo

---

### Post by leo_rockway on 2007-07-21
ok, i solved this. i modified a file called .asoundrc in my home folder and added a few lines i found in the alsa project website. i hope this helps somebody else out there w/ my same problem.

sudo nano ~/.asoundrc #To open the file... you can use vim or gedit too...

pcm.hda-intel {
           type hw
           card 0
        }

        ctl.hda-intel {
           type hw
           card 0
        }


Added those lines and now i have my sound back! but it is choppy again... :-(

---

