---
title: "NO sound"
date: 2007-08-09
forum: General Help
---

### Post by traildog on 2007-08-09
new installation--w/ the exception of no sound--no problems. any ideas??

---

### Post by raja on 2007-08-09
[This]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") is an excellent place to start from.

---

### Post by traildog on 2007-08-09
thanks for the link--i got all the way to the list of drivers and found my sound card listed and got to an ftp server with perhaps 100 drivers all with the same name. i opened a couple and they weren't for my card--do i have to go through all of them...?????!!!!!

i know it's all free but geez--how about a little labeling...

---

### Post by fredj on 2007-08-09
Before you start doing anything rash try to find out what sound chip you have and if a driver is
being loaded for it.
Open a terminal and type cat /proc/asound/card0/codec\#*
The first line of output from this will tell which sound chip you have.
Then also in a terminal type sudo lshw -class sound. This will tell you which driver is being loaded
for your sound card. Don't get tempted to try installing new drivers or recompiling Alsa until you
know if your sound card is already detected and supported.
Post the name of the soundchip and the driver here.

---

### Post by traildog on 2007-08-10
i typed the first command and got:  "no such file or directory"

i typed the 2nd and got:  "password:"

from the previous link in this thread i typed:  "lspci -v"  and got a list of my hardware with this info for the sound:

intel corp 82801db/dbm
(ich4/ich4-L/ich4-m)
ac97 audio controller vers 3


thanks for any help in advance!!

jim

---

