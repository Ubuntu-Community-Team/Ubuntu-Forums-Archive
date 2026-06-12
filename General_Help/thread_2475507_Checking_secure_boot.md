---
title: "Checking secure boot"
date: 2022-05-30
forum: General Help
---

### Post by cam17 on 2022-05-30
When I enter a command to check if secure boot is active on my 20.04.4 LTS it gives the followin

sudo mokutil --sb-state&#8203;

mokutil: unrecognized option '--sb-state&#8203;'

why is the command not recognized ?

---

### Post by yancek on 2022-05-30
According to the link below, that would mean that mokutil is not installed.  If it is, is should be in /usr/bin.  You can check this with either:  whereis mokutil or which mokutil.

[https://techoverflow.net/2019/05/23/how-to-check-if-secure-boot-is-enabled-on-ubuntu/](https://techoverflow.net/2019/05/23/how-to-check-if-secure-boot-is-enabled-on-ubuntu/)

---

### Post by cam17 on 2022-05-31
Yes it is installed. the result of the whereis as follows.
mokutil: /usr/bin/mokutil /usr/share/man/man1/mokutil.1.gz

Ubuntu is installed on a Win 10 machine with secure boot enabled.

---

### Post by sudodus on 2022-05-31
I have a 20.04.4 LTS system that is installed in BIOS mode alias CSM alias legacy mode. In that system there is no mokutil.

I have a 22.04 LTS system that is installed in UEFI mode and it works as expected,

```

$ sudo mokutil --sb-state&#8203;
SecureBoot enabled

```

It is strange that mokutil is installed but --sb-state is not recognized. Is your system running in UEFI mode or BIOS mode? You can check with

```

test -d /sys/firmware/efi && echo efi || echo bios

```

---

### Post by westie457 on 2022-05-31
In my 20.04 system 'mokutil --sb-state' returns invalid option. However shortening the command to 'mokutil --sb' returns ```
graham@graham-IdeaCentre-AIO-3-24ALC6:~$ mokutil --sb
SecureBoot disabled
Platform is in Setup Mode
```
No idea why that and some other options in the man page do not work as expected.

---

### Post by sudodus on 2022-05-31
Thanks for finding a more general syntax @westie457,

I tested in my 22.04 LTS system, and 
```

mokutil --sb

```

works there too, so it works both in 20.04 and 22.04 :-)

Please notice also that we need not use sudo.

---

### Post by cam17 on 2022-06-01
i get
mokutil --sb

SecureBoot disabled
Platform is in Setup Mode

however I have secure setup in my BIOS should this be enabled ?

---

### Post by sudodus on 2022-06-01
Some people think it is important to have it enabled, some people think it might as well be disabled. I have it disabled (I even run in BIOS mode (where there is no secure boot) in my main computer.)

---

### Post by #&amp;thj^% on 2022-06-01
> **sudodus said:**
> Some people think it is important to have it enabled, some people think it might as well be disabled. I have it disabled.

+1 Me as well.
```
mokutil --sb-state
SecureBoot disabled

```

---

### Post by cam17 on 2022-06-02
I have secure boot enabled in BIOS. How can Ubuntu be installed without being configured for Secureboot ?

---

### Post by sudodus on 2022-06-02
Ubuntu can be installed with and without secure boot enabled in the computer. There are special signatures in the Ubuntu software to make it accepted with secure boot, and these signatures are [only] checked when secure boot is enabled in the UEFI-BIOS system.

Ubuntu has bought a license from Microsoft in order to use these signatures. The alternative (used by several Linux distros) is to refuse to buy such a license, and those Linux distros cannot boot in a computer where secure boot is enabled.

---

### Post by sudodus on 2022-06-02
@cam17,
@westie457,

I am planning to create a bug report about **[FONT=Courier New]mokutil[/FONT]** because the mismatch between the options [FONT=Courier New]**--sb-state**[/FONT] and [FONT=Courier New]**--sb**[/FONT]
and the manual **[FONT=Courier New]man mokutil[/FONT]**.

Please let us know the version of mokutil in your systems (where [FONT=Courier New]**--sb-state**[/FONT] is missing). A well defined way is to run

```

apt-cache policy mokutil

```

and post the result in a reply.

---

