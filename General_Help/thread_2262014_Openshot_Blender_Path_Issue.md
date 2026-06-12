---
title: "Openshot Blender Path Issue"
date: 2015-01-22
forum: General Help
---

### Post by CaptainMikeRak on 2015-01-22
I'm trying to make a "New Animated Title" with Openshot, but I keep getting an error telling me that there is a "Blender Error" and it shows me the path it's trying to use (I am using Blender version 2.70a if that has anything to do with it).

I have tried using the following paths:
[LIST]
[*]blender (this is the default one)
[*]usr/share/applications
[*]/usr/share/applications
[/LIST]

Nothing appears to be working. I am wondering if the version might be the problem but not sure. If anyone has anything that might be of help I would greatly appreciate it. I could do with the help soon since I have a rather complex project to get done (well... compared to the previous ones it's complex).

---

### Post by CaptainMikeRak on 2015-01-22
This is strange, I set it to just "blender" for the path, and it gives me this error:
```
No frame was found in the output from Blender.
```

Anyone know why this would happen?

---

### Post by CaptainMikeRak on 2015-01-22
Okay, now it appears intermittant and on the more complex ones. Is it possible this is due to lower spec hardware?

Anyways, if it helps (or if anyone replies), here is the full error dialogue:
```

Blender, the free open source 3D content creation suite is required for this action (http://www.blender.org).

Please check the preferences in OpenShot and be sure the Blender executable is correct.  This setting should be the path of the 'blender' executable on your computer.  Also, please be sure that it is pointing to Blender version 2.62 or greater.


Blender Path:
blender


Error Output:
No frame was found in the output from Blender

```

I really need to get this working, so any help is much appreciated.

---

### Post by CaptainMikeRak on 2015-01-22
Okay, looks like I solved *part* of the problem. I changed the directory to "/usr/bin/blender" and now it is detecting it.
I found this after some Googling: [https://answers.launchpad.net/openshot/+question/249837](https://answers.launchpad.net/openshot/+question/249837)

Blender seems to crash when I use some of the titles. This issue appears to either be an issue with my video driver or my outdated hardware. Anyways, it seems I solved my issue (except I ran into another issue). It seems to work sometimes now, but I still run into this error on some items. I'm leaving this open if in case anyone has any ideas that might explain it other than this.

---

