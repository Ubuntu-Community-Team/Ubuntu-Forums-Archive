---
title: "RCA Android 10 tablet won't USB connect with Ubuntu 18.04"
date: 2021-01-30
forum: General Help
---

### Post by ra7411 on 2021-01-30
Anybody know how make this connection? I used the technique to become "developer" and it still won't switch how its controlled in settings. I've installed gmtp in Ub and it says no device.

I'm at a loss on this.

Thank

---

### Post by CelticWarrior on 2021-01-30
I'm at a loos too regarding what you want to do, what does developer mode or gmtp have to do with it.

---

### Post by jeremy31 on 2021-01-30
> **CelticWarrior said:**
> I'm at a loos too regarding what you want to do, what does developer mode or gmtp have to do with it.
Developer mode can be used to change the default USB connection from charge only to file transfer

---

### Post by ra7411 on 2021-01-30
> **jeremy31 said:**
> Developer mode can be used to change the default USB connection from charge only to file transfer

Right. And in answer to the other post, I want to be able copy files from Ubuntu into the tablet.

---

### Post by CelticWarrior on 2021-01-30
> **ra7411 said:**
> Right. And in answer to the other post, I want to be able copy files from Ubuntu into the tablet.

That was the clarification needed and absent in the first post. And basic troubleshooting is also missing (you may skip to the last paragraph).

For that purpose it isn't necessary to enable developer mode. Any modern Android device once connected should present a menu with the available options for the USB connection that vary between manufacturers and OSes (vanilla Android or modified/skinned versions like the famous Xiaomi's MIUI or Meizu's Flyme) but typically have at least "charging only", "file transfer" (MPT) and "photo transfer" (PTP). If the aforementioned menu isn't served then the device isn't recognizing the connection as a connection to a computer or similar but merely as a changer. Nothing in the developer mode will make it recognize it differently. Reasons for that can be many but typically either that feature has been removed on purpose, the Android OS has issues or anopther cable is needed (some cheap cables not always allow data transfer, some Android deices are picky).

Have you tested it and confirmed it's working as intended with the same cable in another computer? If so, you need to troubleshoot your Ubuntu computer; if not, start by testing with another cable.

---

### Post by jeremy31 on 2021-01-30
I wonder if the Android device supports obex as I had that issue with an Android phone years ago

---

### Post by CelticWarrior on 2021-01-30
> **ra7411 said:**
> Most people understand what "USB connect" means.
Yes, most people know that a "USB connection" can be 3 , 4 or half-a-dozen different things. Anyone that used a smartphone or tablet knows that there are at least the aforementioned 3 options available and more advanced users also know that an USB connection to an Android device can also be used for debugging ([ADB]("https://en.wikipedia.org/wiki/Android_software_development#Android_Debug_Bridge_(ADB)")) and that in itself can mean or encompass a multitude of usages.

Surely the file transfer feature being the issue could have been inferred from the poorly written, confusing and lacking any basic troubleshooting first post, but a clarification was in order. It could have been a lot simpler if you just posted as:

> Can't enable file/photos transfer (MTP/PTP) when connected to the Ubuntu XX.XX computer via USB.
It works in other computer.

That being the case no clarification was needed and we could immediately make suggestions regarding troubleshooting your Ubuntu computer.
That NOT being the case - it doesn't work in other computers - then you have a problem with the Android device and/or the cable so, not really a problem for this forum, don't you think?

---

### Post by ra7411 on 2021-01-30
> **jeremy31 said:**
> I wonder if the Android device supports obex as I had that issue with an Android phone years ago

Not familiar with obex. I have an RCA android 4 tablet that I've used for several years with no Ub 16.04 or 18.04 usb connection problems.

It does "see" my usb connect as it shows the name i gave to the desktop, but nothing shows up in either device's file managers.

I tried a Bluetooth connect, it recognizes it, but again, no file manager access in either device.

Aggravating.

---

### Post by ra7411 on 2021-01-30
> **CelticWarrior said:**
> Yes, most people know that a "USB connection" can be 3 , 4 or half-a-dozen different things. Anyone that used a smartphone or tablet knows that there are at least the aforementioned 3 options available and more advanced users also know that an USB connection to an Android device can also be used for debugging ([ADB]("https://en.wikipedia.org/wiki/Android_software_development#Android_Debug_Bridge_(ADB)")) and that in itself can mean or encompass a multitude of usages.

Surely the file transfer feature being the issue could have been inferred from the poorly written, confusing and lacking any basic troubleshooting first post, but a clarification was in order. It could have been a lot simpler if you just posted as:

That being the case no clarification was needed and we could immediately make suggestions regarding troubleshooting your Ubuntu computer.
That NOT being the case - it doesn't work in other computers - then you have a problem with the Android device and/or the cable so, not really a problem for this forum, don't you think?

>Surely the file transfer feature being the issue could have been inferred from the poorly written,<

Then why didn't you? 
People post in here to get help, not for pedantic nonsense.
Do me a favor, and leave the thread.

---

### Post by Autodave on 2021-01-30
I have an RCA tablet here that I have never been able to get into via USB.

---

### Post by ra7411 on 2021-01-30
> **Autodave said:**
> I have an RCA tablet here that I have never been able to get into via USB.

Yeh, I do have a Windows install I just hate to resort to giving up on Ub to see if it will work.

---

