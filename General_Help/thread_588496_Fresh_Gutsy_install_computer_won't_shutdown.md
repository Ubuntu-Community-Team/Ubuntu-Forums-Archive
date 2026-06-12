---
title: "Fresh Gutsy install: computer won't shutdown"
date: 2007-10-23
forum: General Help
---

### Post by Tallman on 2007-10-23
Hi all,

I did a fresh install of Gutsy earlier today and now my computer won't shutdown. After clicking on the power button in the upper right corner and selecting "Shut Down", the splash screen comes up and the bar is getting empty. When the bar is completely black, the computer hangs and all I can do is giving it a hard shutdown.

Strange thing is that I had Dapper, Edgy and Feisty running on this machine with the same specs and they didn't have this problem.

Who can help me in the right direction?
Thanks

---

### Post by Tallman on 2007-10-24
Let me bump this thread... :oops:

Anyone else with this problem?

---

### Post by cazoo on 2007-10-25
Yes, I have the same problem and I only installed Ubuntu yesterday. It does exactly the same. The bar completes and it just hangs on a black screen. I have to hard shut it down every time.

---

### Post by klainmeister on 2007-10-25
I have the exact same problem and have to hard shutdown each time.

Bump and someone please help, this is rather annoying.

---

### Post by Tallman on 2007-10-25
Found this bug on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308")

I have tried the two solutions provided there:

> Do sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Restart. On "Shutdown" it should.

> I don't know if this is related but I had a shutdown issue with feisty and gutsy, it was module snd-hda-intel that would hang. (black screen no info) So what I did was went to the script for the actual halt command in /etc/init.d opend the halt script and at the top of it added rmmod snd-hda-int so it unloads that modual at the start of shutdown. Works a charm.

Both to no avail ](*,)

At least when the system halts the heads on my hard drives are parked. I can hear the clicking sound of the heads being parked and the fans are out. So I guess the hardware is safe :confused:

