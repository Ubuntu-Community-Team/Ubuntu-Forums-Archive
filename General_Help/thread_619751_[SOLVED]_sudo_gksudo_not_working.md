---
title: "[SOLVED] sudo gksudo not working"
date: 2007-11-21
forum: General Help
---

### Post by CupofDice on 2007-11-21
I installed virtualbox earlier, and it worked just fine other than the fact I couldn't get sound to work. Next thing I know sound on gutsy stopped working and the music previews no longer showed the little sign that showed it was playing music. Amarok gives me a "xine was unable to initialize any audio drivers." error. It got worse.:( Sudo and gksudo no longer worked and I just downloaded a gutsy amd64 iso (lost my original copy :confused:), but I can't use the default burner. I got an error (There was an error writing to the disc:The recorder could not be accessed.). I still have the option of installing dapper, then using that on the iso I downloaded, but I would prefer to fix it first (if it's possible). Did I mess up when I added myself to vboxusers?  Any help is appreciated.

Edit- When I type "su gedit", I get "Unknown id: gedit"

Edit2- I just came across [aysiu's help here]("http://www.psychocats.net/ubuntu/sudo"). I'm gonna try it to see if it helps.

Edit3- Editing /etc/group worked. I can now use sudo, but still no sound.

Edit4- I just fixed the sound problem. I was playing around with sudo and decided to sudo beep-meidia-player and that worked, so it was a permissions problem. Manually editing /etc/group as suggested in the comprehensive sound problems solutions guide to give myself permission did not work, but "sudo chmod -R a+rwX /dev/snd/" worked instantly. I got that from [here]("http://alsa.opensrc.org/index.php/TroubleShooting#alsamixer:_function_snd_ctl_open_failed_for_default:_No_such_device").

---

