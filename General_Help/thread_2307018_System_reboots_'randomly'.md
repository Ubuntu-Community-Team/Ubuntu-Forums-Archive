---
title: "System reboots 'randomly'"
date: 2015-12-21
forum: General Help
---

### Post by Jakub_Amanowicz on 2015-12-21
Hello there!
At the beginning I just want to let you know that I'm pretty fresh user of Linux in general so the question may be dumb - I don't really know.

I encounter a unexpected reboot each time the given scenario takes place:
1. I open a .doc file using LibreOffice
2. The program prompts a message regarding 'Recovering Data'. It does not matter if discard it or not - the behaviour afterwards is the same.
3. The file opens without any problems.
4. I move the document windows to the side so it can cover only half of the screen and...
5. The system reboots and I get the following message on the blackscreen just before the boot:

```

fcsk from util-linux 2.26.2
/dev/sda1: clean, 453471/18661376 files, 12430780/74635009 blocks
[  OK  ] Started Light Display Manager ,
[  OK  ] Satrted ACPI event daemon ,
[ 8306.606698 ] radeon 0000:01:00.0: VCE init error (-110) , 
[ 8376.779732 ] radeon 0000:01:00.0: VCE init error (-110) ,
[ 8451.103352 ] radeon 0000:01:00.0: VCE init error (-110) ,
[ 8522.445620 ] radeon 0000:01:00.0: VCE init error (-110) ,

```

I'm pretty sure this kind of error happened to me before in some other situation that the LibreOffice one but lately I've encountered given scenario many times.

I would appreciate any help - I suspect my graphic card but that's just a guess.
Thanks in advance!

---

### Post by grahammechanical on 2015-12-21
There are a couple of things that you need to know. When Linux loads it prints systems messages to the screen. On Ubuntu these are usually suppressed or hidden by a splash screen. What you are seeing are messages from the Linux loading session.

fcsk = file system check. This is a usual task and it is showing that sda1 is clean. There may or may not be a problem with your graphic adapter. Does the system load at the correct screen resolution?

When we shut down the OS with a Libreoffice document still open the next time we start Ubuntu & load Libreoffice it will attempt to recover the document from the backups that Libreoffice makes.

The real issue here is the system rebooting when you resize the Libreoffice window. As the forced shut down is happening each time you resize the Libreoffice document you are getting a re-occurrence of Libreoffice recovery of the document. It is a loop. Break the loop.

Next time accept the recovered document & close Libreoffice. Then shut down Ubuntu and restart. Shut down & restart at least twice to establish a good loading & shut down profile.

And then attempt to recreate the forced shut down by resizing different application windows. You may have a problem with the graphic adapter. Is it over heating? Is its fan still working?

I have installed Psensor. An icon sits in the top panel and with a click I get a drop down menu showing fan speeds and temperatures for motherboard, CPU, disk drives & GPU. It is useful for keeping an eye on overheating.

Regards.

---

### Post by Jakub_Amanowicz on 2015-12-22
Thank you for your answer!

> **grahammechanical said:**
> 
Does the system load at the correct screen resolution?
Is it over heating? Is its fan still working?

Yes, no and yes :)

I'll follow your instructions and I'll also look into the program you've suggested.

Take care!

---

### Post by Bucky Ball on 2015-12-22
There was maybe an unexpected crash and shutdown some time when a Libreoffice doc was open and that started the ball rolling.

A random thought, but try this. Boot the machine. Launch Libreoffice. Recover that document then immediately close it. Close Libreoffice. Close everything so you just have a desktop, nothing running.

Now, go for a restart. At the GUI of options, you should have logout, restart, shutdown, etc., and down the bottom a tick box with 'save session etc. ...' Tick it.

Reboot and when at the desktop this time, go for restart and untick that box. Reboot. See if it is any different.

May not do anything but my theory is that closing the document and Libreoffice cleanly might make a difference. Then again, might not.

[QUOTE=grahammechanical]The real issue here is the system rebooting when you resize the Libreoffice window. [/QUOTE]

Certainly seems to be and where I'd start looking. :)

---

### Post by ian-weisser on 2015-12-22
> **Jakub_Amanowicz said:**
> 5. The system reboots and I get the following message on the blackscreen just before the boot:

```

fcsk from util-linux 2.26.2
/dev/sda1: clean, 453471/18661376 files, 12430780/74635009 blocks
[  OK  ] Started Light Display Manager ,
[  OK  ] Satrted ACPI event daemon ,
[ 8306.606698 ] radeon 0000:01:00.0: VCE init error (-110) , 
[ 8376.779732 ] radeon 0000:01:00.0: VCE init error (-110) ,
[ 8451.103352 ] radeon 0000:01:00.0: VCE init error (-110) ,
[ 8522.445620 ] radeon 0000:01:00.0: VCE init error (-110) ,

```


Question: Is your sytem really rebooting (blinky keyboard lights, manufaturer logo, GRUB, splash page, login screen)?
Or is your screen merely changing to text for a moment, then returning to the login screen (no blinky keyboard lights, no manfacturer logo, no GRUB)?

That console message seems to indicate a video card fault or video card driver fault, not overheating. Those 8000-series numbers are seconds since poweron.
That system has been powered on for over two hours, and is having kernel-level video errors about a minute apart, the final about five minutes later.

---

