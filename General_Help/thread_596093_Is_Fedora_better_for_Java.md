---
title: "Is Fedora better for Java?"
date: 2007-10-29
forum: General Help
---

### Post by VHans on 2007-10-29
Until recently I used Fedora (FC6), Firefox and java plugin without any problem. Now that I moved to Ubuntu I can't get Java to work. Firefox crashes whenever I navigate to a page with a Java-applet (eg the Sun Java Plugin test page).
I tried removing Java completely from my PC and reinstalling, I tried several versions of Java, I tried IcedTea but the result is the same: ff crashes when loading a Java applet.
The only solution I see is to go back to Fedora. Or can Java work with Ubuntu?

---

### Post by taurus on 2007-10-29
How did you install java plugin in Ubuntu?  What versions have you tried?  Which release are you running?  Are you using x386 or x386_64?

---

### Post by VHans on 2007-10-29
Hello Taurus,
I am now trying Java 6 on Ubuntu 7.10 32bit Intel. I installed it using Synaptic: ff crashes (and Epiphany too) on Java applets.

Before I tried Java 1.5 and Java 1.4.
I tried installing via apt-get and I tried downloading Java from Sun's site. Neither worked.

Hans

---

### Post by taurus on 2007-10-29
I assume you did install sun-java6-plugin from synaptic.

---

### Post by VHans on 2007-10-29
I installed sun-java6-plugin from Synaptic indeed.

---

### Post by VHans on 2007-10-30
I tried again today:
1. use Synaptic to completely remove all packages related to java
2. completely remove Firefox
3. reboot (probably not needed, but you never know)
4. install Firefox (using Applications->Add/Remove)
5. install Sun Java 5 Plugin, Sun Java 5 Runtime, Sun Java 6 Web Start

Start Firefox: it doesn't find the Java plugin (about:plugins says no plugins installed)
I manually add the symlink in /usr/lib/mozilla/plugins -> same problem
I manually add the symlink in /usr/lib/firefox/plugins -> Java plugin is found

When testing the plugin on the sun web-site: Firefox terminates!

All this on Ubuntu 7.10 x86.

Time to move to another Linux distro or back to Windows?

---

### Post by yostral on 2007-10-30
> **VHans said:**
> Time to move to another Linux distro or back to Windows?
As you want...

---

### Post by SunnyRabbiera on 2007-10-30
odd... I should test this myself to see what happens.

---

### Post by VHans on 2007-10-30
> **yostral said:**
> As you want...

I don't want to, but if I can't get Java working then I'll have no choice. I don't understand what is going wrong and nobody seems to be able to help.
I uninstalled/reinstalled Java and Firefox several times and I still have the same problem.

---

### Post by VHans on 2007-10-30
> **SunnyRabbiera said:**
> odd... I should test this myself to see what happens.

Do you know if there is a way to check what goes wrong? Firefox just exits with no error message. How can I see what is causing the problem?

---

### Post by taurus on 2007-10-30
> **VHans said:**
> Do you know if there is a way to check what goes wrong? Firefox just exits with no error message. How can I see what is causing the problem?

Run it from a terminal to see what's wrong with it.

Applications -> Accessories -> Terminal
```
firefox
```

---

### Post by VHans on 2007-10-30
> **taurus said:**
> Run it from a terminal to see what's wrong with it.

Applications -> Accessories -> Terminal
```
firefox
```

I tried that but I don't get no error message. Is there a way to run ff with a 'debug' option?

I had a ff session open before I started a new session from the terminal. The first session crashed together with the one started from the terminal.

---

### Post by VHans on 2007-10-31
> **taurus said:**
> Run it from a terminal to see what's wrong with it.

Applications -> Accessories -> Terminal
```
firefox
```

Some more info: typing firefox from the terminal didn't return an error. But when I type the full path to firefox I get some feedback:

```
hans@lthvp:~$ /usr/lib/firefox/firefox
An irrecoverable stack overflow has occurred.
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7e74cbc, pid=18815, tid=3023256464
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x71cbc]  memcpy+0x1c
#
# An error report file with more information is saved as hs_err_pid18815.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
INTERNAL ERROR on Browser End: Plugin instance index out of bounds -28751

System error?:: Success
hans@lthvp:~$ 

```

Here is the hs_err_pid18815.log file:

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7e74cbc, pid=18815, tid=3023256464
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x71cbc]  memcpy+0x1c
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x08253800):  JavaThread "Thread-4" [_thread_in_native, id=18842]

siginfo:si_signo=11, si_errno=0, si_code=2, si_addr=0xb42e3000

Registers:
EAX=0xb535c001, EBX=0xb7f48ff4, ECX=0x0000023e, EDX=0x00000fff
ESP=0xb42b2770, EBP=0xb42b2794, ESI=0xb535c708, EDI=0xb42e3000
EIP=0xb7e74cbc, CR2=0xb42e3000, EFLAGS=0x00210217

Top of Stack: (sp=0xb42b2770)
0xb42b2770:   b7e5cfda b42e28f9 b535c001 00000fff
0xb42b2780:   b42e28f9 b42b27dc b7f48ff4 b42b28f8
0xb42b2790:   fbad2488 b42b27b8 b7e5cf51 083cbd10
0xb42b27a0:   b42b28f8 0000ffe6 0000000a 00000001
0xb42b27b0:   00000000 b7f48ff4 b42b27e0 b7e657ab
0xb42b27c0:   083cbd10 b42b28f8 0003ffe7 0000000a
0xb42b27d0:   00000001 b7d97ff4 b43328fc 00040000
0xb42b27e0:   b42b2838 b7d90f55 b42b28f8 0003ffe8 

