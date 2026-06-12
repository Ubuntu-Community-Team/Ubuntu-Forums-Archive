---
title: "No Audio after upgrade to 20.04"
date: 2021-01-31
forum: General Help
---

### Post by equi000 on 2021-01-31
Hi,

I'm new to the Forum. I used Bionic Beaver for 1 year and installed 20.04 today. I'm just a user and do not know too much about Linux configuration.

After upgrading to 20.04 the audio of my notebook does not work anymore. No sound on the head phone jack. Only Dummy Device available in the settings. I read some pages about that topic from mid of last year and tried some hints mentioned there (like several of these: [https://askubuntu.com/questions/1231602/no-sound-ubuntu-20-04-lts](https://askubuntu.com/questions/1231602/no-sound-ubuntu-20-04-lts) or [https://ubuntuforums.org/showthread.php?t=2457062&highlight=audio+device](https://ubuntuforums.org/showthread.php?t=2457062&highlight=audio+device)), but no success so far.

My system is a FUJITSU S761 notebook, LTS 20.04.02 64-Bit

Meanwhile I learned a little about the topic.

aplay -l shows:
Karte 0: PCH [HDA Intel PCH], Gerät 0: ALC269VB Analog [ALC269VB Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0

alsamixer says:
Gerät: HDA Intel PCH 
Chip: Realtek ALC269VB

So it seems the HW is basically there?

I read something about maybe a newer kernel that might fix this. But I don't know where to get this.

Any help appreciated.

---

### Post by Autodave on 2021-01-31
I am confused: did you do a clean install or upgrade what you already were using?

---

### Post by equi000 on 2021-01-31
I got the message in 18.04 that 20.04 is available, so I backuped my data to be secure to an external disc and then later I selected to upgrade - no clean install.

---

### Post by Autodave on 2021-01-31
I would suggest that you d-l 20.04 and burn it to a DVD or thumb drive and boot to that medium.  If your sound works, then your upgrade failed somewhere along the line.

I learned a looooong time ago to only do clean installs and never upgrade.  Most of the time, the upgrade works.  But when it doesn't, it can take longer to fix what it broke that it would take to just do a clean install.

---

### Post by equi000 on 2021-01-31
Hm, I already thought about reinstalling 18.04. But if your experience is that the new version might work with a clean install I&#8216;ll probably give it a try. I guess I&#8216;ll spend maybe the next weekend looking for a fix, but no more ;-)

---

### Post by equi000 on 2021-02-07
Ok, I decided to try a clean install of 20.04. Audio works fine now, but it took quite some time till NAS (Samba V1 based) and printer worked again. Seems like Gutenprint is not part of 20.04 by default.

---

