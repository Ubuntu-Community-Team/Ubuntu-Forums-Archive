---
title: "Dmraid won't list raid device!"
date: 2007-01-01
forum: General Help
---

### Post by Qchan on 2007-01-01
[b][color=darkred]
Hello all! I'm using Ubuntu 6.10 Edgy. I have a MSI AN8-N7 board. It uses the sil sata raid controller (if you want to call it that since it's software anyway!)

Well, in anycase. I followed the directions for how to install/setup dmraid for Raid 0 here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Now, keep in mind that I already have an install of Windows XP on this raid. So, I cannot use the software raid that in bundled with Linux/Ubuntu.

I follow the directions to the T. I install dmraid and I go ahead and check /dev/mapper. This is what I get:

> 
qchan@Natsumi:/dev/mapper$ dir
control
qchan@Natsumi:/dev/mapper$


As you can see, the device(s) aren't listed! However, when I do this:

> 
qchan@Natsumi:/dev/mapper$ sudo dmraid -r
Password:
/dev/sdb: sil, "sil_agajeibiccdg", stripe, ok, 135369126016 sectors, data@ 0
/dev/sdc: sil, "sil_agajeibiccdg", stripe, ok, 135369126016 sectors, data@ 0
qchan@Natsumi:/dev/mapper$


There's the raid in plain sight!!

I tried doing this on a LiveCD as well and I get the same issue. What could I possible be doing wrong?
[/b][/color]

---

### Post by Qchan on 2007-01-02
[b][color=darkred]
Bump!

Anyone know?
[/b][/color]

---

### Post by Hibbelharry on 2007-01-06
please search for an updated dmraid package(1.0 ...rc09->rc13), it's flying around somewhere in ubuntu bugzilla or compile it by hand, you can even do this from the livecd. It should cure your problem, as it has done for me.

Good luck ;)

---

### Post by Qchan on 2007-01-07
[b][color=darkred]
Sorry, I didn't specify. I'm running dmraid 1.0.0.rc13-2. It appears to be the latest version
[/b][/color]

---

