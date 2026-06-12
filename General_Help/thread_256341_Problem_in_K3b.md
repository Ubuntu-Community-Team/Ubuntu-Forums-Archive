---
title: "Problem in K3b"
date: 2006-09-12
forum: General Help
---

### Post by Bigguy2468 on 2006-09-12
I installed K3b using Synaptic and all went well. Didn't see any dependencies being chosen by Synaptic at the time of the installation.

I decided to burn a disc to test the installation after it was done. I opened K3b, that worked, then I tried to select some mp3 files to burn, but every song I select comes back and says it's the wrong format. I opened my music directory and all the extensions I chose are .mp3 so that should work.

Then I closed k3b and reopened it in the terminal to see what the problem is. I thought maybe I had restricted rights or something so I opened the program with:
[COLOR="Blue"]sudo k3b[/COLOR]

The program opened with a lot of errors. Here is the print out of what I got:
paul@ubuntu-paul:~$ sudo k3b
Password:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: Communication problem with k3b, it probably crashed.
paul@ubuntu-paul:~$ k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
Link points to "/tmp/kde-root"
Link points to "/tmp/ksocket-root"

It's telling me that there is a problem in the /tmp directory, but I don't know what I am looking for.

Can anyone help me with this?

TIA

*Sorry about the smileys, the program is iterpreting a colone followed by a capitol D as a happy face.*

---

### Post by Bigguy2468 on 2006-09-12
I think I just found the answer in the WIKI
I'll give it a try, appears See Below:

[I]K3B does not come with MP3 decoding support out of the box. Depending on your version of Ubuntu, you will need different packages.

**Ubuntu 6.06**

For full functionality, install the following packages: libk3b2-mp3 sox transcode vcdimager [/I]

---

### Post by Bigguy2468 on 2006-09-12
Yup!
It works fine now!

---

