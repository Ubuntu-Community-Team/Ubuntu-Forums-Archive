---
title: "Cannot mount Windows 10 NTFS after Microsoft's recent updates"
date: 2018-01-14
forum: General Help
---

### Post by Paddy Landau on 2018-01-14
It used to be dead easy to mount Windows NTFS drives from Ubuntu (or Lubuntu in my case).

Since the latest updates from Microsoft, I can no longer do this. I get the following error message.
[ATTACH=CONFIG]278194[/ATTACH]
Going into Windows, I noticed that Fast Boot had been turned back on (why? Who knows why Microsoft does what it does). So, I turned it off again:

Control Panel > Hardware and Sound > Power Options > Change what the power buttons do > Change settings that are currently unavailable > Shutdown settings > Turn on fast startup [turn it off]

After restarting into Lubuntu, the error message remained. So, I ran a Windows check-disk and again restarted into Lubuntu.

Still the same error message :-(

What can I do to reinstate access to my Windows 10 drive from Lubuntu, please?

---

### Post by DuckHook on 2018-01-14
My contribution is pretty much useless to you because I haven't run Windows in years, but just by way of a general observation: the latest round of updates has been murderously hard on all developers. They've basically been forced to put out patches dealing with very low level vulnerabilities on short notice, under immense pressure and with practically no sleep. I would not be surprised if some things are broken. We can even excuse Microsoft this time.

[LIST=1]
[*]Perhaps a bug continues to flag Windows hibernation as "on" when it is not?
[*]Perhaps the Windows process for turning off fastboot is, in fact, broken (it remains on)?
[*]Try turning off fastboot, rebooting immediately into Windows, then checking again to see if it is truly off.
[*]Can you read it if mounting read-only?
[/LIST]
Aside from above, I have no further ideas. When it comes to Windows or dual boot these days, I'm a complete dummy.

---

### Post by HermanAB on 2018-01-14
Howdy,

Due to Windows fast boot and suspend issues, it is best to use a separate disk partition or USB stick to transfer files between the two systems.

My preferred method is to install Windows in a virtual machine on Linux.  Then Windows can run in a window on Linux and file sharing can be done over anonymous FTP or through the VM file sharing service.

---

### Post by mastablasta on 2018-01-15
scan the drive with SMART tools, do the "deep" check disk scan. try and mount it read only.

---

### Post by dragonfly41 on 2018-01-15
I see this error message on an ntfs partition, for files shared between Windows 10 and Ubuntu.

In Ubuntu install ntfsfix and then when you next see the error run the command

```
sudo ntfsfix /dev/sda3
```

---

### Post by Paddy Landau on 2018-01-15
Thanks, everyone, for your advice.

> **DuckHook said:**
> Perhaps a bug continues to flag Windows hibernation as "on" when it is not?
Hmm, I wouldn't know how to check or fix that. In theory, restarting Windows should clear this.
> **DuckHook said:**
> Perhaps the Windows process for turning off fastboot is, in fact, broken (it remains on)? Try turning off fastboot, rebooting immediately into Windows, then checking again to see if it is truly off.
I have done this. It seems to have remained off.
> **DuckHook said:**
> Can you read it if mounting read-only?
Yes, I can do so. Unfortunately, I transfer files from one to the other, so I need read-write.

> **HermanAB said:**
> Due to Windows fast boot and suspend issues, it is best to use a separate disk partition or USB stick to transfer files between the two systems.
I think that I may use this method: I'll reduce the Windows partition and create a new NTFS partition just for the purpose. It seems so silly to have to do this, though!

> **HermanAB said:**
> My preferred method is to install Windows in a virtual machine on Linux.
I would agree, if my computer had the RAM for it!

> **mastablasta said:**
> scan the drive with SMART tools, do the "deep" check disk scan. try and mount it read only.
Sorry, what are the SMART tools? I've run the full Windows check-disk; is that what you mean by "deep"?

> **dragonfly41 said:**
> I see this error message on an ntfs partition, for files shared between Windows 10 and Ubuntu.

In Ubuntu install ntfsfix and then when you next see the error run the command
Yes, it's the Windows C: drive. I am hesitant to run [FONT=lucida console]ntfsfix[/FONT] when I can run the native Windows check-disk on the partition.

**Summary**

Unless I find a fix, I'll do as HermanAB suggested and create a separate partition just for the purpose. It does mean double-copying files at times, but it will have to do.

Thanks again for all of the ideas.

---

### Post by dragonfly41 on 2018-01-15
> [COLOR=#000000]Yes, it's the Windows C: drive. I am hesitant to run [/COLOR][COLOR=#000000][FONT=&quot]ntfsfix[/FONT][/COLOR][COLOR=#000000] when I can run the native Windows check-disk on the partition.[/COLOR]
I should have clarified that I created a dedicated ntfs partition named SHARE on my single hard drive and another ext4 for Ubuntu.  
But that is what HermanAB suggests.
The advantage of using ntfsfix is that you don't need to reboot into Windows to fix the shared partition for use in Ubuntu (where you see the error message).  Horses for courses.

---

### Post by Paddy Landau on 2018-01-15
Ah, I've found the answer!

I had to disable not only Fast Boot but also Hibernate (why? Who knows why Microsoft does what it does).

In Windows, open Command Prompt (Admin) or PowerShell (Admin) and enter this command:
```
powercfg /h off
```
It works now.

---

### Post by mastablasta on 2018-01-15
> **Paddy Landau said:**
> 
Sorry, what are the SMART tools? I've run the full Windows check-disk; is that what you mean by "deep"?


SMART are drive diagnostic tools. they provide a quick reference to the state of the drive. although they are not 100% reliable, they can show any disk errors.

WD (Data Lifeguard Diagnostics): 
[https://support.wdc.com/downloads.aspx?p=3](https://support.wdc.com/downloads.aspx?p=3)
[https://support.wdc.com/knowledgebase/answer.aspx?ID=940](https://support.wdc.com/knowledgebase/answer.aspx?ID=940)

Seagate: [https://www.seagate.com/gb/en/support/downloads/seatools/](https://www.seagate.com/gb/en/support/downloads/seatools/)

there are two check disk options. one is the quick one one is full that lasts quite a bit longer. check disk check for file system errors (NTFS and FAT), while SMART tools check for drive errors. So to eliminate these causes you would run both tests. but as i said SMART can show OK status, but disk could still be close to fail. however if there are no other symptoms then it is probably still OK. for example SMART showed my drive as being in relatively good condition, but the drive was clicking and had problems starting up. it was an error not on the drive itself, but probably of the drive controller.

in any case passing these tests would mean disk and file systems are ok, then the next step is trying to mount it in read only. and then if it works i would mount it as read and write and if still it doesn't work then use the ntfsfix or try to force it to work :)

---

### Post by mastablasta on 2018-01-16
> **Paddy Landau said:**
> 
I had to disable not only Fast Boot but also Hibernate (why? Who knows why Microsoft does what it does).


that's because Hibernate locks the drive. it has to do it so it can safely restore the session (files etc.) back to RAM.

from: [https://askubuntu.com/questions/3369/what-is-the-difference-between-hibernate-and-suspend](https://askubuntu.com/questions/3369/what-is-the-difference-between-hibernate-and-suspend)

> 
[COLOR=#111111][FONT=Ubuntu]**Suspend** does not turn off your computer. It puts the computer and all peripherals on a low power consumption mode. If the battery runs out or the computer turns off for some reason, the current session and unsaved changes will be lost.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**Hibernate** saves the state of your computer to the hard disk and completely powers off. When resuming, the saved state is restored to RAM.[/FONT][/COLOR]


---

### Post by Paddy Landau on 2018-01-16
> **mastablasta said:**
> that's because Hibernate locks the drive…
Ah, but I wasn't hibernating! I was restarting, which — in theory — closes *everything*.

---

### Post by DuckHook on 2018-01-16
> **Paddy Landau said:**
> Ah, but I wasn't hibernating! I was restarting, which — in theory — closes *everything*.
According to my understanding, it actually doesn't—not in Windows. Starting with Windows 8 (I believe?) Windows default behaviour is to hibernate. This is because it takes modern Windows so long to boot up that they have to cheat by using hibernation. Since MS has always assumed that Windows is the only OS on the drive, it hasn't much cared what difficulties this causes other OSes.

I thought turning off fastboot also turns off hibernation, but the latest update may have nerfed that.

---

### Post by Paddy Landau on 2018-01-16
> **DuckHook said:**
> … Windows default behaviour is to hibernate. This is because it takes modern Windows so long to boot up…
Yes, you're not kidding about how long it takes to boot up! Thanks for the explanation.

I wonder, then, what the difference is between Fast Boot and Hibernate? Maybe an explicit Hibernate leaves you logged in, while an implicit one logs you out?

---

### Post by DuckHook on 2018-01-16
> **Paddy Landau said:**
> Yes, you're not kidding about how long it takes to boot up! Thanks for the explanation.

I wonder, then, what the difference is between Fast Boot and Hibernate? Maybe an explicit Hibernate leaves you logged in, while an implicit one logs you out?
I've no idea. My knowledge of Windows is all second-hand, gleaned from following the trials and tribulations of the hard-pressed members of this forum (like yourself! :p ).

Glad you solved it in any case.

---

