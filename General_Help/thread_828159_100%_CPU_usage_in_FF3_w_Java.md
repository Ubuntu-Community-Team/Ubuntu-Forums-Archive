---
title: "100% CPU usage in FF3 w/ Java"
date: 2008-06-13
forum: General Help
---

### Post by detroit/zero on 2008-06-13
I'm having some issues with FF3 and using Java to play Yahoo games.

I'm using a fresh install of Hardy Heron on a Toshiba Satellite a135 w/ Intel 1.73GHz, 1GB RAM, Intel 945 onboard graphics, and onboard sound.

LSPCI output:```
zero@zero-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```Because of my addiction to Yahoo Pool, I had to uninstall whatever Java (Iced Tea?) ships as standard with a fresh install of 8.04 and install JRE 1.5 with plugins, etc. (1.5 is the only version that works with Yahoo and Pogo games.)

When I have FF3 running, everything is normal; i.e., no heavy CPU load or abnormal behavior. As soon as I log into Yahoo games and Java loads to run the game apps, my CPU load hovers between 80% and 100%, and the memory load is increased as well. 

HTOP says that it is indeed FF3 using all the CPU and that Java is running normally:
[CENTER][IMG]http://img80.imageshack.us/img80/8418/screenshot1ec6.png[/IMG]
[/CENTER]
 
You can see that FF3, highlighted, is using 99.7 of the CPU, but Java not so much.. The system monitor graph I keep in my top panel is maxxed out, as well.

The strange thing is: There's no noticible system lag or effect on performance. I still have Compiz running with a cube, animations, screenlets, AWN, etc. Everything seems to be OK despite what HTOP and my system monitors tell me.

Anybody have any ideas for me? If you need more info, I'll be glad to post it.

---

### Post by Pjotr123 on 2008-06-13
I play chess on Yahoo Games, and it works fine with Sun Java 1.6. Maybe you could try 1.6 instead of 1.5?

---

### Post by detroit/zero on 2008-06-13
> **Pjotr123 said:**
> I play chess on Yahoo Games, and it works fine with Sun Java 1.6. Maybe you could try 1.6 instead of 1.5?

That's strange - I could never get 1.6 to work right.. It would get stuck in a seemingly endless "loading applet" when the game lobby window comes up. I'll give it one more try and post what happens..

---

### Post by bollix47 on 2008-06-13
Are you using the 64-bit version of Ubuntu?  If so, there is no java browser plugin for those versions of java.  If it doesn't work using IcedTea (I do play some pogo games with the IcedTea plugin but it can be troublesome), then you might want to install a 32-bit browser with 32-bit java plugins.

Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=202537&highlight=32-bit+firefox") for a good HowTo to set it up.

Another option is to install a 32-bit version of Ubuntu in Virtualbox and run your games from there.

[Virtual Box HowTo]("http://ubuntuforums.org/showthread.php?t=770745")

---

### Post by detroit/zero on 2008-06-14
> **bollix47 said:**
> Are you using the 64-bit version of Ubuntu?

Short answer: No.

I tried removing the JRE 1.5 and its plugins, etc.,and running on JRE1.6 but I wasn't able to make it work.

I don't understand it myself. Across three versions of Ubuntu (Feisty, Gutsy, and Hardy) and various versions of FF (2.x, Swiftfox, Iceweasel, 3.0b) the JRE1.6 has never worked for me. Maybe it's my computer? Maybe something else? This is just my Toshiba laptop, but I also had the same problem with my HP Desktop using Edgy and Feisty, and all the previously mentioned brands of FF, excluding 3.0b.

---

### Post by bollix47 on 2008-06-14
When you type ```
about:plugins
``` in the url/address window of Firefox what does it show for java?

Another command you can run in a terminal is:

```
java -version
```

Your htop window show multiple java_vm's running.  This will definitely cause the type of problem you're seeing. Either reboot or kill them all off and try again.

---

### Post by detroit/zero on 2008-06-14
This is a doosie:

```
**Java(TM) Plug-in 1.5.0_15-b04**

 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.5.0_15   MIME Type Description Suffixes Enabled    application/x-java-vm Java 
Yes   application/x-java-applet Java 
Yes   application/x-java-applet;version=1.1 Java 
Yes   application/x-java-applet;version=1.1.1 Java 
Yes   application/x-java-applet;version=1.1.2 Java 
Yes   application/x-java-applet;version=1.1.3 Java 
Yes   application/x-java-applet;version=1.2 Java 
Yes   application/x-java-applet;version=1.2.1 Java 
Yes   application/x-java-applet;version=1.2.2 Java 
Yes   application/x-java-applet;version=1.3 Java 
Yes   application/x-java-applet;version=1.3.1 Java 
Yes   application/x-java-applet;version=1.4 Java 
Yes   application/x-java-applet;version=1.4.1 Java 
Yes   application/x-java-applet;version=1.4.2 Java 
Yes   application/x-java-applet;version=1.5 Java 
Yes   application/x-java-applet;jpi-version=1.5.0_15 Java 
Yes   application/x-java-bean Java 
Yes   application/x-java-bean;version=1.1 Java 
Yes   application/x-java-bean;version=1.1.1 Java 
Yes   application/x-java-bean;version=1.1.2 Java 
Yes   application/x-java-bean;version=1.1.3 Java 
Yes   application/x-java-bean;version=1.2 Java 
Yes   application/x-java-bean;version=1.2.1 Java 
Yes   application/x-java-bean;version=1.2.2 Java 
Yes   application/x-java-bean;version=1.3 Java 
Yes   application/x-java-bean;version=1.3.1 Java 
Yes   application/x-java-bean;version=1.4 Java 
Yes   application/x-java-bean;version=1.4.1 Java 
Yes   application/x-java-bean;version=1.4.2 Java 
Yes   application/x-java-bean;version=1.5 Java 
Yes   application/x-java-bean;jpi-version=1.5.0_15 Java 
Yes
```

