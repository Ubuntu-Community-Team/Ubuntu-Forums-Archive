---
title: "Can't get Ubuntu to boot live from disk on older laptop"
date: 2020-01-12
forum: General Help
---

### Post by lexmarks567 on 2020-01-12
I Have a old Gateway 9550 that came with windows 98SE. I tried burning the iso for Ubuntu 16.04 in both 32 and 64 as that meets the system requirements but nether will boot on startup. The only thing that will boot live is BT3 that was included when I bought the laptop. it refuses to run ubuntu 16.04 or any other OS like haiku etc. No hardrive at the moment as the machine didn't like the 100Gb I put in. I checked and it's burned correctly with all the files. Any ideas? Again BT3 boots live no issues. Bios is set to boot from the dvd drive first.

---

### Post by CelticWarrior on 2020-01-12
I seriously doubt that something of the Windows 98 era supports any current Linux distro. And certainly not 64'bit.

---

### Post by mörgæs on 2020-01-12
You could try [Antix]("http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html#_system_requirements") as an educational project but you will not get any real use out of a Pentium 3.

---

### Post by lexmarks567 on 2020-01-12
> **mörgæs said:**
> You could try [Antix]("http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html#_system_requirements") as an educational project but you will not get any real use out of a Pentium 3.

I will take a look and see if the machine will play nice. I also got Lubuntu 18.04 32'bit to try also along with the 16.04 powerpc image for the mac powerbook G4 as that ones giving me crap also claiming no files that can be read by the OS.

---

### Post by mörgæs on 2020-01-13
A Powerpc ISO is made for the Powerpc processor. It would surprise me if it worked on a Pentium 3.

If you want a text-only environment there are many options, by the way.

---

### Post by guiverc on 2020-01-13
The current i386 ISOs require a 686 class cpu.  I suspect you're dealing with a 586 class cpu only, which the linux kernel will not boot.

Ubuntu follows debian's standard of treating all of i386, i486, i586 & i686 cpu (or all of x86 32-bit) as i386 so the real limitation necessary isn't immediately apparent.  But Ubuntu's kernel is easily detected, and it has the same restrictions as the linux kernel itself has, so for 18.04 LTS, the default ISOs use the 4.15 kernel so use that to look up minimum specifications, for 18.04.2 the 4.18 kernel is used so look up that etc...

For your type of CPU, you may boot up Ubuntu 10.04 LTS probably (I recall it running on pentium II processors), but I doubt you'll get anything later running (Ubuntu 11.04 wouldn't run on pII/III as I recall; or if it did at beginning of cycle, during the 11.04 cycle a change occurred that created issues for cpus that ancient... [I]It could also be my memory is hazy & it was a different cycle
[/I]
You didn't provide specs of CPU, but I suspect it's the classification of 386/486/586/686 used by intel/amd/kernel that is your issue, and you're trying to run 686 code on a lower grade of x86 cpu.  *Some of this wording could be less than ideal, sorry I'm not fact checking*

---

### Post by mörgæs on 2020-01-13
A Pentium 3 is part of the i686 family / P6 architecture so no problem with kernel support.

---

### Post by lexmarks567 on 2020-01-14
Processor is a Intel P3 1.066Ghz. 512 MB ram 30GB hardrive. Laptop is a gateway solo 9550

---

### Post by CelticWarrior on 2020-01-15
> **lexmarks567 said:**
> Processor is a Intel P3 1.066Ghz. 512 MB ram 30GB hardrive. Laptop is a gateway solo 9550

Not even the current Lubuntu will work acceptably in such ancient hardware.

---

### Post by mörgæs on 2020-01-16
Lubuntu has deviated quite a bit from its 'light' roots. For a real light distro Antix is one of the options as mentioned above.

---

### Post by lexmarks567 on 2020-01-18
You know it never occurred to me the reason it won't boot is cause all the Ubuntu or Lubuntus I tried installing were all burned on DVD. The machine can only read CD-Rs. BT3 is on CD as well as the PC check software. Even antiXbase is over the 700MB limit for a blank CD. I need to get a external DVD burner and try again. I had one but can't find it. Could try bootable USB.

---

### Post by mörgæs on 2020-01-18
There are many Antix variants, for example Antix-net which fits to a CD.

---

### Post by guiverc on 2020-01-18
@[COLOR=#DD4814][mörgæs]("https://ubuntuforums.org/member.php?u=939075") [/COLOR]I don't think Lubuntu has deviated from it's "*light*" roots, in fact Lubuntu 18.10 & 19.04 performed better in my experience/usage on single core pentium M laptops with 1-1.5gb of ram over older Lubuntu with LXDE. 

Given the speed drop on MATE and later XFCE as it moved from GTK2 to GTK3 on that hardware, I was pleasantly surprised when the move to LXQt actually increased performance on that really old hardware.

(*I really can't compare with much older Lubuntu's than 16.04; I wasn't using Lubuntu before then*)

---

### Post by C.S.Cameron on 2020-01-18
Puppy Linux is small, full featured and fun.
The spec's are minimal.
The large number of release options might be confusing.
[https://www.ncf.ca/ncf/support/wiki/Puppy_Linux](https://www.ncf.ca/ncf/support/wiki/Puppy_Linux)

---

### Post by lexmarks567 on 2020-01-19
Still having issues. Even when using PLOP boot manager it still refuses to boot from USB or external DVD drive. Found a copy of AntiX 386 base 19.1 that just fits on a CD. I get all the way to installing grub boot loader and I get grub install failed. I Go into control panel I get to boot repair but then it asks for a password I don't have one. I tried using the ones I setup during install but it won't accept those. What is the password or how do I get grub to install so it will boot from the hardrive.

---

### Post by mörgæs on 2020-01-20
Try first to [install the text-only version]("https://sourceforge.net/projects/antix-linux/files/Final/antiX-19/antiX-19.1_386-net.iso/download") and then we can add a GUI later.

---

### Post by lwalper on 2020-01-20
Or you might try [PuppyLinux]("http://puppylinux.com/"). It's supposed to run in that architecture.

---

