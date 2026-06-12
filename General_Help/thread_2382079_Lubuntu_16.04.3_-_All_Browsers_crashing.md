---
title: "Lubuntu 16.04.3 - All Browsers crashing"
date: 2018-01-08
forum: General Help
---

### Post by cswd2 on 2018-01-08
I'm new to Linux and trying to get Lubuntu running on a fairly old PC.  Hardinfo gives the spec details below, but in summary it's an AMD Athlon 1.24 GHz, 1.5 Gb RAM, 160 GB HDD bought in 2003.

I installed Lubuntu from the Minimal CD, have a decent wireless network connection to download and install anything extra required. I struggled to get my head around Synaptic, so have used LXTerminal to install. LibreOffice seems to function OK.

However, I need to get a web browser working so I can at least use the BBC website, sites like this and, ideally, YouTube etc. but:
Firefox crashes on trying to open it (crash report below, though it doesn't look like it has any useful info to me).
Chromium installs, but does nothing when I try to open it, not even giving the impression of trying to open then crashing.
Web (which seem to list itself as Epiphany in Task Manager) almost works but tends to crash after 20 seconds saying 'Oops! Something went wrong while displaying this page. Please reload or visit a different page to continue.'.

Hunting around the forums others have had similar issues but none of the threads seem to have a solution.

I'd like to use Lubuntu, but I'm wondering if the PC just isn't powerful enough. I guess I've got a couple of options:
1) Work out a fix to a web browser, but perhaps the CPU not having SSE2 is the issue and I'll never get one to work properly.
or
2) Move to an older Lubuntu distro - will 14.04 LTS work given it's older it might not need quite as much power?
or
3) Find a different Distro.  E.g. Puppy Linux or Core Linux seem to have very low system specs.  However, if I do this, I'm worried that I'm just wasting time as the browser (Web, FF, whatever) will need just as much PC power to run whatever underlying OS it is running on.
or
4) Give up, admit the PC is too old and bin it.

I could wipe an old SATA HDD and put that in if it would help significantly.

Thanks for any advice you can provide, below are the various crash reports etc. I've saved to a USB stick and transferred to a second PC so that I can post this without it all crashing.

Cheers,
cswd

