---
title: "Wake up using USB Keyboard or mouse?"
date: 2008-03-01
forum: General Help
---

### Post by rcsdnj on 2008-03-01
Hi,

I'm happy to see that, since Gutsy, Ubuntu started supporting my hardware fine, resuming from suspend-to-ram without random lockups or other problems like this. Great advance.

The only remaining problem is: how can I wake up the computer (in ACPI S3 state) using my keyboard or mouse? The only option I currently have is using the power button. It's not a big problem, of course, but I'd prefer it to be more natural, though, just like when the monitor (only) sleeps. On Windows, this feature works without problem.

I've tried searching, but I wans't lucky enough to find interesting results. On Ubuntu Forums, I only found some answers about wake-on-lan. So, did anyone try to solve this little problem, and wants to share the experience?

Or... do you think I should just report this as a bug?

---

### Post by geraldm on 2008-03-01
USB mouse and keyboard should have the capability to resume from suspend, and USB modems may also need to resume.  The USB spec is quite detailed, and has different categories, global suspend and selective suspend.  It gets more complex, as the device notifies its hub, which then  must complete the process.  Also, the hub could be suspended, and it must also complete its wakeup.  If you are going to test, I would suggest first testing without any hubs between the computer and the tested device.  

A selective suspend is initiated by software, that sends a control transfer to the hub (which could be the root hub) with a SetPortFeature(PORT_SUSPEND) request.  The hub responds to this request by placing the port in the suspended state.  You would need to find out how to initiate this request.  

Gerald

---

### Post by tgalati4 on 2008-03-01
Sometimes the BIOS has settings to allow USB devices to Wake from Suspend, but you have to turn it on.

---

### Post by rcsdnj on 2008-03-06
Hi, thank for your answer. geraldm, I think I wasn't clear on my question: my keyboard/mouse works fine after resuming; the point is, I'd like to be able to use them just to make the computer come back from sleep state, instead of pressing the power button.

tgalati4, my brother's computer has this option in the BIOS as you said, but unfortunately it made no difference for Ubuntu. 

Anyway, I think I've found the answer. There's a file (or device) called /proc/acpi/wakeup

if you check its content using:

```
cat /proc/acpi/wakeup
```

you'll se an output like

```

Device  S-state   Status   Sysfs node
SLPB      S4    *enabled
P32       S4     disabled  pci:0000:00:1e.0
ECIR      S4     disabled  pnp:00:08
UAR1      S4     disabled  pnp:00:09
ILAN      S4     disabled  pci:0000:00:19.0
PEGP      S4     disabled  pci:0000:00:01.0
PEX0      S4     disabled  pci:0000:00:1c.0
PEX1      S4     disabled  pci:0000:00:1c.1
PEX2      S4     disabled  pci:0000:00:1c.2
PEX3      S4     disabled  pci:0000:00:1c.3
PEX4      S4     disabled  pci:0000:00:1c.4
PEX5      S4     disabled
UHC1      S3     disabled  pci:0000:00:1d.0
UHC2      S3     disabled  pci:0000:00:1d.1
UHC3      S3     disabled  pci:0000:00:1d.2
UHC4      S3     disabled
EHCI      S3     disabled  pci:0000:00:1d.7
EHC2      S3     disabled  pci:0000:00:1a.7
UH42      S3     disabled  pci:0000:00:1a.0
UHC5      S3     disabled  pci:0000:00:1a.1
UHC6      S3     disabled  pci:0000:00:1a.2
AZAL      S3     disabled  pci:0000:00:1b.0

```

I still don't know which is each of these things (anyone does), but I read that if you do, as an example: 

```
echo UCH1 > /proc/acpi/wakeup
``` 

it toggles its state. According to some posts I saw, in some computers the device to be activated would be "USB0, 1... etc.". In my case, it would be UHC1, 2... etc.

I've tried this, and it worked for me. Anyway, since I think this feature should be the default, I reported it as a bug, here: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/199006](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/199006)

Any other opinions or ways to solve this are still welcome :)

---

### Post by alexforcefive on 2008-03-07
hi guys, I'm having a bit of trouble with this command. When I type ```
cat /proc/acpi/wakeup
``` I get the expected result. However when I try ```
sudo 'echo USB1 > /proc/acpi/wakeup'
``` I just get a "command not found" error. I'm sure this is a syntax problem, but I honestly can't figure it out. Any ideas?

---

### Post by rcsdnj on 2008-03-07
alexforcefive, I think it should work trying this way:

```

sudo -s
echo USB1 > /proc/acpi/wakeup

```

I don't know the ' symbol meaning, so I don't know the reason for the "command not found" message. But I guess if you put just " sudo echo USB1 > /proc/acpi/wakeup ", it wouldn't work too, because it will redirect the sudo's output to the wakeup file, not the echo command's output.

---

### Post by alexforcefive on 2008-03-07
You're a genius, thanks so much! 

I stole the quote mark thing from another post on the subject, you just get "permission denied" without it. Your method worked perfectly, though. thanks again

---

### Post by highfructose327 on 2008-03-11
I was able to return from suspend with the keyboard using:  ```
echo "USB0" > /proc/acpi/wakeup
``` but when I restart my computer it is disabled again. This is not a big issue  but I was curious if anyone found a way to get it to be enabled even after a reboot? or anyone is having a similar issue? I tried to use a script to enable it on start up but no luck it was:
```
#!/bin/bash
 echo "USB0" > /proc/acpi/wakeup
