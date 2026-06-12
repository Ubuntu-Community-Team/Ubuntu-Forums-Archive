---
title: "Cannot open previously working VMPlayer"
date: 2006-07-15
forum: General Help
---

### Post by dotancohen on 2006-07-15
Until recently I had no problem starting VMPlayer and running a virtual WindowsXP. The probelm _may_ have started when I updated via apt-get, as I have had other problems since. Now, when I try to run VMPlayer, I get this:

dotancohen@ubuntu:~/video2$ vmplayer WindowsXP.vmx
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
kde-config: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
kde-config: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Also, two error messages pop up, but they are blank. They have only an OK button, no text.

Dotan Cohen
[http://what-is-what.com](http://what-is-what.com)

---

### Post by bigken on 2006-07-15
you have probablys update the kernel i got round this by reruning the vmware script and it solved my problems if look about the the frorum you will also find other answers to this ;)

---

### Post by dotancohen on 2006-07-15
Yes, I did in fact update the kernel. What do you mean by rerun the vmware script. To install windows I just called vmware with the name of the iso file. To start windwos, I would call vmware with the name of the vmx file.

What must I do?

---

### Post by bigken on 2006-07-16
reinstall vmware

---

### Post by krazykirk on 2006-07-16
I had that same problem (well kind of) and what i did was i ran vmware, (by just typing vmware in the console) then it told me to run a script file, i ran that and that fixed it!

---

### Post by dotancohen on 2006-07-18
Which script file, please?

---

### Post by andy_cowman on 2006-07-18
Where ever you extracted the VMware files to there is a folder called 

vmware-player-distrib

in there is a file called vmware-install.pl which you need to run from the terminal (i think as sudo but cant remember). THis will then re configure VMplayer to the new kernel you have. Make sure you have the correct kernel image files installed aswell (which if you had it working before and upgraded you have anyway) by looking in /usr/src for a directory called something like

inux-headers-2.6.15-26-686

depending on which kernel you have installed.

Good luck

---

### Post by dotancohen on 2006-07-20
Thanks. We left Haifa and the computer on Sunday, but as soon as we can return I'll try that and report back with the results. I assume that a previously-working OS file will continue working again? I had some important things stored in that file. If not, I'd rather boot the old kernel and jsut use that.

Dotan Cohen
[http://gmail-com.com](http://gmail-com.com)

2

---

