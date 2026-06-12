---
title: "One path for Windows and Linux?"
date: 2007-08-28
forum: General Help
---

### Post by inselaffe on 2007-08-28
I dual-boot (Windows XP/Ubuntu 7.04) a couple of systems, and where possible use common settings for any applications I use on both OSes. For instance, I use the same profile folder for Firefox on both Linux and Windows. While Firefox works a treat like this, there are applications that don't, primarily because the path format is different.

Other applications which run both Windows and Linux but store settings on a server have similar problems: for instance Lotus Notes stores the path to the file used for the email signature in the server mail file, in the path format used by the OS in which it is set.

What is needed is a common path format for both OSes.

I can make a soft link to Windows partitions in Linux so I can reference [Windows C:\] as /C:/ which makes something like file:///C:/Directory work in either OS, but most applications aren't happy with using this type of URI.

Is there a way of making either Linux understand Windows-style paths or Windows understand Linux-style paths, at a low enough level that any application can use?

---

### Post by kidders on 2007-08-29
Hi there,

Trying to share the same application settings between more than one copy of the same OS is a bad idea ... let alone sharing between different OSs. Even if you could get it to work, I would be disappointed if you didn't encounter odd behaviour, because it would mean that your application implementations were essentially identical across operating systems. In practice, you'd presumably also encounter problems associated with software updates.

I strongly suggest not trying to manipulate your computer into sharing application settings.

---

