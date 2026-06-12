---
title: "[SOLVED] Most Apps taking 20 seconds exactly to open"
date: 2007-10-11
forum: General Help
---

### Post by bretto_40 on 2007-10-11
Hi
I am a newcomer to Ubuntu, and absolutely love it and don't want to go back to Windows, but if I can't get the following fixed I may have no choice... and I don't want to do that! :(

I am sorry in advance for the long post, but hopefully someone will be able to help just by reading the initial list of issues:

I installed Edgy and upgraded to Feisty, but before the upgrade and now after the upgrade I have had the following issue:

Most applications that I open will take exactly 20 seconds to open, and I am being specific here, I have timed them. To anyone sitting there waiting for something to open, 20 seconds feels like an eternity.

Once apps are open they work fine. But an important thing to note here is that it's as though from the point I click on an app to open it it will count off 20 seconds, and then proceed as though I had just clicked it after 20 seconds.

For example, something that normally would take about 2 - 3 seconds to load (such as Firefox) will do so after 22-23 seconds, as though it waits 20 seconds after I click, and then opens. Or if something that would normally take 5 seconds to open, will open instead in exactly 25 seconds.

I haven't tested everything in Ubunto, but here is a list of common apps that I have tested this on and perform exactly the same way EVERY time:

Firefox
Terminal
Text Editor
Network
Thunderbird
Monkey bubble (Game)
Totem

I have noticed however that opening Synaptic or Add/Remove comes up normally; there may be others, but I haven't testing everything.

One thing in addition to the above, when opening Open Office, which I realize is a slow opener normally, in following the above 20 second pattern the loading splash screen will come up immediately but it will sit there for "20 seconds" then all of a sudden it will progress almost to fully loading and then sit there for another "20 seconds" and bang, it's open.

The only other tests I have tried to do is tried re-booting with my wireless router turned off to see if that makes a difference, it did... sort of. I have both a LAN card and a wireless card in my machine but am only using the LAN card connected directly to the router because my wireless network is currently WPA which is not supported in Ubuntu, so I have it connected directly to the router through cable and DHCP. Which means that I have a Wireless card sitting in there doing nothing, so I'm not sure if that has anything to do with this.

But when I rebooted without the router on it booted into Ubuntu and I opened up a terminal and it came straight up, I then opened Firefox and it too came straight up (so naturally I thought it might be network related). However, after the 10 seconds or so that it took me to test these two items, the problem returned and everything reverted back to opening after exactly 20 seconds.

I won't say anything more in the hope that someone already knows a solution, other than that I am using a new Nvidia GeForce 8500GT graphics card which is not yet supported natively by Ubuntu, but I got the X server working by installing the latest drivers for the card from Nvidia and installing via the command line (something I had to redo after upgrading to Feisty). But I guess I don't see how a graphics card would be forcing applications to load only after exactly 20 seconds.

Another note is that after upgrading to Feisty, after entering my user name and password the Nautilus splash screen takes much longer to finish and disappear.

If anyone requires more detailed info regarding my machine or the processes I performed to get to this point let me know and I will include them.

Sorry for the LONG post. :oops:

Cheers

---

### Post by cyberfin on 2007-10-11
Wow! I have found another being on the planet that has EXACTLY the same problem as me! In my case though it's on the laptop, my desktop works perfectly. I have reinstalled like 20 times, scavenged the web, forums and irc with no avail.

This laptop in question is a custom made 1.3 Mhz intel centrino mobile with integrated 915 graphics and 1 gig of ram. I have already posted this [here]("http://ubuntuforums.org/showthread.php?t=571593").

This is very strange and I've tried installing 7.04 and 7.10 with and without live cd, both of them.

About a year ago I installed ubuntu on the same laptop and did not have this issue. Have you installed any previous versions? Do you happen to get USB error messages when detecting your hardware?

Keep the hope up, ubuntu is wonderful once you get it to work properly.

---

### Post by bretto_40 on 2007-10-11
Hi Cyberfin, :)

