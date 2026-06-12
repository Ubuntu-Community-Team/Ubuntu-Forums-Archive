---
title: "ATI build problems"
date: 2006-07-07
forum: General Help
---

### Post by ehula on 2006-07-07
I am having problems installing the ATI-supplied driver on my Dapper install, after I have compiled a custom 2.6.17 kernel.

These are the steps that ran successfully:

> sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb
sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare
sudo module-assistant update
But, when I run the next command:
> sudo module-assistant build fglrx
I get:
> dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17-ck1.postinst; \
fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/kernel-headers-2.6.17-ck1 SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/kernel-headers-2.6.17-ck1'
/usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile:38: /usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu: No such file or directory
make[1]: *** No rule to make target `/usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu'. Stop.
make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17-ck1'
make: *** [build] Error 2
Can anyone please offer some help. It would be greatly appreciated.

---

### Post by vem0m on 2006-07-07
hey glad to see another ATi user here goes [THIS GUIDE]("http://ubuntuforums.org/showthread.php?t=204910") will tell you how to get it running i have with that guide got it running 3/3 tries its similar to what u are doing except for it seems that one part of the guide is differant then what you are doing

```

Compile the kernel module:

sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod

```

hope this helps if not start over with the steps in that guide :D

---

### Post by ehula on 2006-07-07
> **vem0m said:**
> hey glad to see another ATi user here goes [THIS GUIDE]("http://ubuntuforums.org/showthread.php?t=204910") will tell you how to get it running i have with that guide got it running 3/3 tries its similar to what u are doing except for it seems that one part of the guide is differant then what you are doing

```

Compile the kernel module:

sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod

```

hope this helps if not start over with the steps in that guide :D
I am doing exactly what that guide is saying. The only difference is that I am breaking the command:
[FONT="Courier New"][INDENT]sudo module-assistant build,install fglrx[/INDENT][/FONT]
into these two commands to isolate the problem:
[FONT="Courier New"][INDENT]sudo module-assistant build fglrx
sudo module-assistant install fglrx[/INDENT][/FONT]
The problem is that it fails as per my first message after I run the "build fglrx" command. I believe the cause may be that I am doing this on a custom kernel (2.6.17) as I stated above.

Has anyone successfully installed the ATI fglrx driver against a compiled 2.6.17 kernel?

---

### Post by vem0m on 2006-07-07
can you explain what is custom about it? also have u tried re compiling the kernel/ATi drivers?

---

### Post by ehula on 2006-07-08
> **vem0m said:**
> can you explain what is custom about it? also have u tried re compiling the kernel/ATi drivers?
This is what I have done so far:

I compiled the kernel from source I downloaded from kernel.org, with the ck1 patch applied. Then I removed all the fglrx stuff that I was using with kernel 2.6.15-xx. Then I tried installing the ATI drivers as described above.

Does that answer your question about recompiling kernel/ATI drivers?

---

### Post by vem0m on 2006-07-08
yes hmmmmm i never removed the fglrx stuff when i changed kernels i just reinstalled them and everything worked fine so i have no clue why its not working for you cept maybe u could try getting the older ATi drivers from the repositories then from there updating to the newest using that guide :)

---

### Post by ehula on 2006-07-08
The reason I removed the fglrx stuff is because I was using the restricted modules with my 2.6.15-25 kernel. This is my first attempt with ATI's proprietary driver.

I just looked and cannot find an older version of the proprietary ATI driver. I did notice though that ATI recommends that you uninstall older version of their driver before you update.

Any other ideas? Do the error messages I posted offer any clues?

---

### Post by vem0m on 2006-07-08
maybe are you using a 686 kernel? as what ATi is trying to do is read in the form of a i386 for some odd reason
> /usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile:38: /usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu: No such file or directory
make[1]: *** No rule to make target `/usr/src/kernel-headers-2.6.17-ck1/arch/i386/Makefile.cpu'. Stop.
make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17-ck1'

but beyond that i am not sure i am new to linux but learning fast but that may be your problem let us know so we may help further

---

### Post by ehula on 2006-07-08
I am using a kernel I compiled for Pentium M (Thinkpad T43p). I checked and I do have the following directory: /usr/src/kernel-headers-2.6.17-ck1/arch/i386.

---

### Post by vem0m on 2006-07-08
yes but what architecture is it for? what package did u use? as it is trying to use the make from that directory and if its not there or not the right architecture it won't work

---

### Post by ehula on 2006-07-09
I'm not sure what you are asking. I compiled the kernel for Pentium M...maybe I should have chosen 686? I can't remember what my choices were, but since I am running on a Pentium M, I thought that would be the best choice.

---

