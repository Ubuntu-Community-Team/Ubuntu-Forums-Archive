---
title: "Compiling PCSX2 from SVN"
date: 2007-12-05
forum: General Help
---

### Post by barius on 2007-12-05
This should work on Feisty, Gutsy and Hardy, just make sure to read the NOTE in step 1.  
The following will download the full SVN source code, and compile the emulator + available plugins.  You can simply select+middle-click the following blocks of code into a console to execute them (click Enter to complete each command in the console).

*Update - 2008-04-28
 - If you have just upgraded from Gutsy/Feisty to Hardy you will find that PCSX2 will not run anymore.  This is because libglew1.4-dev has been replaced with libglew1.5-dev.  All you need to do is make sure libglew1.5-dev is installed and recompile (or just redo the 4 steps below).

*Update - 2008-01-09
 - Added a 'Common Questions and Answers' section below.

*Update - 2007-12-14
 - Added the library 'libsdl1.2-dev' to step (1) because the pkgconfig file 'sdl.pc' is now needed by the zeropad plugin v0.2.0.
 - The recent addition of Zeropad v0.2.0 seems to have caused a strange bug during compilation.  The problem seems to happen only if you've already downloaded a previous version of the SVN code.  The error will look something like this:
```

...
mv -f .deps/libZeroPAD_a-zeropad.Tpo .deps/libZeroPAD_a-zeropad.Po
make: *** No rule to make target `linux.cpp', needed by `libZeroPAD_a-linux.o'.  Stop.
Error with building plugins

```
If you see this, the easiest fix is to delete the source code and start again from scratch.  I.e. delete everything from the pcsx2 folder *except* for the bin folder (which contains your save-games, bios, etc) and follow this guide again from the start.

**---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------**

(1) Install the needed libraries.  
NOTES: replace libglew1.5-dev with
 Gutsy: libglew1.4-dev
 Feisty: libglew-dev

```

sudo apt-get install subversion libsdl1.2-dev libjpeg62-dev build-essential \
libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 \
libbz2-dev libasound-dev nvidia-cg-toolkit libglu1-mesa-dev libglew1.5-dev;

```

(2) Create a folder for the source code:

```

cd ~/;
mkdir pcsx2;
svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2

```

(3) Make sure permissions are right, then build it:

```

cd pcsx2;
chmod +x build.sh;
sh build.sh all

```

(4) Create a startup script.  By default the compilation will create the pcsx2 executable in the ~/pcsx2/bin folder.  The following script will put a start script named 'play.sh' in that folder.  If you want to move the executable somewhere else, you need to move the whole bin folder, and modify this script appropriately.

```

cd bin;
echo \#\!'/bin/bash' > play.sh;echo 'cd ~/pcsx2/bin'>>play.sh;\
echo 'LD_LIBRARY_PATH="./" ./pcsx2' >> play.sh;
chmod +x play.sh

```

(5) Start 'er up either from the desktop file browser by clicking on play.sh, or from the commandline with 
```

./play.sh

