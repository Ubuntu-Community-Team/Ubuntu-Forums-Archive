---
title: "Wine ERRORS"
date: 2006-10-28
forum: General Help
---

### Post by handband2 on 2006-10-28
I'm wondering if anyone else got the same errors I'm getting.

I just installed a clean install of edgy.  I then installed **WINE (0.9.22-0ubuntu3)** from the **Synapic Package Manager**.  Then I ran **winecfg** and I get this error:
```
wine: creating configuration directory '/home/*user*/.wine'...
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: '/home/*user*/.wine' created successfully.
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  145 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x24c
  Serial number of failed request:  19
  Current serial number in output stream:  19
```

I'm not sure why I get this error from **WINE** because **Cedega** and **Crossover** installed and run just fine.

---

### Post by handband2 on 2006-10-28
Okay, I fixed one of my problems...

I installed the following: 
[LIST]
[*]libjack0.100.0-0
[*]libjack0.100.0-dev
[*]libjackasyn-dev
[*]libjackasyn0
[/LIST]
```
sudo apt-get install libjack0.100.0-0 libjack0.100.0-dev libjackasyn-dev libjackasyn libjackasyn0
```
This got rid of my error> fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

Now I just need to fix > fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.


---

### Post by manifoldronin on 2006-11-14
Hi handband2,

Did you get past the BadWindow error?  I'm having almost exactly the same error when running winecfg.

Thanks.
--mr

---

### Post by CompShrink on 2006-12-10
The solution is use an earlier version of wine. I'm using the dapper version of wine(0.9.9) in Edgy, and it works fine for me with xinerama. Using ti of course because I had the same problem as you.

dapper version:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fw%2Fwine%2Fwine_0.9.9-0ubuntu2_i386.deb&md5sum=4546533378332b6a7a82f7c09f2ae755&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fw%2Fwine%2Fwine_0.9.9-0ubuntu2_i386.deb&md5sum=4546533378332b6a7a82f7c09f2ae755&arch=i386&type=main)

just type in a terminal
```
dpkg -i wine*.deb
```
once you download that

---

