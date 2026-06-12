---
title: "Recent edgy hardlocks"
date: 2006-11-09
forum: General Help
---

### Post by misha680 on 2006-11-09
Hi,

I have recently (as of a couple of days ago, possibly this past weekend) have started experiencing random hard locks on my edgy system for no apparent reason (a lot have been scrolling in firefox, but one was when I wasn't even at the computer with evolution open). I was wondering if anyone has had the same problems. From my synaptic history these are my recent updates:

```
Commit Log for Sat Nov  4 12:54:44 2006


Upgraded the following packages:
fglrx-control (8.28.8+2.6.17.5-11) to 8.28.8+2.6.17.6-1
libimlib2 (1.2.1-2ubuntu1) to 1.2.1-2ubuntu1.1
librpm4 (4.4.1-9.1build1) to 4.4.1-9.1ubuntu0.1
linux-restricted-modules-2.6.17-10-generic (2.6.17.5-11) to 2.6.17.6-1
linux-restricted-modules-common (2.6.17.5-11) to 2.6.17.6-1
rpm (4.4.1-9.1build1) to 4.4.1-9.1ubuntu0.1

```

and

```

Commit Log for Fri Nov  3 09:26:27 2006


Upgraded the following packages:
imagemagick (7:6.2.4.5.dfsg1-0.10) to 7:6.2.4.5.dfsg1-0.10ubuntu0.1
libmagick9 (7:6.2.4.5.dfsg1-0.10) to 7:6.2.4.5.dfsg1-0.10ubuntu0.1
libpq4 (8.1.4-7) to 8.1.4-7ubuntu0.1
libwv-1.2-1 (1.2.1-2) to 1.2.1-2ubuntu0.1
screen (4.0.2-4.1ubuntu5) to 4.0.2-4.1ubuntu5.6.10

```

I was wondering if anyone else has this problem and has any solutions? I checked syslog but didn't find any errors.

Misha

---

### Post by Pcghost on 2006-11-11
I too am having this problem.  It only happens when I run the 2.6.17-generic kernel instead of the i386 version. My machine is an Athlon X2 64 4200+, 2GB corsair PC3200 DDR, 2x Nvidia GeForce 6800XT (using nvidia driver).

   This is a very frustrating development because nothing shows up in the logs and there is not a lot of people having this problem that I can find.  I have heard some say this issue is Ubuntu specific, I sincerley hope not because there are not too many distros of Ubuntus quality anymore IMO.  

   Does anyone have any idea what is causing this????  Is it an Nvidia problem or a SMP kernel problem?](*,)

---

### Post by albertomm on 2006-11-11
Same problem here with an ATI X300. The computer has a crash hard almost every day. I've looked a the logs but there is nothing strange.

---

### Post by misha680 on 2006-11-11
I _think_ I solved my problem because I have been messing with NetworkManager cvs a lot lately and actually had two different versions of the -dev and regular debs installed, so perhaps this was a dbus problem for me. In any case, I haven't had a hard lock for a few days... but I'll cross my fingers and hope it won't happen again.

Misha

---

### Post by jimbob on 2006-11-11
Just for the record, I too am experiencing random hard lockups. 

Mine occur about every other day and it doesn't matter if I am working on something or the computer is just sitting there idle.

I blamed it on memory for a while but the memory runs all night with no errors.

Wish I could put my finger on the cause.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by albertomm on 2006-11-11
> **misha680 said:**
> I _think_ I solved my problem because I have been messing with NetworkManager cvs a lot lately and actually had two different versions of the -dev and regular debs installed, so perhaps this was a dbus problem for me. In any case, I haven't had a hard lock for a few days... but I'll cross my fingers and hope it won't happen again.

I dont think that networkmanager or dbus can make the system hang completely. When I say hardlock i mean that the mouse is stuck, the CTRL+ALT+BACKSPACE dont restart the X server and the system dont answer even remotely by network (I try whith SSH and nmap).

---

### Post by misha680 on 2006-11-11
Yes, I believe you are correct, although the problems I was having were in fact hard locks as you described, mouse is stuck, no ctrl+altr+backspace or ctrl+alt+delete, ssh doesn't connect, etc., but I think it was solved by fixing my network manager inconsistency although possibly (a) my problem is not solved or (b) something else solved the problem.

Misha

> **albertomm said:**
> I dont think that networkmanager or dbus can make the system hang completely. When I say hardlock i mean that the mouse is stuck, the CTRL+ALT+BACKSPACE dont restart the X server and the system dont answer even remotely by network (I try whith SSH and nmap).

---

### Post by vvlist on 2006-11-12
I'm having the hardlocks too, it must be Gnome-related, because I can use xterm just fine...