```

The first time it runs you will be asked to configure it.  If you followed the steps above then the default locations will be ~/pcsx2/bin/plugins and ~/pcsx2/bin/bios.

You can update your installation by doing steps 2 and 3 over again at any time.

Notes for newbs:
[LIST]
[*]PCSX2 requires a PS2 bios.  To use the emulator legally you must dump the bios from a PS2 that you own.  The PCSX2 forums contain links to bios dumping guides.
[*]Only the OGL graphics plugins will work on Linux.
[*]PCSX2 requires a *very* powerful machine to emulate 3D games at reasonable frame rates.  See the PCSX2 faq on their forums for more details.
[*]Many games do not yet run properly on the emulator.  The PCSX2 team have provided a compatibility list so that you can look up the status of your game.  Only those games listed as 'playable' can be run without major issues.  The link to the list is below.
[/LIST]

Compilation problems:
[LIST]
[*]If you're having trouble compiling the plugins you may have better luck by installing a newer version of the CG Toolkit from the [Nvidia Developer]("http://developer.nvidia.com/object/cg_toolkit.html#downloads") site.  The version provided in the Ubuntu repositories is usually several months out of date, though I've never had a problem with it myself.
[*]If you use AMD or Nvidia graphics cards you will need to install the non-free drivers.
[*]If your CPU does not support SSE2 or higher you might as well give up now.
[*]If your GPU (graphics card) does not support Pixel Shaders 2.0 or higher you are similarly out of luck.
[*]Search both Google and the PCSX2 forums before asking questions about your hardware.  Every question imaginable has already been asked, and the forum moderators will likely ignore you if you haven't made an obvious effort to find previous answers.  Also see the FAQ as it answers many of these questions.
[/LIST]

Personal Experience:
[LIST]
[*]Compiz on Kubuntu severly impacts performance.  Turn it off while playing (in console "kwin --replace &").
[*]I bought a Logitech RumblePad2 controller not really knowing if it would work with Ubuntu/PCSX2.  Thankfully, it works great with zero setup issues!
[/LIST]

Common Questions and Answers:
[LIST]
[*] Q: I get 30 fps but the game seems to move in s-l-o-w m-o-t-i-o-n!
 A: PCSX2 frame rate does not work the same way PC games do.  30fps in PCSX2 is *half* the normal speed of the game played on a real PS2, so it will feel very slow.  Don't expect to get full speed in *any* game without some serious gaming hardware.
[*] Q: I have a QuadCore CPU (4 cores), can PCSX2 be configured to use all 4 cores?
 A: No.  PCSX2 is programmed to use only 2 cores.
[*] Q: What's the best GS/CDVD/Whatever plugin to use?
 A: It varies.  In general, the best plugins are the ones that work for you.
[*] Q: Why does game <insert name here> keep crashing?
 Q: Why does game <insert name here> not run?
 Q: Is there a 'trick' to make game <insert name here> run better/faster?
 A: The compatibility list posted at [www.pcsx2.net](www.pcsx2.net) lists almost every game in existence and how well it is emulated at this time.  If your game has a status other than 'playable' then give up now and wait for a new release, it is pointless to even ask the question on their forum.  On the other hand, if the game is listed as 'playable' and you are having trouble with it you may find the answer on their forum.
[*] Q: How do the developers prioritize improvements to games?
 A: They don't.  PCSX2 is not designed to emulate individual games, it emulates the hardware of the PS2 as a whole.  As the emulator is improved, emulation of all games will improve.
[/LIST]

Links:
[LIST]
[*][PCSX2 Home]("http://www.pcsx2.net")
[*][Compatibility Guide]("http://www.pcsx2.net/compat.php?c=key") - Explains what games are playable on the emulator to date.
[*][FAQ]("http://forums.ngemu.com/pcsx2-official-forum/62230-pcsx2-0-9-4-faq-frequently-asked-questions.html")
[*][Forum]("http://www.pcsx2.net/forums.php")
[/LIST]

---

### Post by ehcualp on 2007-12-05
Mucho gracious!  I cant wait to play my games! All i have to do now is get the bios from my ps2

---

### Post by Bonster on 2007-12-08
Can u upload your working PCSX2 file somewhere.
I try compiling with the guide still getting errors.

---

### Post by barius on 2007-12-08
No, it's too large to post here.
Make sure that you have all the packages from step 1 installed.  Also, don't put your bios/plugins under too many folders since there are some path length limitations.  If you still get errors when compiling then post your errors and what hardware you have in the PCSX2 forums.  They are usually pretty helpful to Linux SVN users.

---

### Post by Bonster on 2007-12-09
Well u can upload it to mediafire or megaupload or rapidshare. I would join the PCSX2 forum but seems like they banning everyone that trys to sign up. So I cant sign up so this is the only forum I can get help from.

I did manage to compile from the Official Source package. But it didnt have the plugins. And it was giving me all these GS errors and such.


However on the SVN always gives me errors. So I never manage to pass the point on compiling that.

make[2]: Entering directory `/home/bonster/Desktop/gtg/plugins/gs/zerogs/opengl'
make[2]: Nothing to be done for `install-exec-am'.
test -z "" || mkdir -p -- ""
  /usr/bin/install -c 'libZeroGSoglr.so.0.96.2' '/libZeroGSoglr.so.0.96.2'
/usr/bin/install: cannot create regular file `/libZeroGSoglr.so.0.96.2': Permission denied
make[2]: *** [install-traplibPROGRAMS] Error 1
make[2]: Leaving directory `/home/bonster/Desktop/gtg/plugins/gs/zerogs/opengl'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bonster/Desktop/gtg/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1

---

### Post by barius on 2007-12-09
The only reason anyone gets kicked from the PCSX2 forum is for talking about pirated games/bioses.  The development team has a very strict no-piracy stance, for obvious reasons (..Sony legal dept.).  If you want help, make sure you are using a legally obtained bios and games, it's that simple.  It's not like a PS2 is crazy expensive anymore anyways, you'll have a lot more fun playing games on the real thing for a few years yet because the emulator still has a ways to go before it's as stable as the old PS1 emus.

As to your compiling problem, judging by the paths in the error report you did not follow the guide exactly.  The error is quite clearly a permissions issue due to something you've done differently.  Delete what you have, and follow the guide above by simply copy/pasting the commands into a terminal.

---

### Post by Phayder92889 on 2007-12-09
Gods amongst men reside within this forum.

Thanks!

---

### Post by Bonster on 2007-12-12
I didnt get kick from the PCSX2 forum. I was never even in it. They dont let me sign up. Keeps saying ban when I try to sign up. Maybe u can tell those guys to fix this. I emailed them like 1week ago but the problem still the same. Is not only me others experience this also.

Thanks BTW: I think it was the long path limit you said.

---

### Post by go_beep_yourself on 2007-12-12
> **barius said:**
> 
[*]If your CPU does not support SSE2+ you might as well give up now.
[/LIST]

```
chris@ubuntu:~/Desktop/pcsx2$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2200.222
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr 
sse [COLOR="Red"]sse2[/COLOR] ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4403.13
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2200.222
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr 
sse [COLOR="Red"]sse2[/COLOR] ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4400.72
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