Still extremely annoying though :(:(:(

---

### Post by unebaguettesvp on 2007-10-25
i have had this problem since edgy. the computer will eventually shut down. but you need to give it 5 minutes or so. have you waited that long? be patient and try it.

i've just learned to deal with it. if any of you find a solution, please post it! i believe i read somewhere that this is a linux kernel problem.

---

### Post by Tallman on 2007-10-25
> **unebaguettesvp said:**
> i have had this problem since edgy. the computer will eventually shut down. but you need to give it 5 minutes or so. have you waited that long?

Yeah, I have been giving it a few hours... really!

---

### Post by klainmeister on 2007-10-26
Still nothing? I am somewhat surprised by that. I've searched the forum numerous times and cant find any help. We're screwed!

---

### Post by strabes on 2007-10-26
Does running "sudo halt" or "sudo shutdown -h now" work?

---

### Post by Tallman on 2007-10-27
> **strabes said:**
> Does running "sudo halt" or "sudo shutdown -h now" work?

No, they don't. Result is exactly the same. However, these commands show me a non-graphical screen with all the commands Ubuntu seems to issue before shutting down (sorry for this description, I didn't know how to put it). On this screen, the last messages were about network-manager. That makes me think we've got the same issue as everybody here:

[http://ubuntuforums.org/showthread.php?t=584652]("http://ubuntuforums.org/showthread.php?t=584652")

I haven't tried wicd yet, as suggested in this thread...

Can anyone tell me where I can find the log files Ubuntu writes when shutting down?

---

### Post by Tallman on 2007-10-28
Nobody?

---

### Post by jenhsun on 2007-10-28
Could you tell me your CPU type, 32 or 64bits?

---

### Post by ThomThom on 2007-10-28
I'm having the same issue as well on my computer.

---

### Post by ThomThom on 2007-10-28
When I remove the boot splash I get this upon shutdown:

> 
---
 System is shutting down, please wait...
---

NetworkManager: <WARN>  mn_signal_handler(): caught signal 15, shutting down normally.

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1193573771.092816] nm_print_open_socks() Open sockets List:

NetworkManager: <debug> [1193573771.092816] nm_print_open_socks() Open sockets Done.

NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout experied, or the network connection as broken.

[  226.137045] System halted.


---

### Post by capsh on 2007-10-28
I've upgraded from feisty to gutsy a few days ago, and I have the same problem. no matter what I do the monitor just goes black and nothing else happens. :confused:

---

### Post by ThomThom on 2007-10-28
I just found my issue to be ACPI related. My BIOS is from 2005, but I got a message saying "no DMI BIOS year, acpi=force is required to enable ACPI" during boot.

After I tried force=ACPI it now works fine.

---

### Post by justken on 2007-10-28
I am new to Ubuntu but have been using PCLinuxOS and Sidux for a while.  I  have 7.10 installed (64-bit) and have the same problem with shutting down.  I have followed up the link about replacing the network manager (and followed the instructions found there) but don't seem to be able to get wicd (perhaps not available as a 64-bit module, although website suggests any architecture?).  

The last post from ThomThom, about ACPI, might offer an alternative answer, however.  With the benefit of hindsight, I wouldn't have gone for my current motherboard as a base for linux.  Almost every distribution I have tried has required me to disable ACPI, APIC, APM - or all three.  Bit nervous about forcing ACPI, as I couldn't get the LiveCD to run with it enabled.  Any advice welcome.

Motherboard is an Asus (which I have always found reliable in the past) M2V (seems to have lots of bios problems with linux).  Processor is an AMD 2500 64-bit and memory is 2gig.  Aside from ACPI issues, this configuration works well with Sidux and PCLos - was also fine with Mepis.

Regards,

Ken

---

### Post by jenhsun on 2007-10-28
[https://answers.launchpad.net/upstart/+question/15972](https://answers.launchpad.net/upstart/+question/15972)

---

### Post by Tallman on 2007-10-28
> **jenhsun said:**
> Could you tell me your CPU type, 32 or 64bits?

AMD Athlon XP 2400+, that's 32-bit.

> **ThomThom said:**
> I just found my issue to be ACPI related. My BIOS is from 2005, but I got a message saying "no DMI BIOS year, acpi=force is required to enable ACPI" during boot.

After I tried force=ACPI it now works fine.

Where do you do that?

> **jenhsun said:**
> [https://answers.launchpad.net/upstart/+question/15972](https://answers.launchpad.net/upstart/+question/15972)

That seems like a different issue to me. From the point where my computer hangs, I cannot issue any command, it is just the splash screen with an empty progress bar. Keyboard does not work anymore.

---

### Post by jenhsun on 2007-10-28
I have another source. Check it out
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61")

I guess the problem arise because recently ubuntu or linux want to implement the hibernate or suspend mode. 

Not sure....still looking......

---

### Post by jenhsun on 2007-10-28
> **Tallman said:**
> AMD Athlon XP 2400+, that's 32-bit.



Where do you do that?



That seems like a different issue to me. From the point where my computer hangs, I cannot issue any command, it is just the splash screen with an empty progress bar. Keyboard does not work anymore.

Tallman
Do you want to update your bios from your motherboard manufacture? 
And also check your bios has ACPI enable, etc.

---

### Post by Tallman on 2007-10-28
> **jenhsun said:**
> I guess the problem arise because recently ubuntu or linux want to implement the hibernate or suspend mode. 

That's weird, on a Compaq Presario Desktop...

---

### Post by jenhsun on 2007-10-28
> **Tallman said:**
> That's weird, on a Compaq Presario Desktop...

That's nothing wrong with brand. No matter yours is Dell or IBM.

---

### Post by unebaguettesvp on 2007-10-29
hi. what exactly does the "acpi=force" option do when you add it to menu.list?

---

### Post by ThomThom on 2007-10-29
It forces ACPI to be used even the system don't really want to.

Like in my case, my BIOS didn't report any year, which made Ubuntu to not use ACPI. (From what I gather, ACPI is disabled on BIOS's dated before 2000).

---

### Post by unebaguettesvp on 2007-10-29
ok. one more stupid question... in dumbed down terms what is acpi?

---

### Post by ThomThom on 2007-10-30
I've not actually looked it up until now. I figured it had something to do with power management.

> 
The Advanced Configuration and Power Interface (ACPI) specification is an open industry standard first released in December 1996 developed by HP, Intel, Microsoft, Phoenix and Toshiba that defines common interfaces for hardware recognition, motherboard and device configuration and power management. According to its specification[1], "ACPI is the key element in Operating System-directed configuration and Power Management (OSPM)".

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

---

### Post by Tallman on 2007-10-31
The problem is still there, after flashing my BIOS and adding

```
acpi=force
```

to /boot/grub/menu.lst.

---

### Post by unebaguettesvp on 2007-10-31
same here. thanks for the suggestion anyway ThomThom.

---

### Post by Railsbuntu on 2007-11-06
I kinda have a similar problem. in my case it seems to be due to apache and citadel not being friends. here is my thread: [http://ubuntuforums.org/showthread.php?t=602278]("http://ubuntuforums.org/showthread.php?t=602278")

---

### Post by justken on 2007-11-17
I got a bit fed up with trying to solve the problem and played with Fedora 8 for a while before deciding to come back and have another go.  Much happier with the install second time around (once I wrestled with Java a bit) and I have now been able to resolve the shutdown problem on my PC.  I was getting the same hang and message about network manager, although in reality I think it is about the bios and cpufreq (see previous post in this thread).

There are probably better technical solutions but I used acpi=off in the boot options (Live CD wouldn't start without doing that anyway).  Once installed, I tried to shutdown and  the computer hung as usual.   I then restarted and disabled powernowd in the services menu, then edited menu.lst to remove the acpi=off line (forcing acpi hadn't worked for me previously).  Now it shuts down as it should.

Next step is to find an alternative method of using the stepping abilities of my AMD X2 3800 processor. 

Not particularly elegant, as I said, but it worked for me.

Regards,

Ken

---

### Post by MrSpiffdifilous on 2007-11-18
i've been having a similar issue. i click the power button in the upper right and the bars just disappear. What i've been doing is:

ctrl+alt+F4
then you have to login again
after, type:
> sudo shutdown now

it will end the session
then type:
> gdm

this should start a new xsession and allow you to use the shutdown button at the login screen. hope this helps a little

EDIT: I know this doesnt solve the issue but I've just been doing it to shutdown until i have the patience to reinstall

---