---

### Post by n1xt3r on 2006-11-14
I too have experienced similar random hardlocks. I install updates on a regular basis and actually started experiencing these hardlocks before I decided to upgrade to edgy. I run xubuntu ppc, and was hoping that edgy might upgrade my kernel, but alas I'm still running the same kernel. I have my power button programmed to suspend my ibook and was able to recover from the hardlock by initiating and recovering from a suspend. Unfortunately, any programs I have running are effectively terminated, whenever I use the suspend-to-regain-control trick.

Anyways, looking back to the kernel. I did notice that I have two linux-image's installed:

```
dpkg -l linux-image*
ii  linux-image-2.6.12-9-powe 2.6.12-9.23               Linux kernel image for version 2.6.12 on PowerPC.
ii  linux-image-2.6.15-25-pow 2.6.15-25.43              Linux kernel image for version 2.6.15 on PowerPC.

```

Other than that, there's nothing out of the ordinary. I'm guessing it probably wasn't upgraded, because I'm running a custom kernel. Which makes me wonder if it's caused by a conflict with a userland kernel program. This might also explain why my boot parameter, "video=radeonfb:1024x768-24@60" was seemingly causing ubuntu to boot in 640x480 after the upgrade to edgy.

---

### Post by enigmamachine42 on 2006-11-19
I too have been experiencing 1 or 2 hard locks a day since I upgraded to Edgy.  Usually they occur while playing a game or watching a video, but sometimes the system just locks up for the heck of it.  Being a KDE user, I think that this eliminates the desktop manager from the list of suspects.  Additionally, I had this problem before.  Going back to Dapper fixed the problems entirely and upgrading to Edgy again resurrected them.  If anyone knows how to fix this problem without yet another install, I would really appreciate the help.

---

### Post by n8bounds on 2006-11-19
I have the same thing here.  I had dapper running solid for over 100 consequtive days on this machine...

This can't be some random event.  Most edgy users are former dapper users and know the difference between a kernel and a bag of popcorn.  What gives?

---

### Post by seanUSXIII on 2006-11-19
Is your problem anything like mine?

[http://ubuntuforums.org/showthread.php?t=302907](http://ubuntuforums.org/showthread.php?t=302907)

---

### Post by Grog140 on 2006-11-19
I too am having similar problems. 

Mostly hard locks.

---

### Post by The Belgain on 2006-11-20
Well, just to confirm - I'm also seeing hard-locks on Edgy.  Never had any problem on Dapper (using the same machine).  This is on a laptop, Athlon XP-M, ATI Mobility Radeon 9200.

Seems to be happening more frequently now that it was previously.  It's happening more since I installed Beryl (though that may be coincidental, and it was definitely happening before too).  No clear pattern as to what programs I'm using while it crashes - so far it's hung a couple of time when using Skype and a couple of times when using Azureus.

I haven't really installed very much non-standard stuff, other than Beryl (though as I say, it was happening before then) and a bunch of codecs.  I've confirmed that the problem isn't hardware-related (I'm back with windows for now and it's completely stable there).  What kind of logging do we have to diagnose this?  Any kernel logging which is output and useful for diagnosing hangs?  This is happening with enough frequency that Edgy's unusable for me, so would be good to figure this one out (as I do very much like Edgy).

---

### Post by ducttapebrown on 2006-11-20
I'm getting the same symptoms.  I remember this happening with beta edgy (before I reinstalled the whole shebang last week because I thought I'd mucked something up).  GeForce 2Go, Linksys Wifi card, P4 Dell Inspiron 2650 laptop here.

It's really becoming a pain as term papers are due next week.

---

### Post by seanUSXIII on 2006-11-20
I switched back to nvidia-glx and XGL and the problem went away. Thats kinda sad when my computer is more stable with XGL than without :-k

---

### Post by bailout on 2006-11-20
Suffering hard locks as well (Kubuntu). I have only had Edgy installed for a few days and have already had two hard locks during use but it has also failed to shutdown properly several times requiring me to turn off my pc manually. 

The first hard lock was while fetching a cd cover in amarok and I thought it might be connected to my wireless connection going down while doing this but the next time was just while swapping between applications. The shutdown failures seem to happen about every third or fourth time I try to shutdown. I have now started logging out of the session and then shutting down.

I used to have hard locks in dapper when I tried turning my wireless usb dongle on or off through kde system settings but at least I knew what was causing it and could avoid it by controlling the wireless via the command line. The locks in edgy seems to be random.

