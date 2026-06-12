---
title: "'couldn't find matching udev device' when connecting HTC One S?"
date: 2014-11-14
forum: General Help
---

### Post by lucy3 on 2014-11-14
When I connect my HTC One S phone. I get this error message ```
couldn't find matching udev device
```

I installed fastboot and adb with seemingly no issues. Please tell me how to fix. Only just switched to linux though so be gentle.  I have 14.04.1 Long term support version installed. Thanks.

---

### Post by lucy3 on 2014-11-16
Hi, I have found out that I have to create udev rules for android. Been following this post, [HTML]http://blog.mpshouse.com/?p=609[/HTML] but when I try to edit the fuse line I get the following output.

```
lucy@lucy-N150P:~$ sudo gedit /etc/udev/rules.d/51-android.rules
[sudo] password for lucy: 
lucy@lucy-N150P:~$ sudo gedit /etc/fuse.conf

(gedit:3384): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:3384): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
lucy@lucy-N150P:~$ sudo gedit /etc/group

(gedit:3411): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:3411): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
lucy@lucy-N150P:~$ udo mkdir /mnt/a501
Error:  0: couldn't open source file </mnt/a501.ui>
/mnt/a501.ui: No such file or directory
lucy@lucy-N150P:~$ 

```

Advice appreciated, thanks

---

### Post by nerdtron on 2014-11-17
Why use gedit?? Is gedit even installed in Lubuntu? You can clearly use nano for this:
```
sudo nano /etc/udev/rules.d/51-android.rules
```
You'll be presented with a blank screen. Then just copy and paste what it need in there. (use right click>paste when pasting)
Ctrl+O to save.
Ctrl+X to exit.

Same thing with the fuse.conf
```
sudo nano /etc/fuse.conf
```

What instruction from your link is not clear to you? Maybe we can help clarify it. It seems straightforward to me.

---

### Post by lucy3 on 2014-11-17
Thanks for helping nerdtron, 

Didn't know about nano before the gedit post of earlier and I'd downloaded gedit already. 

> The file fuse.conf needs to be modified, uncomment the line user_allow_other. The file can be edited with the following command:  This means just deleting the # at the start of the line right? That's what I did and worked through the guide until I reached mounting.

> **Mounting**
The mount point can be added to fstab but I have created a small script  to mount the drive and display the directory. If you are not using  nautilus you need to change that line and if the mount point is not  going to be /mnt/a501, that needs to be changed as well.

 #!/bin/bash
gksu -S --message "Enter your password to mount your Android device." "mount mtpfs /mnt/a501 -t fuse -o user,noauto,allow_other"
nautilus /mnt/a501/

Does this mean I can just use this in terminal or do I need to create a script myself, how? How do I know if I'm using nautilus or not?

---

### Post by nerdtron on 2014-11-17
> This means just deleting the # at the start of the line right? That's  what I did and worked through the guide until I reached mounting.
Yes. Correct.
> 
Does this mean I can just use this in terminal or do I need to create a  script myself, how? 
You don't have to create a script. Just run the command in the terminal to mount the device, I don't think you need the message either. So:
```
sudo mount mtpfs /mnt/a501 -t fuse -o user,noauto,allow_other
```

> How do I know if I'm using nautilus or not?
Lubuntu doesn't use nautilus file manager.
After the mounting command, assuming it is successful, you just Open your file manager and go to /mnt/a501 to see your android device.

---

### Post by lucy3 on 2014-11-18
Well my phone is picked up but it can't connect.

```
lucy@lucy-N150P:~$ sudo chown lucy:lucy /mnt/a501
[sudo] password for lucy: 
lucy@lucy-N150P:~$ sudo mount mtpfs /mnt/a501 -t fuse -o user,noauto,allow_otherUnable to open ~/.mtpz-data for reading, MTPZ disabled.Listing raw device(s)
Device 0 (VID=0bb4 and PID=0df9) is a HTC HTC One S (ID2).
   Found 1 device(s):
   HTC: HTC One S (ID2) (0bb4:0df9) @ bus 1, dev 5
Attempting to connect device
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
```

Any ideas? Appreciate the time your spending on this.

Edit: plugging my cable into another usb port device shows up as two phone shaped 'mpt' rather than two 'android' I can see my files and fastboot recognises my phone with no errors. However I still get the > couldn't find matching udev device When first plugging in and phone is not listed in devices.

---

