---
title: "Cannot access pictures on camera unless logged in as root"
date: 2007-03-27
forum: General Help
---

### Post by Duffy on 2007-03-27
I've never had a problem with Digikam before. Always worked great, easy to set-up, etc. So now I have my new Kubuntu system. Installed Digikam and connected my Canon A70. Digikam detects the camera correctly and sets it up. Infocenter sees the camera correctly connected to the USB port. But when I try to download the photos, I get a "failed to connect the camera" error or "failed to list files in camera" error. I also get a connection error when I try to see the pictures in the camera with Konqueror. So I don't think it is Digikam issue, but what could be keeping the camera from communicating, especially when Digikam can see and identify the camera and Infocenter sees it correctly? I am puzzled.

So was googling the Internet and found that someone else had the problem and could access the camera when logged is as root. Sure enough, it worked for me that way. But the question is how can I access the camera logged in as just a normal user? Funny thing is on other Kubuntu systems this worked without modification. Why this system?

Anyone know how to change the permissions of the camera? Only way I know how to fix it, but cannot find it mounted anywhere in the system.

---

### Post by kidders on 2007-03-27
Hi there,

> **Duffy said:**
> So was googling the Internet and found that someone else had the problem and could access the camera when logged is as root. Sure enough, it worked for me that way.Oddly enough, it would be better if you didn't know that! You shouldn't really be logging into your graphical environment as the superuser.

> **Duffy said:**
> But the question is how can I access the camera logged in as just a normal user?What permissions does the camera have in /dev?

Depending on what they are, either fixing the account you want to log in as, or loosening the default access restrictions in udev could be your next move.

---

### Post by Duffy on 2007-03-27
First, when the camera is on and Kubuntu sees the camera, I cannot find where the camera is mounted in the system so I have been unable to determine the permission settings. And I have looked everywhere.

---

### Post by kidders on 2007-03-27
Hmm... no hints in your dmesg?

If your camera is being mounted, typing **mount** should be all you need to do to find out where it is. If your Kubuntu is being mysterious about what it's doing, running a quick comparison of the contents & permissions of /dev before and after plugging your camera in would certainly show you what's what!

---

### Post by Duffy on 2007-03-27
A fellow in the Yahoo Groups Ubuntu board pointed me here. Performed the changes, and now it works correctly. Appears to be a bug.

For others with this problem, go here:

[http://kubuntuforums.net/forums/index.php?topic=3080756.0](http://kubuntuforums.net/forums/index.php?topic=3080756.0)

---