Great to hear someone else out there with this problem... though disappointing to know that the two of us seem to be the only ones. I was hoping someone could point out that it's a common issue with a common solution.

My machine specs are as follows:

Intel Core 2 Quad Core CPU
2 gig RAM
2 x 320 gb SATA HDD
512mb Nvidia GeForce 8500GT graphics card
Broadcom Wireless card
Onboard LAN

And that's about it that's relevant I guess.

Ok, some more detail on my problems:

First though I might mention that I have been running and trying Ubuntu for a few weeks now in Virtualbox on Windows XP with NONE of the issues I've discussed or about to note here.

Starting with my Edgy live CD (6.10), I could not use the standard start/install option because I got the infamous "Can't access tty; job control turned off" after it goes through the motions a little bit.

Many people have had this error with no resolution but I found a post while researching that SATA hard drives have a tendency to block the CD Rom drive. Armed with this idea (and after trying to disconnect one of my HDDs which was another suggestion, failed), I grabbed my USB external CD/DVD drive and booted off USB, and I was able to proceed around this error. (note: Once everything was running I still had to add piix to the initramfs module, but everything worked after that).

I was then still unable to install normally because I would get a failed to start x server error when trying to get into the live CD. So I installed via the text mode.

This worked but after install I still couldn't boot into x server "error: no screens found", which I discovered was because Ubuntu did not natively support my graphics card. So I then downloaded the drivers for it on my laptop, burnt them to CD, manually mounted the CD via the command line on my desktop machine and was able to install the drivers.

After that I was able to boot into Ubuntu. Now, there is an important note here to consider: you asked if I had it working ok with any previous releases.

At this point in time I had just get everything working so I could actually get IN to Ubuntu and I concentrated on my next task which was to get Ubuntu to run on my wireless network. Now, while I was fiddling around with that I "think" this issue of apps taking 20 second to open was not happening. I say that I "think" this because I don't seem to recall the issue and I was fiddling around long enough to notice I think.

So anyway, I eventually got the wireless working and it was while I was getting ready to download the upgrade to Feisty (7.04) that I started noticing the issue (though I hadn't discovered the 20 second thing yet). 

I ignored it and hoped it would be fixed by the upgrade to Feisty.

After the upgrade to Feisty I found I couldn't get the X server working again and sure enough I had to re-load the Nvidia driver, and it worked again:

However, another thing important to note: Ever since the upgrade, when booting up from the computer being off, it goes through it's normal paces with the Ubuntu and "Windows" like loading bar, but before it finishes it switches to text mode where you see everything loading with [OK] at the end, and I seem to recall something about a mem test failing or something, not sure (or maybe this was while shutting down? It's too fast to get a good sense).

But the thing is, apart from that everything boots up fine; however one other difference is that now, after I've put in my user name the Ubuntu splash screen that loads Nautilus etc. takes a long time to finish and in fact the desktop actually loads by the time it finishes.

That pretty much brings me to where I am. Sorry for another LONG post.

I just hope I can find a tweak or something that will fix this because I really don't want to have to put up with it. I could go back to Windows while running Ubuntu through Virtualbox but to me it's too volatile given that a bad error in Virtualbox could mean I lose my entire Ubuntu installation.

*sigh* :(

p.s. No USB errors yet. After reading your post tried one of my USB stick drives, no probs.

---

### Post by cyberfin on 2007-10-11
Well Bretto_40,

I have seen a few posts mentioning issues as soon as the box connects to internet. I don't know if this is related. In my case, I have tried installing while connected and without, both with the same result. I keep my fingers crossed when Ubuntu boots up, but when I enter the username and discover that it takes almost half a minute for the password field to come up... (sigh).

Another thing, I get the USB errors without any devices connected. If I boot Xubuntu Live CD it doesn't show up (not that I can see at least).

Let's hope someone can give us some insight to this problem. I enjoy Ubuntu on my desktop, I would like to extend the enjoyment to the laptop as well.

By the way: If anyone is reading this... please help!!! ](*,)](*,)](*,)

