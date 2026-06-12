---
title: "New System Crashes -- Unknown Cause -- Troubleshooting Help"
date: 2022-01-26
forum: General Help
---

### Post by coraxwolf on 2022-01-26
I've replaced windows on my desktop with Ubuntu 20.04.  This was after replacing a failed hard drive, so it's on a new hard drive and a fresh install of Ubuntu.  I've had this running for nearly a month now and it will randomly lock up on me.  The entire system locks up and I can't get it to respond to pings nor can I ssh into the machine from other computers.  The machine will even show as off-line to my wifi router.

I don't see anything standing out in the logs.  It will happen when the machine is left alone or in the middle of an activity.  The mouse will still move around the screen but clicking has no effect and not response from pressing keys on the keyboard.  nothing shows in the /var/crash folder after a reboot, but I do see entries in the journal about whoopsie not being able to reach daisy.ubuntu.com.  

I am at a loss as to how to track down what the issue is for this.  I can go days without a lockup and then other times I can make it an hour between lockups.

This issue is getting frustrating for me.  Any help or hints towards tracking down the issue would be greatly appreciated.

System Info:
Gigabyte AB350 Gaming 3 Motherboard
AMD Ryzen 5 1600 6-core 12 thread cpu
NVidia GeForce GTX 1060 3GB Video Card
16GB RAM DIMM DDR4 @ 2400MHz -- 2 8 GB Bank 0 & 2
AR9287 Wireless NIC (PCI-Express)
Seagate BarraCuda 1TB 3.5 SATA HDD

---