### Post by MAFoElffen on 2022-06-03
On my laptop, I have:
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache policy mokutil
mokutil:
  Installed: 0.3.0+1538710437.fb6250f-1
  Candidate: 0.3.0+1538710437.fb6250f-1
  Version table:
 *** 0.3.0+1538710437.fb6250f-1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status

mafoelffen@Mikes-ThinkPad-T520:~$ mokutil --sb-state
This system doesn't support Secure Boot

mafoelffen@Mikes-ThinkPad-T520:~$ mokutil --sb
This system doesn't support Secure Boot

mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -d
Description:    Ubuntu 20.04.4 LTS

mafoelffen@Mikes-ThinkPad-T520:~$ test -d /sys/firmware/efi && echo efi || echo bios
efi

```
Even though 'mokutil' works on mine with both option switches... The reason I am interested in following this, is that in the UbuntuForums 'system-info' script I use 'mokutil' with this option as a diagnostic query... It will tell if an UEFI machine has SecureBoot enabled or not... I also recommend people install this even if their machine does not support SecureBoot (and if  booted as BIOS, because: (from the comments I included in my script)
```

                # These are the four known messages returned from UEFI utility mokutil
                # This system doesn't support Secure Boot
                # Secure Boot is enabled
                # Secure Boot is disabled
                # Failed to read SecureBoot
                # Platform is in Setup Mode
                # 
                # An error in stderr indicating that EFI Variables do not exist indicates that it is Legacy BIOS.

```
On a machine booted as BIOS boot, it will determine if it is a Legacy BIOS Machine, or if an UEFI capable Machine just booted in CSM Mode... So yes, this utility tells us a lot as a diagnostics tool, and that is why I use it for that purpose in the 'system-info' script. 

The documentation on 'mokutil' does not mention '--sb' as a valid option flag... But since westie357 found that it works, as the '--sb-state' option should, I currently have our script using that option flag, until this is resolved. That script needs to work on all flavors of all supported versions of Ubuntu... As well as for other branches and distributions in Linux (...to a point, functionally).

---

### Post by westie457 on 2022-06-03
@sudodus
As per your request for info ```
graham@graham-IdeaCentre-AIO-3-24ALC6:~$ apt-cache policy mokutil
mokutil:
  Installed: 0.3.0+1538710437.fb6250f-1
  Candidate: 0.3.0+1538710437.fb6250f-1
  Version table:
 *** 0.3.0+1538710437.fb6250f-1 500
        500 http://gb.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
graham@graham-IdeaCentre-AIO-3-24ALC6:~$ lsb_release -d
Description:    Ubuntu 20.04.4 LTS
graham@graham-IdeaCentre-AIO-3-24ALC6:~$ test -d /sys/firmware/efi && echo efi || echo bios
efi
graham@graham-IdeaCentre-AIO-3-24ALC6:~$ mokutil --sb-state
SecureBoot disabled
Platform is in Setup Mode

```
As you can see it has now started working properly

---

### Post by sudodus on 2022-06-03
It seems a recent upgrade of mokutil has squashed this bug :-)

---

### Post by MAFoElffen on 2022-06-03
I think for the sake of recovering (alternate methods of finding those answers) from that in the future, I have an idea to add some error handling in the 'system-info' script for 'mokutil'... I'm going to try to work on adding that to the 'system-info' script this weekend. I hear from you all that it is fixed, but it doesn't hurt to be prepared for the what-if's, and just-in-case's.

Thank you all for your keen eyes, due diligence and support to the users of Ubuntu.

---

### Post by Frogs Hair on 2022-06-05
I have never used sudo with that command. 

```
david@d-box:~$ mokutil --sb-state
SecureBoot enabled

```
```
ls /sys/firmware/efi
config_table  esrt              fw_vendor      runtime      systab
efivars       fw_platform_size  mok-variables  runtime-map  vars


```

---

### Post by dragonfly41 on 2022-06-05
For completeness here is what I see using **rEFInd** to boot ..

[FONT=monospace][COLOR=#000000]mokutil --sb-state[/COLOR]
SecureBoot disabled
[/FONT]
ls /sys/firmware/efi
config_table  efivars  esrt  fw_platform_size  fw_vendor  runtime  runtime-map  systab  vars

---

