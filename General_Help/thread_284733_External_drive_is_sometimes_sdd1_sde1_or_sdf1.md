---
title: "External drive is sometimes sdd1 sde1 or sdf1"
date: 2006-10-26
forum: General Help
---

### Post by Kza on 2006-10-26
Hi, My external USB hard drive and USB sticks have inconsistent device names and mount points depending on the order in which they are plugged in, switched on, or mounted.

This wouldnt be such a huge problem, but my mp3 playing software (amarok) stores a database of the path names, and expects /media/usbdrive, but if I have a memory stick or flash card mounted then sometimes my external drive gets mounted as /media/usbdrive-1 and amarok has to rescan it.

Any ideas on how to specify either consistent /dev/ names, or mount points for certain devices?

Thanks

Kurt

---

### Post by ToonArmy on 2006-10-26
I just setup something very similar for my USB *pen* drive on Edgy so YMMV but this is how I did it.

1) Open the gnome device manager, it's hidden in System -> Administration -> Device Manager

2) Plug in your USB HD and find it in the device manager. Follow the tree  for the device down to the Volume object, which should be the last item. Now traverse up one node and click the advanced tab in the right hand pane. Hopefully in the list there should be a property storing something unique to the device, I found the serial number of my pen drive in *storage.serial* but again YMMV. Once you found something unique or unique enough that another device you are likely to connect will not have the same property. Make a note of the property **key** and **value**, you can copy and paste from the list, just click on the text to select it. :)

3) Open a terminal window

4) Perform these commands:

```
cd /usr/share/hal/fdi/policy/
sudo mkdir 95userpolicy
gksudo gedit 95userpolicy/10-usbhd.fdi
```

Note: You might want to use vi or gedit instead of nano.

5) Now we need to write the XML for the HAL

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
	<device>
		<match key="block.is_volume" bool="true">
			<match key="@info.parent:**your.key**" string="**your.value**">
				<merge key="volume.policy.desired_mount_point" type="string">**mount_point**</merge>
			</match>
		</match>
	</device>
</deviceinfo>
```

Replace the bold sections with the values obtained earlier and the mount point you want to use for the device, note this is prefixed automatically by */media*. So just put something like *usbhd*.

6) Unmount your device, otherwise gnome might get confused, and then unplug it.

6) Restart HALd, took me ages to work this out!

```
sudo /etc/etc/dbus-1/event.d/20hal restart
```

7) Plug the HDD back in.

I hope this helps and I didn't miss anything.

---