---

### Post by bollix47 on 2008-06-14
Please see my last post again.  I was editing it while you were responding.

---

### Post by detroit/zero on 2008-06-14
> **bollix47 said:**
> Your htop window show multiple java_vm's running.  This will definitely cause the type of problem you're seeing. Either reboot or kill them all off and try again.

Oh, OK. I did notice that in htop, too. I thought maybe it was one vm running for each window that was open.. the main window with yahoo games that sets everything in motion, the game lobby room window, and the individual game window - but I count four in just that screenshot and that doesn't add up.

When I type java -version in a terminal, I get this:```
zero@zero-laptop:~$ java -version
java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Client VM (build 1.5.0_15-b04, mixed mode, sharing)
```Nothing out of the ordinary, I say.

Do you think this is just a bug that'll be cleared up when FF3 leaves beta? I've done multiple un/re-installs of various Java versions with plenty of reboots along the way.

How can I keep all those extra VMs from loading?

---

### Post by bollix47 on 2008-06-14
Your plugins and version look okay.

There should only be one java_vm running.  Others get added if there's been a java error and you don't restart Firefox.  That's when you'll see the CPU usage go up for Firefox.

---

### Post by silbar on 2008-06-14
Greetings,

Coming into this thread with similar problems getting Firefox 3 to run a Java applet -- in my case it is the interactive Washington Post crossword puzzle.

For a while, after installing gcjwebplugin-4.2 and its dependencies, just entering the web page that has this applet causes FF3 to crash and burn.
Having removed gcjwebplugin-4.2 (and gij-4.2), I now can enter that web page page without crashing, but -- of course -- no interactive crossword puzzle.

The FF3 preferences says it has Java enabled.  However, following
Bollix47's sugestion,

  > When you type 'about:plugins' in the url/address window 
  > of Firefox what does it show for java?

it shows nothing.  This is still true after I install Java 1.6 (getting it from the Sun web site and running the RPM through alien).  It does install things in /usr/java/jre1.6.0_06/.  Bollix47 also suggests

  > Another command you can run in a terminal is 'java -version'.

When I do that I get it the following response:

  silbar@Lynx:~$ java -version
  Error occurred during initialization of VM
  java/lang/NoClassDefFoundError: java/lang/Object

I have also tried the following link

  ls -s /usr/java/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so 
        /usr/lib/firefox/plugins

(no broken line) and that does not help.

So, I am at a loss about how to proceed.  And I actually need to run Java applets in FireFox for reasons other than the crossword puzzle.

Thanks in advance for any suggestions,

   Dick Silbar

---

### Post by bollix47 on 2008-06-14
```
ls -s /usr/java/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/plugins

```

That should be ln -s not ls -s.

You could have installed 1.6 using synaptic.  It's in the multiverse repository.

If you're using 64-bit ubuntu then try the ICED TEA java.  It's what I have and the crossword works fine for me.

---

### Post by silbar on 2008-06-14
Thanks Bollix47.  It was in fact 'ln -s ...', and the link is definitely there.  Sorry for the typo.

Dick Silbar

---

### Post by bollix47 on 2008-06-14
Okay, assuming you're using 32-bit Ubuntu I would try the following:

Close Firefox.

Open Synaptic Package Manager. (System > Administration)

Go to Settings > Repositories and make sure there's a checkmark for universe and multiverse.

Click on the Reload button.

Click on the Search button and enter sun-java.

Put a checkmark next to sun-java6-bin and sun-java6-jre.

Click  on apply.

After it finishes installing open up Firefox and try the following again:

```
about:plugins
```


Does java appear now?

---

### Post by silbar on 2008-06-14
Well, double thanks, Bollix47, for the pointer to Synaptic.  When I had looked there earlier, I didn't see Java 1.6, which is why I went to the Sun web site.  But, it IS there, just under sun-java6-***.  After removing the jre that was installed earlier by alien and doing the install of the sun-java6-plugin (and its associated dependencies) I now have interactive java applets working in FireFox 3.

Dick Silbar

---

### Post by silbar on 2009-05-08
Curious that I/we had solved this a year ago.  But, after a re-install of the system, I had to relearn all that is already here in this thread.  Amazing how much one can forget in 11 months.

Dick Silbar

---

### Post by detroit/zero on 2009-05-08
Congratulations.

I started the thread, and my problem never got solved. It's been almost a year and I haven't been able to use Java in FF3 inside Ubuntu the whole time. I've done multiple un-/re-installs of a few different versions of Java, even compiling my own - no go for me. Trying to access a page with Java causes 100% cpu usage for Firefox, freezes my system, and I usually have to kill the process manually from TTY2.

Luckily, I have an XP virtual machine that I use whenever I get an itch to play java games or anything else.

---