I have only really just set up edgy and have been imaging the partition with True Image at every stage so I can recover after a crash. TBH I am getting so fed up with Edgy I am thinking of trying another distro such as Mepis to see if it is any more reliable.

---

### Post by The Belgain on 2006-11-21
Well, I've submitted a bug report in launchpad for this: [https://launchpad.net/distros/ubuntu/+bug/72800](https://launchpad.net/distros/ubuntu/+bug/72800).

I suggest people add to this in order to have this tracker and hopefully addressed?

---

### Post by woodzcl55 on 2006-11-21
Hello, this is my first post here. I just wanted to put in my 2 cents that I don't think this is Ubuntu/Kubuntu specific.  I had been using Fedora core 5 for a long time then installed fc6 and had the same problem: [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=212777](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=212777).  I tried Kubuntu Edgy and the problem was still there. I then installed Kubuntu 6.06.1 and the problem was gone.  Now I'm back to 6.10 with no lockups after replacing the generic kernel with the i386 kernel. My CPU is an Athlon-XP 2500+ with NVIDIA Geforce4 MX440 graphics card (using 'nv' driver).

---

### Post by bonzini on 2006-11-22
This is just a "me too" to all of the above.  Dapper 6.06LTS worked fine on my Toshiba until I installed (not upgraded) the Edgy release.  I've had the same kind of "firmly stuck" behaviour, maybe once a day, maybe every other day, ever since.

Tried fglrx.  No difference.  Back to ati, following Radeon instructions on Wiki to get performance in hand.  Still no difference.

No message in logs at the time of crash; today, there were just the "MARK" messaged, then the reboot messages.

The last two times this has happened I've been using gmail in Firefox.

Glad to find out it's happening in Kubuntu **before** I tried installing that.:confused: 

Let's hope someone with some ideas on fixing this problem stumbles on this thread!

---

### Post by Ramses de Norre on 2006-11-22
I experienced this too, but switching from the generic to the i386 kernel seems to solve it. I've had a few x crashes but no kernel panics anymore.

For the record: my machine is an amd64 3700+ with 1G ram and an ati x600 with the fglrx driver from the repo.

---

### Post by jinxen on 2006-11-22
wierd, i am experiencing hard-locks too.. The most recent one was where i was typing in a new post here at the forum. Has anyone solved the problem yet?

---

### Post by master_b on 2006-11-22
Quick fix

Uninstalled latest ( last 3 or 4 days) flash-plugin obtained from multiverse repo.

No longer (so far) get lock-ups when surfing web.  Amazing how many websites/bbs's etc have loads of unnecessary flash content.

found the following links via Google:-

