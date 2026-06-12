---
title: "Bluetooth disabled"
date: 2016-12-14
forum: General Help
---

### Post by dagon92 on 2016-12-14
Hello. I'm having some issues getting bluetooth working on Ubuntu 16.04. I go to the bluetooth program and turn it on but it says it's disabled and visibility is faded and unselectable. The computer does have bluetooth, so that isn't the issue. I'm assuming I'm possibly missing some drivers or something similiar.

---

### Post by ndc333 on 2016-12-14
if its the first use, youll probably find its blocked at the kernel level. If i remember correctly you need to use rfkill -> do a google search for instructions.

---

### Post by dagon92 on 2016-12-14
Is it the softblock thing because according to rfkill it is neither soft or hard blocked.

---

### Post by #&amp;thj^% on 2016-12-14
With so little information to go off here...just some suggestions to try:
1.Check in  /etc/bluetooth/main.conf 
I have noticed that this line is un-commented:

[B]Change #AutoEnable=false to AutoEnable=true 
[/B]
```
# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
AutoEnable=true

```

Now you can Restart the bluetooth service 
```
sudo systemctl restart bluetooth.service
```

Or even reboot your system.
Hope this helps.

---

### Post by dagon92 on 2016-12-14
I'm sorry. I should have clarified that while I am not totally useless with linux I am still a newbie I don't know what to do with your first suggestion. Just go to the directory and as an example treat it as the about:config in firefox for example? I really do apologize. I'm not this bad with Windows.

---

### Post by #&amp;thj^% on 2016-12-15
No worries... Sorry if i was unclear on this:
First open the file with:
```
sudo -H gedit  /etc/bluetooth/main.conf
``` 
This "gedit" is text editor for a Ubuntu Desktop or even Gnome desktop...just to be clear.
If you are using a different Desktop then that will have a different editor IE: KDE will use "Kate" and XFCE will use "mousepad" Mate Desktop will use "pluma" etc etc. 
Now after that is opened look to the bottom where you see:
```
# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
#AutoEnable=false
```
the bottom that reads **"#AutoEnable=false"** will need to edited to look like **"AutoEnable=true"**
So just the bottom line should now look like this:
```
# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
AutoEnable=true
```
Now save and colse the text editor and resart the service with:
```
sudo systemctl restart bluetooth.service
```
Some have had to even do a reboot.
But hopefully now you should have the Bluetooth Service running or enabled.

---

### Post by dagon92 on 2016-12-15
Well I did as you directed as far as I can tell. The only noticeable change was that the icon showed up in the task bar. I rebooted and the icon doesn't show up again. Any more suggestions?

---

### Post by #&amp;thj^% on 2016-12-15
When you say "noticeable change was that the icon showed up in the task bar" was it then enabled?
```
sudo systemctl enable bluetooth.service
sudo systemctl start bluetooth.service
```
But try this again first.
```
sudo systemctl restart bluetooth.service
```

But some more questions I have are:
Do you have a hard switch on your computer for Buletooth?
Do you have it set to start on bootup?

---

### Post by dagon92 on 2016-12-15
If by enabled you mean I turned it on in the program yes, but other then the icon showing up there was no noticeable change. As far as I can tell there is no hard switch on this laptop. I will do your new suggestion and report back momentarily. I don't know if it's set to start at boot or not.

edit: Alright. The icon is showing up again but the only option I can select is turn bluetooth off, local services, plugins, help and exit.

---

### Post by #&amp;thj^% on 2016-12-15
So it is "on" right now.... right?

---

### Post by dagon92 on 2016-12-15
Yes it is on I'm pretty sure. The icons first option is to turn bluetooth off.

---

### Post by #&amp;thj^% on 2016-12-15
Ok!
But what are we trying to do here?
Your Request for help is "Bluetooth disabled"
Am I to assume you are trying to pair something to it now?
See what I mean with "so little information to go on here"
Help me or (Us) out here... the more information we have from you helps Us to Help You.

---

### Post by dagon92 on 2016-12-15
The issue is that while the bluetooth is on it is disabled. There is no way to actually setup a new device. I tried taking a screen shot of the icon in the task bar but the drop down menu kept disappearing, So I guess this screen shot of the actual bluetooth program is the best I can do. I really don't know how to clarify anymore. The issue baffles me to be honest. Only thing I can think of is that it might be a driver issue of some sort but I dunno.

---

### Post by #&amp;thj^% on 2016-12-15
Hmmm?
Not sure I can help here..But do this for me if you would:
```
sudo apt-get --reinstall install bluez
```
And maybe give us the output of this from the terminal:
With the device you want to pair plugged in.
```
lspci -knn | grep Net -A2; lsusb
```

---

### Post by dagon92 on 2016-12-15
Alright. reinstalled and then ran command with the bluetooth device plugged into the usb port. I assume you just wanted this output and not the whole thing. If you needed the other command as well just let me know.


admin@N3R0:~$ lspci -knn | grep Net -A2; lsusb
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave AW-NE186H [1a3b:1186]
    Kernel driver in use: ath9k
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57de Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by #&amp;thj^% on 2016-12-15
Can you give us the make and model of the Bluetooth Device we are working with here.
even the type of device it is...IE is it a Headset and (Headphones), is it a Speaker etc etc.

---

### Post by dagon92 on 2016-12-15
They are a pair of earbuds. I'm not sure on the exact model number since I got them secondhand from a friend. On my Linux Mint netbook and my android phone they show up as Vivitar met earphones, not that that is very helpful. Sorry. They work fine on every other device I have tried.

---

### Post by #&amp;thj^% on 2016-12-15
I thought that might be the case...I have no experience with those.
But in theory if they work with Mint they should work here as well...as mint is built from ubuntu.
I'm sure someone else will now be able to help though.
Good Luck.;)

---

### Post by dagon92 on 2016-12-15
Thank you for your time and effort

---

### Post by jeremy31 on 2016-12-15
I did not see anything I recognize as a bluetooth device in the lsusb results.  What is the manufacturer and model of the bluetooth dongle?  I suspect a firmware issue

---

### Post by dagon92 on 2016-12-16
Vivitar is the manufacturer. As for the model, no clue. I got the headphones from a friend since he upgraded and never used the set. He doesn't remember the model name. It just shows up as Vivitar met earphones on my other devices. I have tried searching for them on Amazon and the like but have had no luck finding the same set which makes me think they are a model that is no longer made.

---

### Post by jeremy31 on 2016-12-16
So did this headset have its own dongle?  What did you have plugged into the USB port when you posted lsusb results for 1fallen?

---