### Post by oldfred on 2022-01-26
Whoopsie is part of the error reporting system.
[https://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it](https://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it)

It should pop up with a message on whether to report an error or not (or used to).
And that should have a new log file error.

Review log files
sudo egrep -i 'warn|error' /var/log/*g

Also change settings so you can use full RESIUB to shutdown, so if an operation is in process a forced shutdown does not cause file system issues and then you also need fsck on ext4 file system(s).

sudo nano /etc/sysctl.d/10-magic-sysrq.conf
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

You could also open top or htop and keep it running in terminal just to track what is running.

---

### Post by coraxwolf on 2022-01-26
Thanks for the information.  I was wondering why I could never get the magic sysrq keys to work.  They still don't work using my moonlander keyboard even though xev detects the key press,  but a normal keyboard plugged in does work.

I looked back at logs around the last time I had the issue.  Didn't notice anything that would explain the issue precisely.  

I did find a couple of things that I have questions about.  On the reboot (and looks like every boot) I get entries in the kern.log of *PM: hibernation: Registered nosave memory* -- get a long list of these followed by a memory address.  I don't believe I have hibernation or power saving turned on.  The monitor will suspend after 10 hours but the system never goes to sleep or shuts down.  Any googling of those messages brings up issues with recovering from a hibernation.

---

### Post by oldfred on 2022-01-26
I have never used hibernation.
But hibernation uses swap file. Is it correctly configured.

Do you have this file? I have Kubuntu and do not have that file at all. Should be swap file if you have it.
cat /etc/initramfs-tools/conf.d/resume

---

### Post by coraxwolf on 2022-01-26
I checked and don't have that file.  I assume it's not setup since it doesn't hibernate.  The nosave memory is what caught my eye.  doubt it's related to my issues as they can happen while actively using the machine.

awaiting the next crash to see what shows up in the logs right before. have htop running now so i can see if anything looks off before rebooting.

---

### Post by coraxwolf on 2022-01-28
I had another freeze.  The system didn't respond to the magic sysrq keys.  I am able to do them when the system is acting normally, but when it locked up i couldn't.  

I was just browsing the web when it locked up. nothing looked odd on htop at the time.  I also installed atop and looked over the log file it produced and at the time of the crash the system was writing to a file on disk but didn't see anything to indicate what locked it up.  I am doing a smart test on the drive to make sure this drive is functioning correctly without errors.  

Reviewing the logs for warn and errors only show warnings that happen at boot. None of them seem to indicate any real problem (most are about missing devices, like bluetooth and network not being ready yet).  There's nothing showing at the time of the freeze.

Looking through the journalctl for the last boot right before the freeze the wifi link seemed to have gone down.  I get wpa_supplicant CTRL-EVENT-BEACON-LOSS messages and then the whoopsie can't reach site daisy.ubuntu.com.  Even if whoopsie can't report the error it should still create a file in the /var/crash directory? nothing is appearing there.   I disabled the powermanagement on the wifi card so it shouldn't be trying to go to sleep.  Not sure why it seems to drop connection so often.   I see alot of the beacon-loss events in the journal log.  Though I was on the web and viewing pages without issue at the time.

Here is the output from journal at the time of the freeze:

Jan 28 10:22:42 ubuntu systemd[1]: NetworkManager-dispatcher.service: Succeeded. 
Jan 28 10:22:33 ubuntu whoopsie[1231]: [10:22:33] online 
Jan 28 10:22:32 ubuntu whoopsie[1231]: [10:22:32] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1 
Jan 28 10:22:32 ubuntu whoopsie[1231]: [10:22:32] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1 
Jan 28 10:22:32 ubuntu whoopsie[1231]: [10:22:32] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1 
Jan 28 10:22:32 ubuntu whoopsie[1231]: [10:22:32] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com) 
Jan 28 10:22:32 ubuntu NetworkManager[902]:   [1643386952.6534] manager: NetworkManager state is now CONNECTED_GLOBAL 
Jan 28 10:22:31 ubuntu whoopsie[1231]: [10:22:31] offline 
Jan 28 10:22:31 ubuntu whoopsie[1231]: [10:22:31] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com) 
Jan 28 10:22:31 ubuntu dbus-daemon[901]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher' 
Jan 28 10:22:31 ubuntu systemd[1]: Started Network Manager Script Dispatcher Service. 
Jan 28 10:22:31 ubuntu dbus-daemon[901]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.13' > 
Jan 28 10:22:31 ubuntu systemd[1]: Starting Network Manager Script Dispatcher Service... 
Jan 28 10:22:31 ubuntu NetworkManager[902]:   [1643386951.5393] manager: NetworkManager state is now CONNECTED_SITE

---

### Post by ActionParsnip on 2022-01-28
May want to test your RAM health too.

---

### Post by coraxwolf on 2022-01-28
I can't manage to get the memtest86+ to show on the gurb memu

---

### Post by coraxwolf on 2022-01-28
Ended creating a memtest86 (free) usb boot drive and did a memory test that way.  

Both disk and memory tests reported no errors.  

Not sure what to look into next.

---

### Post by coraxwolf on 2022-02-02
I am still having crashes.  They now seem to happen about every 2-3 days.  The only thing that is contestant between them is the wifi signal loss (CTRL-EVENT-BEACON-LOSS) event.  Though that seems to happen about every 10 minutes. 

Not seeing any errors or warnings that don't come up as things you can ignore (they seem to be warnings during boot).  None of them happen around the time of the crashes.

Since the system fails to respond to anything, keyboard input (SysRQ key doesn't work during a crash but does when not crashed) and pings and ssh attempts file to respond.  Wifi router shows the machine as offline and nmap reports the host as down.  This seems to be a full crash and not an issue with just xorg or the windows manager freezing/crashing?

With the lack of errors and warnings is there another location to hunt to clues as to the cause of this issue?

---

### Post by Autodave on 2022-02-02
Power supply issue?  Possibly.  Also, are you using any USB hubs?  Powered hubs can cause all kinds of weird issues.  If you have more than a keyboard and mouse hooked up, try unplugging everything else and see what happens.  If that cures your issue, suspect and powered hub first.  Then, go after the power supply......sounds like it is losing the 5V line or at least that line is going too low to be recognized.  (When it does die, turn your mouse over and see if the laser is still illuminated.  I had a machine once where I had to use an old roller ball mouse on it until I got a power supply for it!)

---

### Post by coraxwolf on 2022-02-02
I only have 3 devices plugged into it.  a Keyboard, mouse, and a web cam (not really used often).  They keyboard and mouse stay lite (keyboard is back lite and the mouse is one of those rgb ones).  Would the machine stay in a powered state if there was an issue with the power supply?  Wouldn't it cause the system to power down?

Wouldn't an issue with the power supply generate some kind of error in the logs?

---

### Post by Autodave on 2022-02-03
Your power supply puts out different voltages for different things inside the computer.  The 5V line runs USB powered items.  It can also run any SSD drives.  Spinner drives are powered by 12V line.  Memory is powered by less than 5V.

---

### Post by coraxwolf on 2022-02-03
The usb devices I use are all directly connected to the tower in the back.  I don't know that any of those ports go through a hub internally.  
Don't have an ssd in this machine only a new sata baracuda 3.5 hdd.  

Been monitoring the wifi adapter and don't see any unusual power fluctuations.  it stays between -54 dBm and -60 dBm.  This machine is off in a corner across the apt from the router so expect it to have a bad signal.  That may be why I see so many beacon drops.  Though I've found a few of other people reporting wifi signal drops issues with Ubuntu 20.04 and Qualcomm wifi cards.

I've had 8 more crashes in the last 24 hours :( .  Running off the live usb stick to see if it happens on this.  

I had no issues when I had windows even with the dying hard drive.  Fear this may be an issue with something in my computer being for windows only and not liking Ubuntu.  Hope that's not the case as I'd hate to have  to go  back to windows.

---

### Post by oldfred on 2022-02-03
I have a USB to SATA adapter.
It worked extremely well for an old SSD.
But my HDD would not even be seen. USB did not have enough power to spin up HDD.
That will depend on your system and what power it can output to USB and power needs of HDD. 
New systems with newer ports like USB-C may have higher power output.

---

### Post by coraxwolf on 2022-02-03
the hard drive is connected to the sata port on the mother board.  Right now I am using a 128G usb ssd drive to run the live ubuntu cd on (this is plugged into one of the 4 usb ports on the front of the tower).  my normal setup is on the internal 1TB hdd.  The smarttool reports shows no errors on it and nothing to indicate a file access error.  Mem test didn't turn up any errors either.

---

### Post by coraxwolf on 2022-02-03
I crashed on the usb stick too.  
I did notice a new issue in the journal from my earlier crash.

Smartmon is reporting temp changes 194 and 190

> Feb 03 12:33:17 ubuntu smartd[857]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 26 to 25 
Feb 03 12:33:17 ubuntu smartd[857]: Device: /dev/sda [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 74 to 75

Looking at turning on smartd to report any changes as they happen.  That event happened at 12:33 and the system crashed at 12:35.

---

### Post by oldfred on 2022-02-03
Have you cleaned fans & checked to make sure they are working? 
Inlet vents on my system sitting on floor would get lots of dust which I had to vacuum out regularly.

---

### Post by dragonfly41 on 2022-02-04
Looking back to post#1 I read ..

[COLOR=#000000]16GB RAM DIMM DDR4 @ 2400MHz -- 2 8 GB Bank 0 & 2

Since you have been inside your machine is it reasonable to think that you might have added a new 8GB memory
card? I guess this since mine started at 8GB. 

Perhaps (after trying earlier ideas posted) if you pulled out one card at a time (memory down to 8GB) you could test for crashes for a time.
Sometimes cards get unseated. And if you do test the cards ensure that you earth yourself to avoid static.[/COLOR]

---

### Post by coraxwolf on 2022-02-06
Can't tell if my cats are trying to help or prevent me from troubleshooting.  They've managed to reboot the pc the last two days so my uptime hasn't been more than 30 hours.

I've been monitoring the HDD temp with hddtemp and from the smartmon tools.  Smartmon is reporting the Airflow_Temp to be 75 it moves between 73 and 76 regularly.  Not sure when this started as I don't recall seeing those errors in the log before.  My syslogs only go back to Feb 1st and they appear in the logs up to that point.  This may of been reported the whole time.  the HDD temp never goes above 28.  Both smartmon and hddtemp are reporting the hdd temp to be the same.

My questions are 1) is the airflow temp in the 75s an issue if the HDD never gets overheated? and 2) can the airflow temp reading be trusted it?  Nothing else in the box is getting near 70 degrees.  All the other sensors (assuming one is the CPU and the CPU Die) stay below 50 degrees.  The two front fans are turning (these would be the ones moving air around the HDD) and the CPU and GPU fans move (the CPU i can see moving while the machine is running the GPU i can't see) and the back fan turns.  I did open up the box and aired it out with a can of compressed air.  Since then over the last two days the cpu temps have dropped a couple of degrees.  PCI-EX8 reports between 28 and 30.  k10temp-pci-00c3 reports in the 30's to the mid 40s (40's is only when I am running a game.)  Temp 2 and System 2 stay in the 30's as well.  I am not sure where those senors are coming from.

For the memory when I ordered the machine it was with 2 8GB of memory.  I've never touched anything on it until the HDD Replacement.  I did look to see if anything was loose and everything appeared well seated and connected.  I'll do another memory test tonight (since was was through with the compressed air i could of messed something up).  With a memtest86 coming back with a clean report is there any reason to suspect this to be a memory issue?

---

### Post by dragonfly41 on 2022-02-07
> [COLOR=#000000]is there any reason to suspect this to be a memory issue?[/COLOR][COLOR=#000000]

[/COLOR]I am suggesting just one line of thought .. mixing and matching different memory cards can create issues.

[https://www.crucial.com/blog/memory/mix-and-match-dram](https://www.crucial.com/blog/memory/mix-and-match-dram)

However if you purchased with two 8GB that rules out that possibility. 
But you could try running with only one 8GB at a time. Then swap cards.
It might be a wild goose chase though.

[P.S.] Further wild goose chase ideas ..

Looking for clues in
   post #1
"failed hard drive"
"new hard drive"
"shows off line to wifi router"

Looking at points of change in status, you might check the cable connections to new hard drive.

Can you run for long periods running only LiveUSB in Try Ubuntu mode (after disconnecting your "new hard drive")? 
 Why did the first drive fail, I ponder?

---

### Post by coraxwolf on 2022-02-07
The first drive failed due to age.  That was all that the smart tool  scan reported drive was way past it's end of life.  This machine is  around 7 years old now.

I didn't disconnect the drive when I  tried just using the live usb, but I didn't use the drive.  I still  encountered the same type of crash.

I don't know how the comcast  router determines if a device is online or offline, but I assume when i  crash the card/machine stops responding in some way to the router.

The system can go days between crashes.

---

### Post by coraxwolf on 2022-02-09
Looks like the last crash was really serious.  checking the kernel logs was giving messages about the canary  starving and CPU's being stalled and a few references about PCI cards not responding.  Looking up the errors returned seems to point to updating the bios.  Looked at my bios and it's date was 2015 so updated this morning.  I am not on the current bios version and then ubuntu had a few new updates to install after that.  I also updated the linux kernel to 5.13.0-28.  Been going for 4 hours so far.  The temp sensors are reading differently now.  My CPU was reading temps in the high 20's and low 30's now it's reporting 14-16 degrees and shows a critical temp setting of 20.8 degrees.  The hard drive is still reporting the same (but there wasn't any smartmon tools updates so that makes sense).

---

### Post by dragonfly41 on 2022-02-09
The fact you established that crash occurs on LiveUSB session did suggest to me it must be something like bios or motherboard or whatever. Not the hard drive and not the OS.

---

### Post by coraxwolf on 2022-02-09
that was my fear too.  and Gigabyte doesn't say their boards wont' work but linux but says that linux isn't a supporting OS for them.  That had be worried.

Hope this fixes things.  Can't afford a new pc right now and refusing to pay for a new windows licenses just cause i got a new hard drive.

---

### Post by dragonfly41 on 2022-02-09
I would browse through other forums discussing that motherboard and compatability

[https://forum.level1techs.com/t/crippling-linux-troubles-gigabyte-ab350-gaming-3/123467/4](https://forum.level1techs.com/t/crippling-linux-troubles-gigabyte-ab350-gaming-3/123467/4)

[https://askubuntu.com/questions/1389997/need-help-ubuntu-crashes-regularly](https://askubuntu.com/questions/1389997/need-help-ubuntu-crashes-regularly)

[https://ubuntu-bugs.narkive.com/bclRwDxF/bug-1671360-new-system-doesn-t-boot-properly-on-amd-ryzen-gigabyte-ga-ab350-gaming-3](https://ubuntu-bugs.narkive.com/bclRwDxF/bug-1671360-new-system-doesn-t-boot-properly-on-amd-ryzen-gigabyte-ga-ab350-gaming-3)

---

