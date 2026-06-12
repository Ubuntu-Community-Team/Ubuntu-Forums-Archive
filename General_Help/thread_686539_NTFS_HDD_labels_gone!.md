---
title: "NTFS HDD labels gone!"
date: 2008-02-03
forum: General Help
---

### Post by shafin on 2008-02-03
I dont know what I had done,but nautilus has stopped showing the labels for my NTFS HDDs. They are now shown as plain sda1 sda2 etc. Also the Eject button for CD/DVD ROMs is missing.

Can you help me?

---

### Post by shafin on 2008-02-10
:(,almost a week gone

---

### Post by chrisccoulson on 2008-02-10
First of all, are these NTFS HDD's auto-mounted, or are they specified in your /etc/fstab? If they are automounted, they will appear in /media/<*label*>. You can set the label of the volume by doing:
```
sudo ntfslabel /dev/**** *label*
```
...where /dev/**** is the device node of the volume and *label* is your desired label.

If the device is specified in your fstab, then Nautilus will probably not display the label.

> Also the Eject button for CD/DVD ROMs is missing.

Could you elaborate please? If you want people to help, I suggest that you be more specific and also separate different problems in to different threads.

---

### Post by shafin on 2008-02-11
> **chrisccoulson said:**
> First of all, are these NTFS HDD's auto-mounted, or are they specified in your /etc/fstab? If they are automounted, they will appear in /media/<*label*>. You can set the label of the volume by doing:
```
sudo ntfslabel /dev/**** *label*
```
...where /dev/**** is the device node of the volume and *label* is your desired label.

If the device is specified in your fstab, then Nautilus will probably not display the label.



Could you elaborate please? If you want people to help, I suggest that you be more specific and also separate different problems in to different threads.
The HDD's are specified in my /etc/fstab
ntfslabel gives the following error:
[FONT=mon][I]sudo: ntfslabel: command not found

[/I][/FONT]

on the CD rom problem, I am using a localized version of ubuntu and there s little hope of getting the support in that language, therefore I just tried to have a rough translation of the functionality. When you right click a mounted CD/DVD ROM it gives you an option to eject the CD/DVD from your drive after unmounting it. And the reason I specified the two problems in the same post is that they started at the same time and I thought they were related.There had also been [another problem]("http://ubuntuforums.org/showthread.php?t=691704") that I discussed in another thread.

What might interest you is that I'm also getting a Failed to initialize HAL report with this.I have a Core2Duo box with Intel 945G chipset ang 1GB RAM.

Hope it helps you to solve the problem.


---

### Post by Rocket2DMn on 2008-02-11
Unmount the ntfs drives, then run
```
sudo apt-get install ntfsprogs
sudo ntfslabel /dev/(yourdevice)
```
As for your cd, I don't know exactly what's up, but you don't really need an eject button, you should just be able to unmount then eject by pressing the button on the drive.
Check out System->Preferences->Removable Drives and Media and make sure "mount removable drives when hot plugged" and "mount removable media when inserted" is checked.

---

### Post by shafin on 2008-02-11
> **Rocket2DMn said:**
> Unmount the ntfs drives, then run
```
sudo apt-get install ntfsprogs
sudo ntfslabel /dev/(yourdevice)
```
As for your cd, I don't know exactly what's up, but you don't really need an eject button, you should just be able to unmount then eject by pressing the button on the drive.
Check out System->Preferences->Removable Drives and Media and make sure "mount removable drives when hot plugged" and "mount removable media when inserted" is checked.
Thanks for helping, Seems like the problem is coming from my HAL failing to initialize. When I try System->Preferences->Removable Drives it says that it needs Hald to operate and my HAL,for some searon,fails to initialize,can you please tell me how I can find out what the problem with HAL is?

---

### Post by Rocket2DMn on 2008-02-11
It sounds like you might have an incompatible piece of hardware.  Did you add anything like a new printer or other piece of hardware?

---

### Post by chrisccoulson on 2008-02-11
HAL failing to initialise would definately be problematic. Can you try:
```
sudo /etc/init.d/hal restart
```
And post the output. If it starts, then it would suggest you have a race condition when you boot your machine.

---

### Post by shafin on 2008-02-11
> **chrisccoulson said:**
> HAL failing to initialise would definately be problematic. Can you try:
```
sudo /etc/init.d/hal restart
```
And post the output. If it starts, then it would suggest you have a race condition when you boot your machine.
It starts, that means I have a race condition when I start my machine?
Now, forgive my noobness,but what is a race condition and how can I solve it and get HAL working?

And again,thanks a lot,you guys have been real helpful :)

---

### Post by Rocket2DMn on 2008-02-11
Do you have automatic login enabled, shafin?  If so, disable it (System->Administration->Login Window and hit the Security tab, then uncheck the box for Automatic Login).

---

### Post by shafin on 2008-02-11
No,automatic login is not enabled.

---

### Post by Rocket2DMn on 2008-02-11
Let's try to reinstall hal, that seems to have worked for a lot of users
Go to System->Administration->Synaptic Package Manager, put in your password.  When in synaptic hit ctrl+f and search for "hal".  When you find it on the list, right click and select Mark for Reinstallation.  Then click the apply button and let it reinstall.  Reboot to check and see if this fixed the HAL problem.

---

### Post by shafin on 2008-02-12
I've reinstalled HAL right after the problem began,but it was to no avail.

---

### Post by Rocket2DMn on 2008-02-12
OK, here is a user who had a similar problem, hopefully something along the same lines will work for (setting the correct load order during boot) - [http://ubuntuforums.org/showthread.php?p=3545464](http://ubuntuforums.org/showthread.php?p=3545464)

---

### Post by chrisccoulson on 2008-02-12
Have you followed any guides online to improve the boot up speed of your machine? I know that one guide I've seen online contains a mod to /etc/default/rcS which enables concurrency. That screws up HAL on my Gutsy machine.

And just to clarify, when I refer to a race, I mean that HAL is trying to start before someting else it depends on has started.

It might be worth trying to find out exactly what is causing it to fail. IIRC the boot messages only go to the console and not in to a log file, so you'll have to disable the quiet and splash options to boot, and watch carefully for a line that begins with something like:
```
* Starting Hardware Abstraction Layer
```
Is there a meaningful error?

To disable 'quiet' and 'splash' at boot time, you need to press [ESC] when Grub loads, then press [E], use the arrow keys to select the line beginning 'kernel', press [E] again, delete the 'quiet' and 'splash' options, press [RETURN] then press [B] to boot.

---