Instructions: (pc=0xb7e74cbc)
0xb7e74cac:   8b 74 24 08 fc d1 e9 73 01 a4 d1 e9 73 02 66 a5
0xb7e74cbc:   f3 a5 89 c7 89 d6 8b 44 24 04 c3 90 90 90 90 90 

Stack: [0xb42e3000,0xb4334000),  sp=0xb42b2770,  free space=-195k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libc.so.6+0x71cbc]  memcpy+0x1c
C  [libc.so.6+0x59f51]  _IO_getline+0x41
C  [libc.so.6+0x627ab]  fgets_unlocked+0x5b
C  [libnss_files.so.2+0x2f55]
C  [libnss_files.so.2+0x374b]  _nss_files_gethostbyname2_r+0xcb

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  java.net.Inet6AddressImpl.lookupAllHostAddr(Ljava/lang/String;)[Ljava/net/InetAddress;+0
j  java.net.InetAddress$1.lookupAllHostAddr(Ljava/lang/String;)[Ljava/net/InetAddress;+4
j  java.net.InetAddress.getAddressFromNameService(Ljava/lang/String;Ljava/net/InetAddress;)Ljava/lang/Object;+17
j  java.net.InetAddress.getAllByName0(Ljava/lang/String;Ljava/net/InetAddress;Z)[Ljava/net/InetAddress;+37
j  java.net.InetAddress.getAllByName(Ljava/lang/String;Ljava/net/InetAddress;)[Ljava/net/InetAddress;+325
j  java.net.InetAddress.getAllByName(Ljava/lang/String;)[Ljava/net/InetAddress;+2
j  java.net.InetAddress.getByName(Ljava/lang/String;)Ljava/net/InetAddress;+1
j  com.sun.deploy.cache.Cache.getHostIP(Ljava/lang/String;)Ljava/net/InetAddress;+3
j  com.sun.deploy.cache.Cache.createHostEntry(Ljava/lang/String;)V+69
j  com.sun.deploy.cache.Cache.updateHostIPFile(Ljava/lang/String;)V+10
j  sun.plugin.AppletViewer.updateHostIPFile(Ljava/lang/String;)V+1
j  sun.applet.AppletPanel.getAccessControlContext(Ljava/net/URL;)Ljava/security/AccessControlContext;+203
j  sun.applet.AppletPanel.getClassLoader(Ljava/net/URL;Ljava/lang/String;)Lsun/applet/AppletClassLoader;+17
j  sun.applet.AppletPanel.createAppletThread()V+33
j  sun.applet.AppletPanel.init()V+89
j  sun.plugin.AppletViewer.createClassLoader()Z+107
j  sun.plugin.AppletViewer.appletInit()V+33
j  sun.plugin.viewer.LifeCycleManager.initAppletPanel(Lsun/plugin/AppletViewer;)V+20
j  sun.plugin.viewer.MNetscapePluginObject$Initer.run()V+4
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x083cb400 JavaThread "TimerQueue" daemon [_thread_blocked, id=18844]
=>0x08253800 JavaThread "Thread-4" [_thread_in_native, id=18842]
  0x08252400 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=18841]
  0x0824e000 JavaThread "Thread-3" [_thread_in_native, id=18840]
  0x0824c400 JavaThread "Thread-2" [_thread_blocked, id=18837]
  0x08239000 JavaThread "ConsoleWriterThread" daemon [_thread_blocked, id=18835]
  0x0821b800 JavaThread "AWT-EventQueue-1" [_thread_blocked, id=18834]
  0x08174000 JavaThread "AWT-Shutdown" [_thread_blocked, id=18833]
  0x08172400 JavaThread "traceMsgQueueThread" daemon [_thread_blocked, id=18830]
  0x0816bc00 JavaThread "CacheCleanUpThread" daemon [_thread_blocked, id=18829]
  0x08160800 JavaThread "AWT-XAWT" daemon [_thread_blocked, id=18828]
  0x080a4400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=18827]
  0x08086400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=18825]
  0x08084c00 JavaThread "CompilerThread0" daemon [_thread_blocked, id=18824]
  0x08083800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=18823]
  0x0807b800 JavaThread "Finalizer" daemon [_thread_blocked, id=18818]
  0x0807a800 JavaThread "Reference Handler" daemon [_thread_blocked, id=18817]
  0x08052400 JavaThread "main" [_thread_in_native, id=18815]

Other Threads:
  0x08079000 VMThread [id=18816]
  0x08087c00 WatcherThread [id=18826]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 960K, used 733K [0x8c0a0000, 0x8c1a0000, 0x8c580000)
  eden space 896K,  76% used [0x8c0a0000, 0x8c14b948, 0x8c180000)
  from space 64K,  73% used [0x8c180000, 0x8c18bc28, 0x8c190000)
  to   space 64K,   0% used [0x8c190000, 0x8c190000, 0x8c1a0000)
 tenured generation   total 4096K, used 2783K [0x8c580000, 0x8c980000, 0x900a0000)
   the space 4096K,  67% used [0x8c580000, 0x8c837c78, 0x8c837e00, 0x8c980000)
 compacting perm gen  total 12288K, used 1476K [0x900a0000, 0x90ca0000, 0x940a0000)
   the space 12288K,  12% used [0x900a0000, 0x90211378, 0x90211400, 0x90ca0000)
    ro space 8192K,  73% used [0x940a0000, 0x94682560, 0x94682600, 0x948a0000)
    rw space 12288K,  58% used [0x948a0000, 0x94f97448, 0x94f97600, 0x954a0000)

Dynamic libraries:
06000000-06417000 r-xp 00000000 fe:00 1033151    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so
06417000-06430000 rwxp 00417000 fe:00 1033151    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so
06430000-0684f000 rwxp 06430000 00:00 0 
08048000-0804b000 r-xp 00000000 fe:00 1033136    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/java_vm
0804b000-0804c000 rwxp 00002000 fe:00 1033136    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/java_vm
0804c000-08402000 rwxp 0804c000 00:00 0          [heap]
8c0a0000-8c1a0000 rwxp 8c0a0000 00:00 0 
8c1a0000-8c580000 rwxp 8c1a0000 00:00 0 
8c580000-8c980000 rwxp 8c580000 00:00 0 
8c980000-900a0000 rwxp 8c980000 00:00 0 
900a0000-90ca0000 rwxp 900a0000 00:00 0 
90ca0000-940a0000 rwxp 90ca0000 00:00 0 
940a0000-94683000 r-xs 00001000 fe:00 1033966    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
94683000-948a0000 rwxp 94683000 00:00 0 
948a0000-94f98000 rwxp 005e4000 fe:00 1033966    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
94f98000-954a0000 rwxp 94f98000 00:00 0 
954a0000-95579000 rwxp 00cdc000 fe:00 1033966    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
95579000-958a0000 rwxp 95579000 00:00 0 
958a0000-958a4000 r-xs 00db5000 fe:00 1033966    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
958a4000-95ca0000 rwxp 958a4000 00:00 0 
b3f12000-b3fa3000 rwxs 00000000 00:09 8912915    /SYSV00000000 (deleted)
b3fa3000-b4034000 rwxp b3fa3000 00:00 0 
b40c3000-b4165000 rwxs 00000000 00:09 8847377    /SYSV00000000 (deleted)
b41a1000-b41a4000 ---p b41a1000 00:00 0 
b41a4000-b4283000 rwxp b41a4000 00:00 0 
b4283000-b42e3000 rwxs 00000000 00:09 8814606    /SYSV00000000 (deleted)
b42e3000-b42e4000 rwxp b42e3000 00:00 0 
b42e4000-b42e6000 ---p b42e4000 00:00 0 
b42e6000-b4334000 rwxp b42e6000 00:00 0 
b4334000-b4337000 ---p b4334000 00:00 0 
b4337000-b4385000 rwxp b4337000 00:00 0 
b4385000-b4388000 ---p b4385000 00:00 0 
b4388000-b43d6000 rwxp b4388000 00:00 0 
b43d6000-b43d9000 ---p b43d6000 00:00 0 
b43d9000-b4427000 rwxp b43d9000 00:00 0 
b4427000-b442a000 ---p b4427000 00:00 0 
b442a000-b4478000 rwxp b442a000 00:00 0 
b4478000-b4489000 r-xp 00000000 fe:00 937020     /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
b4489000-b448f000 r-xs 00000000 fe:00 8243460    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b448f000-b44ce000 rwxp b448f000 00:00 0 
b44cf000-b44d1000 r-xp 00000000 fe:00 11288803   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b44d1000-b44d2000 rwxp 00001000 fe:00 11288803   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b44d2000-b44d3000 r-xs 00000000 fe:00 8243458    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b44d3000-b44d5000 r-xs 00000000 fe:00 8243457    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b44d5000-b44d6000 r-xs 00000000 fe:00 8243456    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b44d6000-b44d7000 r-xs 00000000 fe:00 8243455    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b44d7000-b44db000 r-xs 00000000 fe:00 8243454    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b44db000-b44dc000 r-xs 00000000 fe:00 8243453    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b44dc000-b44df000 r-xs 00000000 fe:00 8243451    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b44df000-b44e0000 r-xs 00000000 fe:00 8243450    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b44e0000-b44e2000 r-xs 00000000 fe:00 8243449    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b44e2000-b44e5000 r-xs 00000000 fe:00 8243448    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b44e5000-b44e7000 r-xs 00000000 fe:00 8243447    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b44e7000-b44e8000 r-xs 00000000 fe:00 8243446    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b44e8000-b44ea000 r-xs 00000000 fe:00 8243445    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b44ea000-b44f0000 r-xs 00000000 fe:00 8242093    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b44f0000-b44f2000 r-xs 00000000 fe:00 8243442    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b44f2000-b44f4000 r-xs 00000000 fe:00 8243443    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b44f4000-b44fc000 r-xs 00000000 fe:00 8243444    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b44fc000-b4502000 r-xs 00000000 fe:00 8243468    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4502000-b4503000 r-xs 00000000 fe:00 8243471    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4503000-b451a000 r-xs 00000000 fe:00 8241751    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b451a000-b451c000 r-xs 00000000 fe:00 8243474    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b451c000-b4522000 r-xs 00000000 fe:00 8243476    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4522000-b4525000 r-xs 00000000 fe:00 8243478    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4525000-b4529000 r-xs 00000000 fe:00 8243480    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4529000-b452b000 r-xs 00000000 fe:00 8243523    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b452b000-b452c000 r-xs 00000000 fe:00 8243515    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b452c000-b452d000 r-xs 00000000 fe:00 8243511    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b452d000-b452e000 r-xs 00000000 fe:00 8241745    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b452e000-b4530000 r-xs 00000000 fe:00 8241737    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4530000-b4533000 r-xs 00000000 fe:00 8243518    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4533000-b453c000 r-xs 00000000 fe:00 8241735    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b453c000-b453f000 r-xs 00000000 fe:00 8243520    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b453f000-b4540000 r-xs 00000000 fe:00 8243475    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4540000-b4542000 r-xs 00000000 fe:00 8243526    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4542000-b4543000 r-xs 00000000 fe:00 8243473    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4543000-b4548000 r-xs 00000000 fe:00 8243472    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4548000-b454c000 r-xs 00000000 fe:00 8243528    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b454c000-b454e000 r-xs 00000000 fe:00 8241353    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b454e000-b4551000 r-xs 00000000 fe:00 8243512    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4551000-b4552000 r-xs 00000000 fe:00 8243470    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b4552000-b4553000 r-xs 00000000 fe:00 8241725    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b4553000-b4555000 r-xs 00000000 fe:00 8243516    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4555000-b455b000 r-xs 00000000 fe:00 8241724    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b455b000-b4561000 r-xs 00000000 fe:00 8243524    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4561000-b4569000 r-xs 00000000 fe:00 8243466    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b4569000-b4572000 r-xs 00000000 fe:00 1295494    /usr/share/fonts/X11/Type1/c0649bt_.pfb
b4572000-b457c000 r-xs 00000000 fe:00 1295507    /usr/share/fonts/X11/Type1/c0582bt_.pfb
b457c000-b459a000 r-xs 00000000 fe:00 7143589    /usr/share/fonts/type1/gsfonts/b018015l.pfb
b459a000-b45bd000 r-xs 00000000 fe:00 7143590    /usr/share/fonts/type1/gsfonts/b018032l.pfb
b45bd000-b45e7000 r-xs 00000000 fe:00 7143615    /usr/share/fonts/type1/gsfonts/p052023l.pfb
b45e7000-b45fe000 r-xs 00000000 fe:00 7143587    /usr/share/fonts/type1/gsfonts/a010035l.pfb
b45fe000-b4615000 r-xs 00000000 fe:00 7143584    /usr/share/fonts/type1/gsfonts/a010013l.pfb
b4615000-b462b000 r-xs 00000000 fe:00 7143585    /usr/share/fonts/type1/gsfonts/a010015l.pfb
b462b000-b4656000 r-xs 00000000 fe:00 7143614    /usr/share/fonts/type1/gsfonts/p052004l.pfb
b4656000-b4679000 r-xs 00000000 fe:00 7143588    /usr/share/fonts/type1/gsfonts/b018012l.pfb
b4679000-b4686000 r-xs 00000000 fe:00 7143618    /usr/share/fonts/type1/gsfonts/z003034l.pfb
b4686000-b46a6000 r-xs 00000000 fe:00 7143591    /usr/share/fonts/type1/gsfonts/b018035l.pfb
b46a6000-b46d2000 r-xs 00000000 fe:00 7143613    /usr/share/fonts/type1/gsfonts/p052003l.pfb
b46d2000-b46d6000 r-xs 00000000 fe:00 8241723    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b46d6000-b46e0000 r-xs 00000000 fe:00 1295499    /usr/share/fonts/X11/Type1/c0611bt_.pfb
b46e0000-b46e9000 r-xs 00000000 fe:00 1295500    /usr/share/fonts/X11/Type1/c0632bt_.pfb
b46e9000-b4715000 r-xs 00000000 fe:00 7143616    /usr/share/fonts/type1/gsfonts/p052024l.pfb
b4715000-b4737000 r-xs 00000000 fe:00 7143606    /usr/share/fonts/type1/gsfonts/n021004l.pfb
b4737000-b4750000 r-xs 00000000 fe:00 7143604    /usr/share/fonts/type1/gsfonts/n019064l.pfb
b4750000-b4768000 r-xs 00000000 fe:00 7143601    /usr/share/fonts/type1/gsfonts/n019043l.pfb
b4768000-b478b000 r-xs 00000000 fe:00 7143605    /usr/share/fonts/type1/gsfonts/n021003l.pfb
b478b000-b47ac000 r-xs 00000000 fe:00 7143608    /usr/share/fonts/type1/gsfonts/n021024l.pfb
b47ac000-b47cf000 r-xs 00000000 fe:00 7143611    /usr/share/fonts/type1/gsfonts/n022023l.pfb
b47cf000-b47e9000 r-xs 00000000 fe:00 7143599    /usr/share/fonts/type1/gsfonts/n019023l.pfb
b47e9000-b4800000 r-xs 00000000 fe:00 7143602    /usr/share/fonts/type1/gsfonts/n019044l.pfb
b4800000-b4822000 r-xs 00000000 fe:00 7143609    /usr/share/fonts/type1/gsfonts/n022003l.pfb
b4822000-b483b000 r-xs 00000000 fe:00 7143600    /usr/share/fonts/type1/gsfonts/n019024l.pfb
b483b000-b4853000 r-xs 00000000 fe:00 7143603    /usr/share/fonts/type1/gsfonts/n019063l.pfb
b4853000-b4877000 r-xs 00000000 fe:00 7143607    /usr/share/fonts/type1/gsfonts/n021023l.pfb
b4877000-b488f000 r-xs 00000000 fe:00 7143598    /usr/share/fonts/type1/gsfonts/n019004l.pfb
b488f000-b48b5000 r-xs 00000000 fe:00 7143612    /usr/share/fonts/type1/gsfonts/n022024l.pfb
b48b5000-b48de000 r-xs 00000000 fe:00 7143610    /usr/share/fonts/type1/gsfonts/n022004l.pfb
b48de000-b4944000 rwxp b48de000 00:00 0 
b4946000-b4949000 r-xs 00000000 fe:00 8243464    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b4949000-b4952000 r-xs 00000000 fe:00 1295508    /usr/share/fonts/X11/Type1/c0633bt_.pfb
b4952000-b496c000 r-xs 00000000 fe:00 7143597    /usr/share/fonts/type1/gsfonts/n019003l.pfb
b496c000-b4973000 r-xp 00000000 fe:00 1033165    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnio.so
b4973000-b4974000 rwxp 00006000 fe:00 1033165    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnio.so
b4974000-b4987000 r-xp 00000000 fe:00 1033164    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnet.so
b4987000-b4988000 rwxp 00013000 fe:00 1033164    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnet.so
b4988000-b499a000 r-xp 00000000 fe:00 983733     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b499a000-b499b000 rwxp 00012000 fe:00 983733     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b499b000-b49b9000 r-xp 00000000 fe:00 885934     /usr/lib/libexpat.so.1.0.0
b49b9000-b49bb000 rwxp 0001e000 fe:00 885934     /usr/lib/libexpat.so.1.0.0
b49bb000-b49dd000 r-xp 00000000 fe:00 888803     /usr/lib/libpng12.so.0.15.0
b49dd000-b49de000 rwxp 00021000 fe:00 888803     /usr/lib/libpng12.so.0.15.0
b49de000-b49f2000 r-xp 00000000 fe:00 885790     /usr/lib/libz.so.1.2.3.3
b49f2000-b49f3000 rwxp 00013000 fe:00 885790     /usr/lib/libz.so.1.2.3.3
b49f3000-b4a5f000 r-xp 00000000 fe:00 885936     /usr/lib/libfreetype.so.6.3.16
b4a5f000-b4a63000 rwxp 0006b000 fe:00 885936     /usr/lib/libfreetype.so.6.3.16
b4a63000-b4a90000 r-xp 00000000 fe:00 885503     /usr/lib/libpangoft2-1.0.so.0.1800.2
b4a90000-b4a91000 rwxp 0002c000 fe:00 885503     /usr/lib/libpangoft2-1.0.so.0.1800.2
b4a91000-b4a96000 r-xp 00000000 fe:00 885913     /usr/lib/libXrandr.so.2.1.0
b4a96000-b4a97000 rwxp 00005000 fe:00 885913     /usr/lib/libXrandr.so.2.1.0
b4a97000-b4aba000 r-xp 00000000 fe:00 885293     /usr/lib/libfontconfig.so.1.2.0
b4aba000-b4ac2000 rwxp 00023000 fe:00 885293     /usr/lib/libfontconfig.so.1.2.0
b4ac2000-b4b37000 r-xp 00000000 fe:00 885571     /usr/lib/libcairo.so.2.11.5
b4b37000-b4b39000 rwxp 00074000 fe:00 885571     /usr/lib/libcairo.so.2.11.5
b4b39000-b4bf5000 r-xp 00000000 fe:00 885769     /usr/lib/libglib-2.0.so.0.1400.1
b4bf5000-b4bf6000 rwxp 000bc000 fe:00 885769     /usr/lib/libglib-2.0.so.0.1400.1
b4bf6000-b4bf9000 r-xp 00000000 fe:00 885770     /usr/lib/libgmodule-2.0.so.0.1400.1
b4bf9000-b4bfa000 rwxp 00002000 fe:00 885770     /usr/lib/libgmodule-2.0.so.0.1400.1
b4bfa000-b4c34000 r-xp 00000000 fe:00 885771     /usr/lib/libgobject-2.0.so.0.1400.1
b4c34000-b4c35000 rwxp 0003a000 fe:00 885771     /usr/lib/libgobject-2.0.so.0.1400.1
b4c35000-b4c70000 r-xp 00000000 fe:00 885499     /usr/lib/libpango-1.0.so.0.1800.2
b4c70000-b4c72000 rwxp 0003b000 fe:00 885499     /usr/lib/libpango-1.0.so.0.1800.2
b4c72000-b4cf6000 r-xp 00000000 fe:00 885530     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b4cf6000-b4cf9000 rwxp 00084000 fe:00 885530     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b4cf9000-b5076000 r-xp 00000000 fe:00 885863     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b5076000-b507d000 rwxp 0037c000 fe:00 885863     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b507d000-b507e000 rwxp b507d000 00:00 0 
b507e000-b5081000 ---p b507e000 00:00 0 
b5081000-b50cf000 rwxp b5081000 00:00 0 
b50cf000-b50d2000 ---p b50cf000 00:00 0 
b50d2000-b5120000 rwxp b50d2000 00:00 0 
b5120000-b5123000 ---p b5120000 00:00 0 
b5123000-b5171000 rwxp b5123000 00:00 0 
b5171000-b5174000 ---p b5171000 00:00 0 
b5174000-b51c2000 rwxp b5174000 00:00 0 
b51c2000-b5272000 r-xp 00000000 fe:00 886124     /usr/lib/libstdc++.so.5.0.7
b5272000-b5277000 rwxp 000af000 fe:00 886124     /usr/lib/libstdc++.so.5.0.7
b5277000-b527c000 rwxp b5277000 00:00 0 
b527c000-b5282000 r-xs 00000000 fe:00 8243460    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5282000-b5283000 r-xs 00000000 fe:00 8243458    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b5283000-b5285000 r-xs 00000000 fe:00 8243457    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5285000-b5286000 r-xs 00000000 fe:00 8243456    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5286000-b5287000 r-xs 00000000 fe:00 8243455    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5287000-b528b000 r-xs 00000000 fe:00 8243454    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b528b000-b528c000 r-xs 00000000 fe:00 8243453    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b528c000-b528f000 r-xs 00000000 fe:00 8243451    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b528f000-b5290000 r-xs 00000000 fe:00 8243450    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5290000-b5292000 r-xs 00000000 fe:00 8243449    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b5292000-b5295000 r-xs 00000000 fe:00 8243448    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5295000-b5297000 r-xs 00000000 fe:00 8243447    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b5297000-b5298000 r-xs 00000000 fe:00 8243446    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b5298000-b529a000 r-xs 00000000 fe:00 8243445    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b529a000-b52a0000 r-xs 00000000 fe:00 8242093    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b52a0000-b52a2000 r-xs 00000000 fe:00 8243442    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b52a2000-b52a4000 r-xs 00000000 fe:00 8243443    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b52a4000-b52ac000 r-xs 00000000 fe:00 8243444    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b52ac000-b52b2000 r-xs 00000000 fe:00 8243468    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b52b2000-b52b3000 r-xs 00000000 fe:00 8243471    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b52b3000-b52ca000 r-xs 00000000 fe:00 8241751    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b52ca000-b52cc000 r-xs 00000000 fe:00 8243474    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b52cc000-b52d2000 r-xs 00000000 fe:00 8243476    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b52d2000-b52d5000 r-xs 00000000 fe:00 8243478    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b52d5000-b52d9000 r-xs 00000000 fe:00 8243480    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b52d9000-b52db000 r-xs 00000000 fe:00 8243523    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b52db000-b52dc000 r-xs 00000000 fe:00 8243515    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b52dc000-b52dd000 r-xs 00000000 fe:00 8243511    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b52dd000-b52de000 r-xs 00000000 fe:00 8241745    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b52de000-b52e0000 r-xs 00000000 fe:00 8241737    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b52e0000-b52e3000 r-xs 00000000 fe:00 8243518    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b52e3000-b52ec000 r-xs 00000000 fe:00 8241735    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b52ec000-b52ef000 r-xs 00000000 fe:00 8243520    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b52ef000-b52f0000 r-xs 00000000 fe:00 8243475    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b52f0000-b52f2000 r-xs 00000000 fe:00 8243526    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b52f2000-b52f3000 r-xs 00000000 fe:00 8243473    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b52f3000-b52f8000 r-xs 00000000 fe:00 8243472    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b52f8000-b52fc000 r-xs 00000000 fe:00 8243528    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b52fc000-b52fe000 r-xs 00000000 fe:00 8241353    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b52fe000-b5304000 r-xs 00000000 fe:00 8241724    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b5304000-b530a000 r-xs 00000000 fe:00 8243524    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b530a000-b5312000 r-xs 00000000 fe:00 8243466    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b5312000-b5314000 r-xp 00000000 fe:00 885911     /usr/lib/libXinerama.so.1.0.0
b5314000-b5315000 rwxp 00001000 fe:00 885911     /usr/lib/libXinerama.so.1.0.0
b5315000-b532e000 r-xp 00000000 fe:00 885774     /usr/lib/libatk-1.0.so.0.2009.1
b532e000-b5330000 rwxp 00018000 fe:00 885774     /usr/lib/libatk-1.0.so.0.2009.1
b5330000-b5338000 r-xp 00000000 fe:00 885501     /usr/lib/libpangocairo-1.0.so.0.1800.2
b5338000-b5339000 rwxp 00007000 fe:00 885501     /usr/lib/libpangocairo-1.0.so.0.1800.2
b5339000-b5350000 r-xp 00000000 fe:00 885532     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b5350000-b5351000 rwxp 00016000 fe:00 885532     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b5351000-b535b000 r-xp 00000000 fe:00 4702268    /lib/libgcc_s.so.1
b535b000-b535c000 rwxp 0000a000 fe:00 4702268    /lib/libgcc_s.so.1
b535c000-b535d000 rwxp b535c000 00:00 0 
b535d000-b5362000 r-xs 00000000 fe:00 8241659    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b5362000-b5363000 r-xp 00000000 fe:00 1097935    /usr/lib/gconv/ISO8859-1.so
b5363000-b5365000 rwxp 00000000 fe:00 1097935    /usr/lib/gconv/ISO8859-1.so
b5365000-b536c000 r-xs 00000000 fe:00 885763     /usr/lib/gconv/gconv-modules.cache
b536c000-b536f000 ---p b536c000 00:00 0 
b536f000-b53bd000 rwxp b536f000 00:00 0 
b53bd000-b53c1000 r-xp 00000000 fe:00 885905     /usr/lib/libXfixes.so.3.1.0
b53c1000-b53c2000 rwxp 00003000 fe:00 885905     /usr/lib/libXfixes.so.3.1.0
b53c2000-b53c9000 r-xp 00000000 fe:00 885567     /usr/lib/libXrender.so.1.3.0
b53c9000-b53ca000 rwxp 00006000 fe:00 885567     /usr/lib/libXrender.so.1.3.0
b53ca000-b53d2000 r-xp 00000000 fe:00 885907     /usr/lib/libXcursor.so.1.0.2
b53d2000-b53d3000 rwxp 00007000 fe:00 885907     /usr/lib/libXcursor.so.1.0.2
b53d3000-b53d4000 r-xs 00000000 fe:00 8243467    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b53d4000-b53d6000 r-xp 00000000 fe:00 885514     /usr/lib/libXdamage.so.1.1.0
b53d6000-b53d7000 rwxp 00001000 fe:00 885514     /usr/lib/libXdamage.so.1.1.0
b53d7000-b53d9000 r-xp 00000000 fe:00 885509     /usr/lib/libXcomposite.so.1.0.0
b53d9000-b53da000 rwxp 00001000 fe:00 885509     /usr/lib/libXcomposite.so.1.0.0
b53da000-b53e2000 r-xp 00000000 fe:00 1033198    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libdeploy.so
b53e2000-b53e3000 rwxp 00007000 fe:00 1033198    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libdeploy.so
b53e3000-b53e6000 r-xs 00000000 fe:00 8243512    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b53e6000-b53ea000 r-xs 00000000 fe:00 8241723    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b53ea000-b53ed000 r-xs 00000000 fe:00 8243464    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b53ed000-b53f2000 r-xs 00000000 fe:00 8241659    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b53f2000-b53f5000 ---p b53f2000 00:00 0 
b53f5000-b5443000 rwxp b53f5000 00:00 0 
b5443000-b54c1000 r-xp 00000000 fe:00 1033183    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libfontmanager.so
b54c1000-b54cb000 rwxp 0007e000 fe:00 1033183    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libfontmanager.so
b54cb000-b54d0000 rwxp b54cb000 00:00 0 
b54d0000-b54e0000 r-xp 00000000 fe:00 1033195    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjavaplugin_jni.so
b54e0000-b54e2000 rwxp 00010000 fe:00 1033195    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjavaplugin_jni.so
b54e2000-b54f5000 rwxp b54e2000 00:00 0 
b54f5000-b54f9000 r-xp 00000000 fe:00 885560     /usr/lib/libXdmcp.so.6.0.0
b54f9000-b54fa000 rwxp 00003000 fe:00 885560     /usr/lib/libXdmcp.so.6.0.0
b54fa000-b54fc000 r-xp 00000000 fe:00 885556     /usr/lib/libXau.so.6.0.0
b54fc000-b54fd000 rwxp 00001000 fe:00 885556     /usr/lib/libXau.so.6.0.0
b54fd000-b5504000 r-xp 00000000 fe:00 885909     /usr/lib/libXi.so.6.0.0
b5504000-b5505000 rwxp 00006000 fe:00 885909     /usr/lib/libXi.so.6.0.0
b5505000-b5509000 r-xp 00000000 fe:00 886565     /usr/lib/libXtst.so.6.1.0
b5509000-b550a000 rwxp 00004000 fe:00 886565     /usr/lib/libXtst.so.6.1.0
b550a000-b55f7000 r-xp 00000000 fe:00 885565     /usr/lib/libX11.so.6.2.0
b55f7000-b55fb000 rwxp 000ed000 fe:00 885565     /usr/lib/libX11.so.6.2.0
b55fb000-b5608000 r-xp 00000000 fe:00 885903     /usr/lib/libXext.so.6.4.0
b5608000-b5609000 rwxp 0000d000 fe:00 885903     /usr/lib/libXext.so.6.4.0
b5609000-b560b000 r-xs 00000000 fe:00 8243516    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b560b000-b5619000 r-xs 00284000 fe:00 1033368    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/deploy.jar
b5619000-b5657000 r-xp 00000000 fe:00 1033178    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/xawt/libmawt.so
b5657000-b5659000 rwxp 0003e000 fe:00 1033178    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/xawt/libmawt.so
b5659000-b565a000 rwxp b5659000 00:00 0 
b565a000-b5720000 r-xp 00000000 fe:00 1033174    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libmlib_image.so
b5720000-b5721000 rwxp 000c5000 fe:00 1033174    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libmlib_image.so
b5721000-b579c000 r-xp 00000000 fe:00 1033175    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libawt.so
b579c000-b57a3000 rwxp 0007b000 fe:00 1033175    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libawt.so
b57a3000-b57c7000 rwxp b57a3000 00:00 0 
b57c7000-b57cf000 r-xs 000e2000 fe:00 1033370    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/plugin.jar
b57cf000-b57ff000 rwxp b57cf000 00:00 0 
b57ff000-b597b000 r-xs 02c8f000 fe:00 1033369    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/rt.jar
b597b000-b597c000 ---p b597b000 00:00 0 
b597c000-b59fc000 rwxp b597c000 00:00 0 
b59fc000-b59ff000 ---p b59fc000 00:00 0 
b59ff000-b5a4d000 rwxp b59ff000 00:00 0 
b5a4d000-b5a50000 ---p b5a4d000 00:00 0 
b5a50000-b5ace000 rwxp b5a50000 00:00 0 
b5ace000-b5ad1000 ---p b5ace000 00:00 0 
b5ad1000-b5b1f000 rwxp b5ad1000 00:00 0 
b5b1f000-b5b22000 ---p b5b1f000 00:00 0 
b5b22000-b5b70000 rwxp b5b22000 00:00 0 
b5b70000-b5b73000 ---p b5b70000 00:00 0 
b5b73000-b5bc1000 rwxp b5b73000 00:00 0 
b5bc1000-b5bc2000 ---p b5bc1000 00:00 0 
b5bc2000-b5c49000 rwxp b5bc2000 00:00 0 
b5c49000-b5c63000 rwxp b5c49000 00:00 0 
b5c63000-b5c66000 rwxp b5c63000 00:00 0 
b5c66000-b5c81000 rwxp b5c66000 00:00 0 
b5c81000-b5c82000 rwxp b5c81000 00:00 0 
b5c82000-b5c83000 rwxp b5c82000 00:00 0 
b5c83000-b5c86000 rwxp b5c83000 00:00 0 
b5c86000-b5ca1000 rwxp b5c86000 00:00 0 
b5ca1000-b5ca7000 rwxp b5ca1000 00:00 0 
b5ca7000-b5cc1000 rwxp b5ca7000 00:00 0 
b5cc1000-b5cd0000 rwxp b5cc1000 00:00 0 
b5cd0000-b5d4c000 rwxp b5cd0000 00:00 0 
b5d4c000-b5e4c000 rwxp b5d4c000 00:00 0 
b5e4c000-b7d4c000 rwxp b5e4c000 00:00 0 
b7d4c000-b7d5b000 r-xp 00000000 fe:00 1033160    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libzip.so
b7d5b000-b7d5d000 rwxp 0000e000 fe:00 1033160    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libzip.so
b7d5d000-b7d80000 r-xp 00000000 fe:00 1033157    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjava.so
b7d80000-b7d82000 rwxp 00023000 fe:00 1033157    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjava.so
b7d82000-b7d8d000 r-xp 00000000 fe:00 1033156    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libverify.so
b7d8d000-b7d8e000 rwxp 0000b000 fe:00 1033156    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libverify.so
b7d8e000-b7d97000 r-xp 00000000 fe:00 4702236    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7d97000-b7d99000 rwxp 00008000 fe:00 4702236    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7d99000-b7da1000 r-xp 00000000 fe:00 4702238    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7da1000-b7da3000 rwxp 00007000 fe:00 4702238    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7da3000-b7daa000 r-xp 00000000 fe:00 4702234    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7daa000-b7dac000 rwxp 00006000 fe:00 4702234    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7dac000-b7dc0000 r-xp 00000000 fe:00 4702233    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7dc0000-b7dc2000 rwxp 00013000 fe:00 4702233    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7dc2000-b7dc4000 rwxp b7dc2000 00:00 0 
b7dc4000-b7dc5000 r-xs 00000000 fe:00 8243470    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b7dc5000-b7dcc000 rwxp b7dc5000 00:00 0 
b7dcc000-b7dd4000 rwxs 00000000 fe:00 3752273    /tmp/hsperfdata_hans/18815
b7dd4000-b7ddb000 r-xp 00000000 fe:00 4702243    /lib/tls/i686/cmov/librt-2.6.1.so
b7ddb000-b7ddd000 rwxp 00006000 fe:00 4702243    /lib/tls/i686/cmov/librt-2.6.1.so
b7ddd000-b7e00000 r-xp 00000000 fe:00 4702231    /lib/tls/i686/cmov/libm-2.6.1.so
b7e00000-b7e02000 rwxp 00023000 fe:00 4702231    /lib/tls/i686/cmov/libm-2.6.1.so
b7e02000-b7e03000 rwxp b7e02000 00:00 0 
b7e03000-b7f47000 r-xp 00000000 fe:00 4702227    /lib/tls/i686/cmov/libc-2.6.1.so
b7f47000-b7f48000 r-xp 00143000 fe:00 4702227    /lib/tls/i686/cmov/libc-2.6.1.so
b7f48000-b7f4a000 rwxp 00144000 fe:00 4702227    /lib/tls/i686/cmov/libc-2.6.1.so
b7f4a000-b7f4d000 rwxp b7f4a000 00:00 0 
b7f4d000-b7f4f000 r-xp 00000000 fe:00 4702230    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f4f000-b7f51000 rwxp 00001000 fe:00 4702230    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f51000-b7f52000 rwxp b7f51000 00:00 0 
b7f52000-b7f66000 r-xp 00000000 fe:00 4702241    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f66000-b7f68000 rwxp 00013000 fe:00 4702241    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f68000-b7f6a000 rwxp b7f68000 00:00 0 
b7f6a000-b7f6b000 r-xs 00000000 fe:00 8241725    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b7f6b000-b7f6c000 r-xs 00000000 fe:00 8243467    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f6c000-b7f71000 rwxp b7f6c000 00:00 0 
b7f71000-b7f77000 r-xp 00000000 fe:00 1033145    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/native_threads/libhpi.so
b7f77000-b7f78000 rwxp 00006000 fe:00 1033145    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/native_threads/libhpi.so
b7f78000-b7f79000 rwxp b7f78000 00:00 0 
b7f79000-b7f7a000 r-xp b7f79000 00:00 0 
b7f7a000-b7f7c000 rwxp b7f7a000 00:00 0 
b7f7c000-b7f96000 r-xp 00000000 fe:00 4703684    /lib/ld-2.6.1.so
b7f96000-b7f98000 rwxp 00019000 fe:00 4703684    /lib/ld-2.6.1.so
bfed7000-bfeda000 ---p bfed7000 00:00 0 
bfeda000-bff27000 rwxp bfeda000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -DtrustProxy=true -Xverify:remote -Xbootclasspath/a:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/plugin.jar:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/deploy.jar:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=160_03 -Djavaplugin.version=1.6.0_03 -Djavaplugin.vm.options=-DtrustProxy=true -Xverify:remote -Djava.class.path=/usr/lib/jvm/java-6-sun-1.6.0.03/jre/classes -Xbootclasspath/a:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/plugin.jar:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/deploy.jar:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=160_03 -Djavaplugin.version=1.6.0_03 
java_command: <unknown>
Launcher Type: generic

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
PATH=/home/hans/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin
USERNAME=hans
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386:/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mre/mre
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3b29c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3b29c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x309ec0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x309ec0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x309ec0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30bef0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR2: [libjvm.so+0x30bef0], sa_mask[0]=0x00000000, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 16378, NOFILE 1024, AS infinity
load average:0.41 0.17 0.22

CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 13 stepping 6, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 2075352k(1150060k free), swap 4796408k(4796408k free)

vm_info: Java HotSpot(TM) Client VM (1.6.0_03-b05) for linux-x86, built on Sep 24 2007 22:45:46 by "java_re" with gcc 3.2.1-7a (J2SE release)

```

Can this help?

---

### Post by VHans on 2007-11-08
Problem finally solved by cleaning up my /etc/hosts file.

---