chris@ubuntu:~/Desktop/pcsx2$ 
```

Is sse2 not the same as sse2+. Does anyones cpuinfo say sse2+ or just sse2? I've been able to compile pcsx2 before, but I never got it to run correctly :(

---

### Post by barius on 2007-12-12
When I wrote SSE2+ what I meant was you need SSE2 *or better*.  Your CPU is fine.

---

### Post by go_beep_yourself on 2007-12-12
> **barius said:**
> When I wrote SSE2+ what I meant was you need SSE2 *or better*.  Your CPU is fine.

Then why after compiling pcsx2, I have no plugins. Was I supposed to download them separately? I never saw that in the directions that I read. I did get all of the dependencies I read I should get.

---

### Post by hikaricore on 2007-12-13
Did you actually download from the SVN like I and others suggested a week ago or are you still trying to compile the downloaded version that doesn't include plugins?

---

### Post by go_beep_yourself on 2007-12-13
> **hikaricore said:**
> Did you actually download from the SVN like I and others suggested a week ago or are you still trying to compile the downloaded version that doesn't include plugins?

I tried both. I'm about to try again.

---

### Post by go_beep_yourself on 2007-12-13
How can this be uninstalled? Is there anything similar to a "make uninstall" for this source code?

---

### Post by go_beep_yourself on 2007-12-13
It's working now. The problem is I used sudo to compile it before, and I have a mess of files on my system that don't work. I'd like to uninstall those with a script if possible.

---

### Post by go_beep_yourself on 2007-12-13
Also, to get this working, I did the advice from two other web forums.

[http://forums.gentoo.org/viewtopic-t-578192-highlight-pcsx2.html](http://forums.gentoo.org/viewtopic-t-578192-highlight-pcsx2.html)

The plugins are working. However I can't use pcsx2 because it is not finding my bios. I told it the directory that the bios files are in. I tried giving all the bios files execute permissions, and that didn't help. Has anyone experienced this problem?

---

### Post by barius on 2007-12-13
To my knowledge, during compilation all the files should be created under a subfolder named 'bin' in the same folder as you ran 'build.sh'.  So, there should be nothing to clean up in respect to compilation.  If you run 'sh build.sh clean' it will delete the compiled files, but only in their expected locations.  If you moved them, you're on your own.

After compilation, when you run the PCSX2 executable, it will by default create it's necessary .ini files and working folders in the home directory of the user running it.  If you ran it as root, you should find the files/folders under /root, if you ran it as yourself you should find them under /home/<your username>.  You can simply delete these files.

**I suggest using my guide, exactly, for at least the first build.**  Once you have a working build you can move the 'bin' folder wherever you like, but remember to modify the 'play.sh' script so that it cd's into the new location before running pcsx2.

---

### Post by kbless7 on 2008-01-12
So I've installed this and then used one of the cd/dvd plugins to rip a game iso image off the cd. I did 007 - Agent Under Fire. It played through the intro fine at 30 fps, but when I pressed start to go the main menu it just went to a black screen. Below is the terminal output, but nothing looks bad in it. Also after of while of waiting for the menu to come up, the intro stuff plays again. What's going on> Thanks for any help.

-Matt


matt@Matthew:~$ pcsx2/bin/play.sh

/home/matt/.themes/OS X Leopard/gtk-2.0/panel.rc:58: Unable to locate image file in pixmap_path: "Panel/panel-bg-trans.png"
/home/matt/.themes/OS X Leopard/gtk-2.0/panel.rc:61: Background image options specified without filename
/home/matt/.themes/OS X Leopard/gtk-2.0/panel.rc:58: Unable to locate image file in pixmap_path: "Panel/panel-bg-trans.png"
/home/matt/.themes/OS X Leopard/gtk-2.0/panel.rc:61: Background image options specified without filename
_openfile /home/matt/Desktop/Bond - Agent Under Fire.iso 0
detected blocksize = 2048
isoOpen: /home/matt/Desktop/Bond - Agent Under Fire.iso ok
offset = 0
blockofs = 24
blocksize = 2048
blocks = 796048
type = 2
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Disabling MRT depth writing
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing

EDIT: I noticed when I finally close out of the program the terminal displays this:
pcsx2/bin/play.sh: line 3:  6360 Segmentation fault      (core dumped) LD_LIBRARY_PATH="./" ./pcsx2

---

### Post by barius on 2008-01-14
007 - Agent Under Fire is not yet listed as 'playable' on their compatibility list, so you can expect numerous bugs.  There's nothing you can do but wait for a newer version of the emulator.  You can try asking about it on their forum, but most likely you'll just get this same answer.

The segmentation fault on Linux is a known issue, and there isn't a fix for it right now.  It doesn't seem to affect anything, except that it can cause your keyboard-repeat setting to be turned off.

---

### Post by bfoos on 2008-01-24
I've been trying to compile svn build 290 and get the following error on attempting to compile pcsx2...

```