[http://copia.ogbuji.net/blog/2006-11-16/Ubuntu_Edg](http://copia.ogbuji.net/blog/2006-11-16/Ubuntu_Edg)

[http://thoth.robrohan.com/client/index.cfm/2006/10/26/Ubuntu-Edgy-and-Flash-9-Dont-Play-Well](http://thoth.robrohan.com/client/index.cfm/2006/10/26/Ubuntu-Edgy-and-Flash-9-Dont-Play-Well)

[http://ralph.n3rds.net/index.php?/archives/164-Flash-Player-version-9.html](http://ralph.n3rds.net/index.php?/archives/164-Flash-Player-version-9.html)

[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)

Not exhaustive - just first few that I found.

I can live without Flash.

Bill

EDIT - forgot to say that this problem is with Dapper.

Bill

---

### Post by The Belgain on 2006-11-22
I can confirm that changing to using the i386 kernel (rather than the generic kernel) seems to have solved the problem.  PC has been up for an hour or so without hanging, whereas previously it was handing within 5 minutes of starting up Gnome.  I had to boot in recovery mode to be able to grab the i386 kernel...

So it looks like just running "apt-get install linux-386" does the trick to fix this.  Hopefully there'll be an actual fix soon?

---

### Post by bailout on 2006-11-22
I have used kubuntu for a while now without a crash but I don't really trust it after my earlier experiences. I don't really want to go back to dapper as I had stability problems with my wireless dongle and printing wouldn't work (it is still pretty dodgy under edgy but it does work). I completely missed any discussion on this 'generic' kernel over the old i386 and other variants. btw mine was crashing without flash installed.

---

### Post by The Belgain on 2006-11-22
Yeah, my problems were also unrelated to flash (i.e. they were occurring without flash installed).  Also, from reading the threads linked to above, the flash problem crashes Firefox only, rather than causing the kernel to hang/crash.

Anyway, it looks like the workaround of moving to the i386 kernel does work and is simple to do (a single apt-get command + a reboot) so I would suggest doing that.

---

### Post by master_b on 2006-11-23
Flash 9 crashes Opera too.

bill

---

### Post by misha680 on 2006-11-28
Hmm... so I guess people are having hardlocks like I was. Now that I have gotten rid of them, I am noticing that a lot of times when my computer is idle it seems to start doing something and get really slow basically until I do a killall -u myusername and then it works fine. I think maybe it could be beagled, but I had it on Dapper and it never did this, and when I do a top it shows some system processes taking up the CPU (but different ones at different times). Anyone else have this prob?

Misha

**Update: although beagled was _never_ in my top list when the computer would be slow, instead kswapd0 always  was, since I disabled beagled I have not had any more problems with slowing.**

---

### Post by RMorris78 on 2006-12-01
I am experiencing these hard locks in edgy (kubuntu) as well. I have kernel 2.6.17-10-386, not the generic so that rules it out for me.  My hard locks usually come from, oddly enough, doing nothing.  I will leave the computer, come back 5 minutes later and my computer will be in a hard lock, with the same time on the clock when i left. CTRL + ALT + BKSP doesnt work, and the mouse will not work either.  I have tried googling this for the past couple days, and cant find anything](*,)

---

### Post by jnderose on 2006-12-23
I was having a similar problem on a dell latitude with an AMD Mobile turion 64 x2, the machine was initially not detecting the hard drive (I fixed it with pci=nomsi boot parameter), and after installation it was having hard lock ups after less than an hour of continuos operation.
I tried including the noapic parameter, and did some research on google. Apparently recent kernel versions have been exhibiting similar behavior in a few different distributions, and poking around led me to the 'nolapic' parameter. So now I've got noapic, and nolapic, as parameters to my boot as well as the pci=nomsi for the drive issue. it would appear that the apic support needs to be disabled, this is likely an smp specific issue. i have been transferring massive amounts of data through my wireless card and generally creating a significant load with vmware on this laptop for the last several hours and have not had any lock ups since adding the noapic and nolapic parameters. i tried them separate but it appears that both are necessary to alleviate the lockups. i hope this helps you all out, not many things are as crummy as a fresh install on a new machine that eats dirt after 45 minutes of use.

---

### Post by jnderose on 2006-12-23
oh i forgot to mention that i am using edgy with the 2.6.17-10-generic kernel...it would make sense that this combination would work since apic is only really an smp specific feature and the resolution for most has been using a uniprocessor kernel (386)..

what they both do:
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2003-08/6804.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2003-08/6804.html)

---

### Post by riven0 on 2006-12-23
Are you guys sure it's not graphical related? Are you guys running a screensaver when it locks up? When I had first installed Dapper on one of my older desktops, (with a radeon 9000), it used to lock up after a few hours of idling. I pinned it down to the screensaver and installed electricsheep instead. 

Never had the problem with edgy, though.:-k

---

### Post by albertomm on 2006-12-26
I have tried the noapic nolapic options and it has no effect for me.

And for the screensaver thing... the computer freezes while I am using it, the screensaver works fine when I am away. The problem we have here is that there is no way to get a clue of what is causing the crashes because there are no logs or system messages about it.

---

### Post by frank392 on 2007-02-05
PLEASE HELP!!
I'm going Bananas
ok First I was using MintLinux on my Laptop until i got a new video card for my Desktop I use to have a ATI X700 but thank to Scorp123 recommendations I got A NVIDIA I love it it is a Geforce 7900 Gs so I was able to install Linux mint on my Desktop, I have install all the drivers old manually with the ubuntu guide an the new ones with automatix bleder. said all that.
My computer Hangs!!
I was using Linuxmint 2.1 when this happened I had the same problem with 2.2. it freezes completely, I have to reboot the system after this happens.
usually it hapends when I'm downloading something from the internet I have a Zyxel wireles card G-302 V3 it is base on a RTL8185L Chipset (realtek) I Have try a SMC same chipset. no luck
BTW my card is recon. by Linux I have try installing the windows drivers with Ndiswrapper but no difference, so maybe is the combination of all this stuff.
I he try modifing the bios making it as simple as posible but no luck.
ok here is the basic conf of my system:
Motherboard Asus A8V-E Deluxe
CPU Athlon 64 3000
Memory 1 G Kington
HD Maxtor eide
Video Pny Nvidia Geforce 7900 GS PCIE
Wireles PCI Zyxel G-302 V3 

At least i do not feel that i'm the only one having this problems

---

### Post by jackrobinson on 2007-02-05
add **acpi=off** and **noapic** in the relevant kernel options line in */boot/grub/menu.lst*

---

### Post by frank392 on 2007-02-09
I fix the problem I got a new wireles card Dynex it is base on artheros chip

---