```
I thinks that is because to run in it I have use sudo su then run:  ```
echo "USB0" > /proc/acpi/wakeup
``` , I am stuck at this point, thanks

---

### Post by rcsdnj on 2008-03-12
highfructose327, did you try adding as a /etc/init.d script?  I think if you added your script to your gnome-session startup programs, you'll have problems because it will require a password and you won't be able to put it (since you don't have the console showing... and even if had, I think you wouldn't want).

I think scripts added on /etc/init.d run as root. If you have tried adding the script this way and it didn't work, maybe there's another problem, maybe the "echo" command doesn't behave as expected when running inside a script, I don't know... please, let us know.

Tonight, when I'm home, I'll try to set up the wakup devices automatically on my computer too, and I should post some comments here about what I got.

---

### Post by highfructose327 on 2008-03-12
rcsdnj, I tried adding the script(wake.sh) to /etc/init.d then a restart no luck! So just  out of curiosity I ran sudo  /etc/init.d/wake.sh  it did enable USB0 so the echo worked in a script but I had no luck on start up. I may have missed something.  Hope you have better luck! I will work with more after class  thanks for the idea. looking forward to see what you get.

---

### Post by rcsdnj on 2008-03-12
highfructose327, I think this may solve the problem: [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by highfructose327 on 2008-03-12
rcsdnj,
That was it! I did  ```
sudo update-rc.d wake.sh defaults
``` and then```
 cd  /etc/init.d/ 
``` after that ```
sudo chmod +x wake.sh
``` wake.sh being what I choose to name the script did a restart and it was enabled on start up. Thanks rcsdnj

gotta go now I am late:)

---

### Post by NEI on 2008-03-17
My sleep doesn't work anymore when enabling USB0. And it enables all USB entries I have How can I find out which device prevented sleep from wprking? Or which device woke up the pc?

---

### Post by highfructose327 on 2008-03-17
NEI, 
 have you tried 

```
 lsusb
```

 to get an output of USB devices connected, this is mine.

```
~$ lsusb
Bus 005 Device 026: ID 05ac:1260 Apple Computer, Inc. 
Bus 005 Device 025: ID 0644:0200 TEAC Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 027: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 026: ID 413c:2005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

if you have not disabled USB0 you can just use this again to do so

```
sudo echo "USB0" > /proc/acpi/wakeup
``` 

of course if you added the script USB0 will be enabled on start up again.

Good luck!

---

### Post by NEI on 2008-03-18
yes, i have to disable it. Else sleep does not work. And i can only enable/disable all USBx in /proc/acpi/wakeup. I cannot select i.e USB3. This would also enable USB0, USB2, USB4, USB5. Unfortunately I am not at my machine, so I cannot post my log.

---

### Post by rcsdnj on 2008-03-18
NEI, did you try disconnecting your mouse? I know it may sound radical, but I've seen some mouses which have some kind of "noise", preventing the cursor from being really 100% "stopped". It's just an hypothesis, I really don't know what's happening.

---

### Post by NEI on 2008-03-18
Ok, i solved it: Had to add ehci_hcd to the modules to be unloaded  when suspending and loaded after resume in  /etc/default/acpi-support. It is described here: 

[http://ubuntuforums.org/showthread.php?t=373268&highlight=getXuser&page=2](http://ubuntuforums.org/showthread.php?t=373268&highlight=getXuser&page=2)

Now it works! :-)

Now i have to work at the next problem:
[http://ubuntuforums.org/showthread.php?t=724391](http://ubuntuforums.org/showthread.php?t=724391)

---

### Post by trojanfoe on 2008-05-27
I think you need to investigate the acpid scripts - of which there are very many!  You need to arrange for /proc/acpi/wakeup to be written by one of the scripts (or a new one) in /etc/acpi/resume.d so that the wake-up settings will always be reloaded.  Alternatively you could set the wake-up during the pre-suspend actions (/etc/acpi/suspend.d), which seems a little more logical to me.

Haven't tried this myself though; I use a script to suspend (a VDR shutdown script) and set the triggers explicitly in that script.

HTH,
Andy

---

### Post by Rebelli0us on 2008-07-18
Wake up from suspend via keyboard is still a problem. I did:

 cat /proc/acpi/wakeup

And I got:

Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:10.0
XVRA	  S5	 disabled  pci:0000:00:04.0
XVRB	  S5	 disabled  
XVRC	  S5	 disabled  
UAR1	  S5	 disabled  pnp:00:08
UAR2	  S5	 disabled  pnp:00:09
USB0	  S4	 disabled  pci:0000:00:0b.0
USB2	  S4	 disabled  pci:0000:00:0b.1
AZAD	  S5	 disabled  pci:0000:00:10.1
MMAC	  S5	 disabled  pci:0000:00:14.0
MMCI	  S5	 disabled  

Then I typed:

echo USB0 > /proc/acpi/wakeup

And I got:

Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:10.0
XVRA	  S5	 disabled  pci:0000:00:04.0
XVRB	  S5	 disabled  
XVRC	  S5	 disabled  
UAR1	  S5	 disabled  pnp:00:08
UAR2	  S5	 disabled  pnp:00:09
USB0	  S4	 enabled   pci:0000:00:0b.0
USB2	  S4	 disabled  pci:0000:00:0b.1
AZAD	  S5	 disabled  pci:0000:00:10.1
MMAC	  S5	 disabled  pci:0000:00:14.0
MMCI	  S5	 disabled  


I seems OK, but wakeup from keyboard works ONCE or only for the session, then it stops working after you reboot. Is there a permanent solution? And I'm really uncomfortable typing system config commands that I don't understand.

Also "wakeup" file is still showing "0 bytes" in the File Browser, so maybe nothing is written with the sudo command. Who is Sudo anyway? ;)



...

---