---

### Post by cyberfin on 2007-10-12
New day, new updates! And I noticed that out of 9 updates the last one is xserver-xorg-video-intel, which seems to update the intel driver for graphic chips; mine particularly is the integrated 915.

I'm gonna go install and run the updates, I'll let you know if the 20 second waiting goes away...

---

### Post by cwhitehouse on 2007-10-12
Sorry to bump your thread and maybe get you excited thinking someone posted a solution.  I just wanted to say that this is one of the strangest issues I have heard of.  I can see how this could be horrible to have to live with.  Keep us posted I'm curious how this will play out.

---

### Post by mbeierl on 2007-10-12
It does sound vaguely network related: X windows talk to the X server via the network.  It almost sounds like there is a route problem back to localhost.  If you have sshd installed, how long does it take for you to get a connection via telnet like so:
```

telnet localhost 22
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

Protocol mismatch.
Connection closed by foreign host.

```
Mine came back immediately.

To troubleshoot a little more, what is the output of ```
ifconfig
``` and what is the contents of your /etc/hosts file?

---

### Post by cyberfin on 2007-10-12
Right, the telnet took about 5 seconds to return anything; that's after 20+ seconds to get the terminal open...

Return of ifconfig:

```
eth1      Link encap:Ethernet  HWaddr 00:0F:B0:7F:DA:0A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xe300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)
```

And the content of /etc/hosts file:

```
127.0.0.1	localhost
127.0.1.1	ubuntulaptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

BTW, I reinstalled and updated with the latest updates but to no avail. However I discovered that when I did a lsusb it shows no devices are connected. I have a usb wireless adapter and I have so far not been able making it work. Also when booting I get the following line: 5-5 usb is not accepting the address -error 110 (or something similar, i get 3 of them).

Is this maybe chipset related?

Any input is very much appreciated.

---

### Post by mbeierl on 2007-10-12
Why 127.0.1.1 for ubuntulaptop?  Try this for your /etc/hosts:
```

127.0.0.1 localhost ubuntulaptop

```
It might be that it's trying to connect to 127.0.1.1, which is not registered to lo, giving up after 20s, then going to 127.0.0.1...

---

### Post by cyberfin on 2007-10-13
Well I tried changing the hosts file as suggested (which I think I have tried previously already) and there was no change. However, last time I rebooted I noticed something which had been there all the time but I hadn't taken into account; it mentions something about my cpu and scaling. Further down it mentions the usb -110 problem as I quoted. Might I have been barking at the wrong tree?

Screenshot attached:

[here]("http://www.geocities.com/cyb3rfin/sync/bootscrnsht2.png")

bretto_40, have you noticed this during boot? 

Opinions anyone? Pweeeety pweeeease!

---

### Post by cyberfin on 2007-10-14
SUCCESS! \\:D/

After hours upon hours of reading forums and other sites it turns out that this is definitively a problem with the i915 chipset and other random causes. Read all about it:

[here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/30557")

Now in another thread on this forum I found people that had the same problem with powernowd and cpu scaling. It suggested that I should reinstall with the following commands added to the install line:

nosplash noapic nolapic (i also added irqpoll and vga=normal which solved my usb and screen problems)

I have just finished installing and the 20 second delay is gone! The reason for it is very well explained in the Bug thread...

Now I just need to get my wireless usb adapter configured, and we're in business!

Please comment or query all you want, I'll be following this thread until it dies.

Good luck!

---

### Post by bretto_40 on 2007-10-18
> **mbeierl said:**
> It does sound vaguely network related: X windows talk to the X server via the network.  It almost sounds like there is a route problem back to localhost.  If you have sshd installed, how long does it take for you to get a connection via telnet like so:
```

telnet localhost 22
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

Protocol mismatch.
Connection closed by foreign host.

