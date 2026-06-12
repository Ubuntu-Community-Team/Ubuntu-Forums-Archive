---
title: "Dapper Power Mgmt Has No UPS Options"
date: 2006-12-23
forum: General Help
---

### Post by RamonBianco on 2006-12-23
Hello, all.

I just put my dapper PC on a UPS, which is recognized okay:[INDENT][FONT="Courier New"]
[COLOR="Blue"]lshal | grep -i ups
 info.product = 'Back-UPS Pro 500/1000/1500'  (string)
 usb_device.product = 'Back-UPS Pro 500/1000/1500'  (string)
 battery.type = 'ups'  (string)
 info.addons = {'hald-addon-hid-ups'} (string list)
 hiddev.product = 'APC Back-UPS ES 500 FW:801.e5.D USB FW:e5'  (string)[/COLOR][/FONT][/INDENT]

The Power Management notification icon tells me that the battery is 100% charged, but that it's running on AC power.

But there is no UPS tab in the Preferences to set when to hibernate if the AC power goes out.

Is there a way to do this?

Thanks.

---

### Post by RamonBianco on 2006-12-23
Can somebody please make this thread sticky?  :lol:

But seriously (:(), is this not the right forum for my question?  :confused:

---

### Post by RamonBianco on 2007-01-01
Happy [COLOR="PaleGreen"]Gregorian[/COLOR] New Year.

---

### Post by RamonBianco on 2007-01-06
[COLOR="White"]Go cowboys![/COLOR]

---

### Post by mariuss on 2007-01-07
Looking at getting an ACP UPS myself. I was looking at the acpupsd and acpd packages. Give them a try.

The acpupsd home page: [http://www.apcupsd.org/](http://www.apcupsd.org/)

---

### Post by RamonBianco on 2007-01-08
Thanks for the response, mariuss, and let me know if/*how* you get it working.

I believe I tried acpupsd before I plugged in the UPS, and it didn't make a difference as far as the power mgmt setup.  Maybe acpupsd has a different interface, but it sure would be nice to have it right in The Power, like some other OSes I know.

---

### Post by mariuss on 2007-01-16
I just installed a new APC UPS under Edgy, you can see the details on my blog:
[http://marius.scurtescu.com/?p=156](http://marius.scurtescu.com/?p=156)

You can also search these forums, I have seen other threads with instructions.

Marius

---

### Post by RamonBianco on 2007-01-24
Thanks again, Marius.

I got acpupsd installed okay, but the UPS tab didn't show up in the Power Mgmt prefs, at least, not when I have the UPS plugged in to the wall outlet.  I tried unplugging it, but apparently, I need a new battery; it started losing power too fast, and went into shutdown mode before I could check the Power Mgmt prefs again.

---

### Post by mozetti on 2007-01-24
You set the preferences in apcupsd, not in the power management gui. I'm no longer subscribed to the thread, but in the HowTo section has a good tutorial I used and the apcupsd website/documentation has all the info you need. If it's a USB connection to the computer (like mine), then it's really easy.

---

### Post by RobNY on 2007-01-24
I installed apcupsd and configured it in Dapper.  It seems to work fine.  But I, too, do not get the UPS tab in gnome-power-manager.  Is this the correct behavior?

---

