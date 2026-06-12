---
title: "Google Earth crash in Ubuntu"
date: 2007-12-15
forum: General Help
---

### Post by Tristanm1 on 2007-12-15
I tried to install Google Earth from both the repositories, and the official installer on the Google Earth site. Both result in the same crash. What happens is I start up Google Earth, and it appears for about a second, but almost immediately just stops running. No error, nothing. I have no clue what could be wrong, it just doesn't seem to work. If anyone knows a fix, please tell me.


Specs:
1.8GHz Turion 64 x2
1024MB Ram
Nvidia GeForce Go 6150
Ubuntu Gutsy x86

---

### Post by oldos2er on 2007-12-15
Are you using the restricted drivers for your Nvidia card?

---

### Post by Tristanm1 on 2007-12-15
Yes I am

---

### Post by Tyke91 on 2007-12-15
are you using the desktop effects?

---

### Post by Tristanm1 on 2007-12-15
I am using some.

---

### Post by Tristanm1 on 2007-12-16
I am using some desktop effects, but turning them off did not stop the crashes.

---

### Post by tgalati4 on 2007-12-18
Post after a crash:

>dmesg | tail

---

### Post by Mike Atnip on 2008-01-05
> **tgalati4 said:**
> Post after a crash:

>dmesg | tail
This is from another member.

[ 6203.328000] ACPI: Power Button (CM) [PWB]
[ 6204.568000] ACPI: Transitioning device [FAN] to D3
[ 6204.568000] ACPI: Transitioning device [FAN] to D3
[ 6204.568000] ACPI: Fan [FAN] (off)
[ 6204.896000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[ 6204.896000] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 6205.016000] ACPI: Thermal Zone [THRM] (38 C)
[ 6205.260000] ACPI: AC Adapter [ACAD] (on-line)
[ 6205.492000] ACPI: Battery Slot [BAT1] (battery present)
[ 6228.960000] eth0: no IPv6 routers present

I am having the same problem.
I am using Inspiron 1000, 2.2g Celeron, with a SIS 650 video card.  
Thanks for any help you can give.

---

### Post by darkpixel on 2008-04-27
Running google earth from the command line might give you a bit more info.
I am running into (possibly) the same issue.

I get the following:
darkpixel@hoth:~$ googleearth 
Google Earth has caught signal 4.

Stacktrace from glibc:
  ./googleearth-bin [0x804f3c7]
  ./googleearth-bin [0x804f8ed]
  [0xb7f31420]
  ./libbase.so(_ZN5earth17ScopedPerfSetting6createERK7QStringbb+0x64) [0xb70760f2]
  ./libbase.so(_ZN5earth17ScopedPerfSettingC2ERK7QStringbb+0x45) [0xb707618b]
  ./libbase.so(_ZN5earth20LogScopedPerfSettingC1ERK7QString+0x35) [0xb7076257]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application13setupQtLocaleEv+0x42) [0xb729fa60]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x31) [0xb729fda9]
  ./googleearth-bin(main+0x2a1) [0x8050b77]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70c5450]
  ./googleearth-bin [0x804f201]

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/darkpixel/.googleearth/crashlogs/crashlog-E90CD4E6.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

darkpixel@hoth:~$

---

### Post by puurokauha on 2008-04-27
I got a same problem as darkpixel. Google Earth worked fine on my Gutsy Gibbon installation. My dmesg | tail
```
[  114.661990] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[  114.666941] [fglrx] GART Table is not in FRAME_BUFFER range 
[  114.666950] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  114.666953] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[  114.759532] [fglrx] interrupt source 20008000 successfully enabled
[  114.759540] [fglrx] enable ID = 0x00000004
[  114.760413] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  114.761006] [fglrx] interrupt source 10000000 successfully enabled
[  114.761010] [fglrx] enable ID = 0x00000005
[  114.761780] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000

```

XP +3000
Ati Radeon 9800pro and restricted drivers
Hardy Heron

---

### Post by puurokauha on 2008-04-27
Oh, looks like you need SSE2 for google earth 4.3 in linux, but not in windows, wtf

[http://groups.google.com/group/earth-linux/browse_thread/thread/b2a5e6c3626e2937/b54ff765888edcc7]("http://groups.google.com/group/earth-linux/browse_thread/thread/b2a5e6c3626e2937/b54ff765888edcc7")

---

### Post by Maximiliano on 2008-05-17
Get Signal 4 error when install from medibuntu. Uninstall from synaptic, then install from googleearth and works perfect.
Have Athlon xp+2400

Me daba error Signal 4 cuando lo instale desde medibuntu. Desinstalar con synaptic e instalar desde googleearth y funciona perfecto.
Tengo Athlon xp+2400

---

### Post by skychris on 2008-05-17
my google earth crashes too but with this error :
```
extension "XFree86-DRI" missing on display
```

any idea?

... and I have an ATI card :)

---