```
Mine came back immediately.

To troubleshoot a little more, what is the output of ```
ifconfig
``` and what is the contents of your /etc/hosts file?

Ok, the following is what I got when used telnet and the output of ifconfig. NOTE: You asked how long it takes to get a connection via Telnet; aside from the fact that it didn't seem to; it took exactly 20 seconds (surprise surprise) for the data to be output after hitting enter.

brett@ubuntu:~$ telnet localhost 22
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
brett@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:D1:A0:19:DA  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:13101032 (12.4 MiB)  TX bytes:1546573 (1.4 MiB)
          Base address:0x30c0 Memory:a3200000-a3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:856 (856.0 b)  TX bytes:856 (856.0 b)


and the following is the contents of my etc/hosts file:

127.0.0.1 localhost
127.0.1.1 ubuntu.HOMESTAR

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by cyberfin on 2007-10-18
Do you know if you get the cpu frequency scaling error message during boot up as happened to me? If that is the case you should be able to solve the problem by deactivating the acpi.

If you can't see it you might want to try doing a -verbose boot to see all the messages...

---

### Post by mbeierl on 2007-10-18
And a ping of localhost?
```
ping 127.0.0.1
- or -
ping 127.0.1.1
```

---

### Post by s.victor on 2007-10-19
I have the same problem since I installed Gutsy yesterday.

The 20 seconds delay happens only when I'm using Firefox and the internet in general. I'm dual-booting with Vista and don't have the same problem there. I never had it in Feisty either.

Any help appreciated.

---

### Post by s.victor on 2007-10-19
I found a solution for my problem [here]("http://ubuntuforums.org/showthread.php?t=550571").

---

### Post by bretto_40 on 2007-10-19
Hi guys,

Ok, first things first. I tried pinging and the responses come back instantly and cleanly.... I'm beginning to think that my issue is not related to my network setup at all.

Cyberfin; I don't remember seeing that error at startup about the CPU scaling... but then I don't seem to have any CPU issues. Your link to the bug page talks about CPU being maxed out while running applications but I don't get this from any of my 4 CPUs... they all seem to run fine.

Question: How can I find out if my computer uses an i915 chipset? I'd like to find out so I can determine if I'm having similar issues because of it, which means I might be able to fix it as you have Cyberfin. Congrats on fixing everything up by the way Cyberfin :)

How do you reboot in verbose mode? Remember I'm a newb so a lot of things people take for granted I don't just don't know how to do.

Now, I have just downloaded 7.10 as an ISO and burnt it to disk and am keen to upgrade my current install via the CD (as apposed to by downloading the update); but how do I do this?

If I update from the CD and then the problem still exists I was planning on just re-installing and starting fresh at the 7.10 mark.

Also, if ACPI could be my problem, how do I disable that as a test to see if it helps to do so?

Cheers

---

### Post by cyberfin on 2007-10-20
> How can I find out if my computer uses an i915 chipset?

I suppose you would have to find the specs of your motherboard, I saw some people on the other thread that were having problems with ASUS mobos.

> How do you reboot in verbose mode?

"When the PC boots up, you will see the Grub countdown, which is set to 3 seconds by default. Press "Esc" to intercept this countdown and go enter a Grub menu. Then

    * Press 'e' to start editing.
    * Scroll down to the "kernel..." line. The is the line that tells Grub which kernel to boot with and the parameters to be passed to the kernel when it boots are placed at the end of this line.
    * Press 'e' again to edit this line.
    * Move to the end of the line. You will see any existing parameters and can add other new parameters to the end.
    * Parameters are separated by spaces and are mostly either a single word (e.g. nolapic), or an equation (e.g. acpi=off).
    * Once you have added the parameter to the end of the line, press Enter to accept the editing.
    * Then press 'b' to boot using that kernel and those parameters."

-Quoted from [here]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")

You just need to add "-verbose" to the end of the line without the quotation marks.

> if ACPI could be my problem, how do I disable that as a test to see if it helps to do so?

Now, I actually did an install with the "noapic" and "nolapic" options (to do this press F6 at the installation menu and add the line like in GRUB, just before hitting enter to start the installation). The result was that my laptop runs flawlessly but does seem to produce more heat (that's what acpi does, it regulates power consumption by managing the cpu and chipset output).

I'm in no sense an expert on the subject, I just read some posts and visited intel's website, but at the end it made perfect sense, so I tried it. It could be that your problem lies elsewhere... But if you have nothing to loose... I suggest giving it a try.

Hope I've helped!

---

### Post by RedfishBluefish on 2007-10-20
> How can I find out if my computer uses an i915 chipset?

Try searching through the output of "lshw"? (which needs to be run as root, i think)

---

### Post by bretto_40 on 2007-10-20
Ok, checked out the output of LSHW and no reference to i915 chipset anywhere in the output; so I guess this is not the source of the problems.

One thing I noticed though, I didn't realise the processor I'm using, which is the Intel Core 2 Duo quad Core 6600 processor(s) is a 64bit processor.

I'm running the standard 32 bit install of Ubuntu.... but surely this is not the cause of the problem?

I'm thinking for now I might upgrade over the net to Gutsy; see if that fixes the issue; and if not I'm going to try re-installing the entire system from scratch using the Gutsy Live CD.

---

### Post by dcstar on 2007-10-20
Make sure that the following looks ok:

```
hostname -s
hostname -f
hostname -a
```

If these aren't all correct, then there could be delay issues (as well as waiting for IPv6 timeouts).

---

### Post by bretto_40 on 2007-10-21
> **dcstar said:**
> Make sure that the following looks ok:

```
hostname -s
hostname -f
hostname -a
```

If these aren't all correct, then there could be delay issues (as well as waiting for IPv6 timeouts).

Ok, tried all of these; and they are not fine. Each one comes up and says "unknown host"

Further to this; from the time I hit enter for each command it is taking it's usual 20 seconds exactly before outputting the result.

How can I fix this???? :(

---

### Post by mbeierl on 2007-10-26
Okay, how about the output of /etc/nsswitch.conf

Also, do you get a 20s delay looking up host names?
```
$ time host ubuntuforums.org
ubuntuforums.org has address 91.189.94.186
ubuntuforums.org mail is handled by 10 mail.ubuntuforums.org.