Firefox Crash report:
uildID:         20180104113147
CrashTime:         1515454740
InstallTime:     1515188380
ProductID:         {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName:     Firefox
ReleaseChannel: release
SafeMode:         0
SecondsSinceLastCrash: 1496
StartupCrash:     1
StartupTime:     1515454738
ThreadIdNameMapping: 3259:"Gecko_IOThread",3260:"Timer",3261:"Link Monitor",3262:"Socket Thread",3263:"JS Watchdog",
Throttleable:     1
UptimeTS:         3.252177
Vendor:         Mozilla
Version:         57.0.4


From Hardinfo:

-Computer-
Processor        :             AMD Athlon(tm)
Memory        :                 1543MB (265MB used)
Operating System        :     Ubuntu 16.04.3 LTS
User Name        :             user (user)
Date/Time        :             Mon 08 Jan 2018 23:37:52 GMT

-Display-
Resolution        :             1920x1200 pixels
OpenGL Renderer        :         Unknown
X11 Vendor        :             The X.Org Foundation
-Multimedia-
Audio Adapter        :         NFORCE - NVidia nForce2
Audio Adapter        :         MPU-401 UART - MPU-401 UART
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
-Printers (CUPS)-
MP600        : <i>Default</i>
-SCSI Disks-
ATA SAMSUNG SP1614N
HL-DT-ST DVDRAM GSA-4120B
E-IDE CD-ROM CR-850E
Canon MP600Storage

-Processor-
Name        :                     AMD Athlon(tm)
Family, model, stepping        :     6, 8, 1 (AMD Athlon XP/MP (Thoroughbred))
Vendor        :                     AuthenticAMD
-Configuration-
Cache Size        :                 256kb
Frequency        :                 1250.00MHz
BogoMIPS        :                 2511.81
Byte Order        :                 Little Endian
-Features-    
FDIV Bug        : no
HLT Bug        : no
F00F Bug        : no
Coma Bug        : no
Has FPU        : yes
-Cache-
Level 1 (Data)        : 2-way set-associative, 512 sets, 64KB size
Level 1 (Instruction)        : 2-way set-associative, 512 sets, 64KB size
Level 2 (Unified)        : 16-way set-associative, 256 sets, 256KB size
-Capabilities-
fpu        : Floating Point Unit
vme        : Virtual 86 Mode Extension
de        : Debug Extensions - I/O breakpoints
pse        : Page Size Extensions (4MB pages)
tsc        : Time Stamp Counter and RDTSC instruction
msr        : Model Specific Registers
pae        : Physical Address Extensions
mce        : Machine Check Architeture
cx8        : CMPXCHG8 instruction
apic        : Advanced Programmable Interrupt Controller
sep        : Fast System Call (SYSENTER/SYSEXIT)
mtrr        : Memory Type Range Registers
pge        : Page Global Enable
mca        : Machine Check Architecture
cmov        : Conditional Move instruction
pat        : Page Attribute Table
pse36        : 36bit Page Size Extensions
mmx        : MMX technology
fxsr        : FXSAVE and FXRSTOR instructions
sse        : SSE instructions
syscall        : SYSCALL and SYSEXIT instructions
mmxext        : Extended MMX Technology
3dnowext        : Extended 3DNow! Technology
3dnow        : 3DNow! Technology
3dnowprefetch
vmmcall

---

### Post by Autodave on 2018-01-08
I cannot help you with Firefox, but do not give up on that machine yet. I run Xubuntu off of a machine that makes your's look like a race car! You should have more than enough there to run Lubuntu.

Exactly what version of Lubuntu did you install?  Did you make sure that all updates were done after the install?

---

### Post by Impavidus on 2018-01-09
sse2 isn't listed among the capabilities of that CPU. Firefox 57 needs sse2. An older supported release of Ubuntu (or Lubuntu, or any other flavour) will give you the same version of Firefox, so that won't help. You could try Firefox 52 esr, an extended support release you can download directly from Mozilla, which doesn't need sse2 and has a few months of support left. I don't know about other web browsers, but I think Firefox isn't the only one that needs sse2 now.

Using an old and unsupported web browser is a bad idea. It's how people get malware.

---

### Post by cswd2 on 2018-01-09
> You should have more than enough there to run Lubuntu
Excellent, that's good to hear.

> Exactly what version of Lubuntu did you install?
lsb_release -a tells me it's Ubuntu 16.04.3, though it says Lubuntu when I logoff (pretty sure I installed Lubuntu).

After install, I followed the most of the instructions here:
[https://sites.google.com/site/easylinuxtipsproject/first-lubuntu](https://sites.google.com/site/easylinuxtipsproject/first-lubuntu)

I've also run Memtest for an hour and a half and it shows no errors.
I'm happy to reinstall if that might address any issues.

Thanks again!
cswd

---

### Post by cswd2 on 2018-01-09
Great, thanks for the Firefox ESR suggestion, I followed the details here to install it:
[https://askubuntu.com/questions/894871/how-do-i-install-firefox-52-esr-on-16-04](https://askubuntu.com/questions/894871/how-do-i-install-firefox-52-esr-on-16-04)

i.e. this:
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt-get update
sudo apt-get install firefox-esr

And that got Firefox ESR running. A quick test suggests that it's working OK. YouTube gives various Unresponsive Script errors, but I'm guessing that it's because it's processor bound so unless I can find decent drivers for the graphics card, that's about as much as is possible.

That saves me trying a reinstall / an alternative distro.

Thanks for all the help!

Regards,
cswd

---

### Post by Impavidus on 2018-01-09
Now keep in mind that Firefox 60 ESR will be released in May and your PPA will pull that one in automatically, but as that will probably need sse2 it won't work on your computer. I don't know that PPA, it may be possible (somehow) to stick to Firefox 52 for a bit longer, as it will be supported until August. After that, you'll need a different solution.

---

### Post by alberane2 on 2018-01-09
Perfect! tnk!

---

### Post by cswd2 on 2018-01-10
> [COLOR=#000000]Now keep in mind that Firefox 60 ESR will be released in May and your PPA will pull that one in automatically, but as that will probably need sse2 it won't work on your computer.
Thanks, good point.  Is there any way to turn the automatic update off, just for Firefox?
It looks like I've only got a couple of options:
1) IF I can turn auto-update off, I'll end up using a slightly out of date web browser (admittedly not great)
or:
2) Having a computer that doesn't browse the internet = useless = thrown away
or:
3) Going back to e.g. Windows XP and Opera (which still supports XP)

Thoughts / alternatives gratefully received!

cswd[/COLOR]

---

### Post by missmoondog on 2018-01-10
you will need this browser, [http://linux.palemoon.org/](http://linux.palemoon.org/). scroll down to where it says "Pale Moon for Linux - SSE-only build"

simply put the palemoon folder in your home directory, unrarred of course, and click the palemoon executable and it will launch. basically, a portable version. no installation required but will remember history, bookmarks, etc.

you can install it also. they have directions on the page, but i've never figured that option out!

i use this on 2 old machines i have! works great. better than firefox anyway. i actually use palemoon on all machines, but use the regular version on those.

every time a new version comes out, just go back to that link and download it from same link and replace all files in the folder.

hope this helps and hope i'm talking about the right thing!

---

### Post by cswd2 on 2018-02-02
Thanks, missmoondog, PaleMoon seems far more stable than Web, Chromium and the various other browsers installed by default.

Thanks again to all, I think this issue is well and truly fixed!

cswd

---

### Post by missmoondog on 2018-02-05
oops! never mind. i see it's already marked as solved.

---