GS.cpp: In function ‘int HasToExit()’:
GS.cpp:1495: error: ‘gsHasToExit’ was not declared in this scope
GS.cpp: In function ‘void* GSThreadProc(void*)’:
GS.cpp:1544: error: ‘gsHasToExit’ was not declared in this scope
make[1]: *** [GS.o] Error 1
make[1]: Leaving directory `/home/bfoos/pcsx2/pcsx2'
make: *** [install-recursive] Error 1
Error with building pcsx2

```

All of the plugins compile successfully, but not pcsx2. I'd have posted this on ngemu, but they have a pretty strict anti svn policy. Any help would be appreciated.

**EDIT**

SVN 292 compiles.

---

### Post by barius on 2008-02-17
> **bfoos said:**
> ... but they have a pretty strict anti svn policy. Any help would be appreciated.


I know you posted 3 weeks ago, but I thought I should mention that the PCSX2 forums actually accept SVN questions if they are in regards to the Linux version.  Only the Windows SVN is banned.  I think this is likely because the official Linux binary seems to have problems running on many of the various distros, so most people end up compiling from SVN anyways.

---

### Post by bfoos on 2008-02-17
> **barius said:**
> I know you posted 3 weeks ago, but I thought I should mention that the PCSX2 forums actually accept SVN questions if they are in regards to the Linux version.  Only the Windows SVN is banned.  I think this is likely because the official Linux binary seems to have problems running on many of the various distros, so most people end up compiling from SVN anyways.
Thanks for that clarification.

---

### Post by biosonik on 2008-03-17
Thank for the info, probably couldn't have installed this without it ;)

I have a problem though. PEOPS spu2 doesn't seem to work. I tried Zeroconf SPU although it was the usual aOSS awful sound.

I heard there was a way to compile peops spu to use ALSA. Does anyone know how to do this?

---

### Post by wingnux on 2008-03-18
This is what I get when trying to compile the latest svn using this tutorial:

> ../GS.h:114: error: ‘XF86VidModeModeInfo’ does not name a type
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/wingnux/Downloads/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

---

### Post by barius on 2008-03-24
> **wingnux said:**
> This is what I get when trying to compile the latest svn using this tutorial:

Is that a direct copy/paste of your output?  If so, there's something wrong with your download of the SVN, as you can see there is a space in the directory name 'opengl':

"Leaving directory `/home/wingnux/Downloads/pcsx2/plugins/gs/zerogs/o pengl/Linux'"

I suggest deleting what you have (except your BIOS files, obviously) and try again.

Also, I suggest that rather than modifying the steps to install into your 'Downloads' folder, that you simply copy/paste the commands and let it put the files directly in your home folder as some of the plugins are path length limited.  Once you have it compiled and it's working then you can play around with moving the 'bin' folder wherever you like.

---

### Post by barius on 2008-04-28
Updated for Hardy Heron.

---

### Post by Kernel_Krunch on 2008-06-06
> **barius said:**
> Updated for Hardy Heron.

wonderful thanks barius.

I have nvidia GeForce 5200, all i get when i try to open iso is "error opening GS plugin"  and nothing but 

```
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: *********
ZeroGS: OGL WARNING: Need GL_EXT_blend_equation_separate
ZeroGS: *********
ZeroGS: *********
ZeroGS: OGL WARNING: multiple render targets not supported, some effects might look bad
ZeroGS: *********
ZeroGS: Disabling MRT depth writing
```

do i need cg toolkit from nvidia i keep reading about on other forums?

edit: nvm my card is toooo old now :(

---

### Post by Mangust22 on 2008-07-21
How to install libasound2-dev?

There is some problem with repository... Dev-package is too old and unable to install it :(

---