real    0m0.471s
user    0m0.003s
sys     0m0.006s

```

---

### Post by bretto_40 on 2007-10-27
This was the output of that file:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---------------------

I have no idea what this means.

Interestingly though, I just upgraded to Gutys but before I did I fiddled around with the network settings and managed to reduce the 20 second problem to 12 seconds! For everything!

Now I have upgraded to Gutsy (Hardly call it an upgrade when now my sound doesn't work because it is no longer supported by the new Kernel.... I find this absolutely idiotic), the 20 second has come back and is in some cases worse.... yet network changes are as they where when I had it down to 12 seconds.

I think I'm going to do a clean install of Feisty and wait until the next Ubuntu release to see if the next Kernel version has support for my sound card again.

If the clean install doesn't fix this problem I may try compiling my own Kernel but I can't seem to find ANYWHERE that has nice Noob friendly instructions on how to do this.

I love Linux... but at the same time, I hate it at times... ](*,)

---

### Post by mbeierl on 2007-10-27
I hear ya!  I've been wrestling with the latest video/compiz fusion/effects, etc...  But at the same time, I find these forums simply awesome!  If these were MS problems, where could we turn?  At least here there is a general collaborative spirit, even if we can't get to the bottom of the problems.

(As an aside, what sound card do you have?  Use lspci to give the basic output.)

An what was the result of the host ubuntuforms.org command?  Did it come back quickly, or same thing (20s).

I'm not sure compiling a new kernel will help, but here's a nice howto:

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by bretto_40 on 2007-10-28
Success!!!!! This problems is now SOLVED! \\:D/

As it turns out, it was my network setup that was just wrong.

The way I found how to fix it was this; in the frustration of not being able to get my sound card to work under Gutsy I had decided to throw the towel in and just do a complete re-install of the distro; but as a Feisty install.

So I downloaded the ISO for the live CD and burnt it do disk. I threw the disk in and to my surprise it actually booted up into the live version of the distro (my Edgy live CD can't do this because it falls over with a common problem experienced by people who run SATA HDDs like me).

So, before I went for the "install" option I decided to give opening up some apps a try to see how they perform because I was always sure that the first time I ran Edgy it wasn't having this issue.

So I tried a few of my known problem programs such as Firefox, a command terminal and open office.

Aside from the fact that each one took much longer than normal because they had to load files off the CD in order to start for the first time, everything ran beautifully. I.e. after that initial first time of opening any one of these apps; once it opened I would close it and open it a second time and BANG; opens up in a flash, which is the way it SHOULD be!

So, I thought to myself, what's the difference?

And so the first place I looked was the network setup. The network automatically set itself up, so I thought, well, if it's automatically setup I figure if the problem is to do with bad network settings, this should then, by a process of elimination, have the CORRECT setup.

So I had a look, and really the only difference was that in my old (bad) setup I had something in the domain name box, where this didn't have anything, and in the host screen I had the first host as "localhost.<domain name>".

So, I jotted all this down on a bit of paper and then rebooted the machine back into my Gutsy install.

I then went in and adjusted all of the network settings so they were identical to what was configured automatically in the live CD, and BANG; everything now opens and works exactly as it should!

I am so happy about this you will not believe because I was worried I'd have a semi-permanent and mysterious hardware issue.

Now, if I can only get the sound card to work. It is an Intel 82801H (ICH8 )

It was supported under the Edgy and Feisty Kernel's but the Kernel for Gutsy doesn't support it... why? I seriously don't know... the only thing I can think of is if they did it to conserve kernel space so it will all fit onto a live CD... but my computer's motherboard is a brand new one, so why would they cut something from the Kernel that people are going to continue to want supported?

I could understand cutting support for 10 year old cards or something like that...

But anyway... now I have solved that I battle a little more to see if I get this sound card supported under the Gutsy Kernel and if I fail I guess I will have to go back to Feisty until my card is supported again. But I have a separate thread going for the sound card issue.

Cheers all that tried to help me out on this one!! All help much appreciated! :)

---

### Post by dcstar on 2007-10-28
> **bretto_40 said:**
> 
..........
Now, if I can only get the sound card to work. It is an Intel 82801H (ICH8 )

It was supported under the Edgy and Feisty Kernel's but the Kernel for Gutsy doesn't support it... why? I seriously don't know... the only thing I can think of is if they did it to conserve kernel space so it will all fit onto a live CD... but my computer's motherboard is a brand new one, so why would they cut something from the Kernel that people are going to continue to want supported?

I could understand cutting support for 10 year old cards or something like that...

But anyway... now I have solved that I battle a little more to see if I get this sound card supported under the Gutsy Kernel and if I fail I guess I will have to go back to Feisty until my card is supported again. But I have a separate thread going for the sound card issue.

Cheers all that tried to help me out on this one!! All help much appreciated! :)

You can recompile the Ubuntu kernel with that option enabled, do a search for the various HOWTOs in the forum if you think it is worthwhile.

---

### Post by bretto_40 on 2007-10-28
Thanks for the suggestion but about 15 minutes after posting that last reply I solved my sound issue as well!! \\:D/

So, if anyone has come across this part of the thread with the same issue (and I will be posting this fix elsewhere as well); then the following may be of interest:

My card is an Intel 8801H (ICH8 ), anyone who has this card won't get any support for it out of the box in Gutsy, but will in Edgy and Feisty (these are the only two I've tried).

I found this site: [http://users.piuha.net/martti/comp/d630/index.html](http://users.piuha.net/martti/comp/d630/index.html)

The guy who authored this site has posted a script to fix this issue automatically; download the script.

After running the script I had to do the following to get it to work so you may have to do the same:

sudo apt-get install linux-source
sudo apt-get install linux-headers-`uname -r`

Once all of that is done, run the script and the whole process should be done automatically; re-boot and you should have sound again! :)

I hope the above works if you have this issue.

---

