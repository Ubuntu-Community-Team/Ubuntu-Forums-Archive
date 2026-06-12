---
title: "Hi there, I have a problem unmounting my mp3 player"
date: 2008-04-08
forum: General Help
---

### Post by stefman88 on 2008-04-08
hey y'all

I'm a Noobie to the Ubuntu stuff, my brother in law installed it into our computer. He's the administer, but he's gone away on vacation---boooooooo

so I was wondering if any of you guys could help me out:

I currently have a Sandisk e200 plugged into my computer, and I want to un mount it, unfortunantly when I attempt to, this is the message I get:

Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy.
details say that it cannot unmount volumes mounted by others uid 1002

does anyone know what this means?

and can anybody help me?

thanks in advance

---

### Post by ibutho on 2008-04-08
Hi,

Do you know who has the uid 1002? You need to login as that user (in the terminal or gui) and unmount the device. You can check your own uid by running the "id" command and you can check that of others by looking at /etc/passwd. Awk can make the process easier e.g. the script below should show each user and their UID
```
awk -F : '{ print $1, $3}' /etc/passwd
```

---

### Post by stefman88 on 2008-04-08
sorry I'm not quite sure of what you mean.

But I kinda think I understand

each of us has a profile on this computer. do I find the id code on my profile, or do I get the administrator's?

once I get the code, what do I do?

---

### Post by ibutho on 2008-04-08
Hi.

Everyone has a user id (uid) which is listed in /etc/profile. Whoever mounted the mp4 player has a uid of 1002, so you need to login as that user in order to unmount the device or try to unmount it whilst logged in as the administrator. I had asked that you post your uid, just to see if it was yourself who had mounted the device (running the command "id" would show you your uid) or whether it was a different user.

---

### Post by stefman88 on 2008-04-08
hmm I have logged in as both profiles that I might have mounted it in but they don't work...I don't think I can log in as the administrator 

if I just un plug it manually what will happen to it?
when I have, it refrshes the database on the mp3 player
that's the message I get from it

---

### Post by stefman88 on 2008-04-08
OH!
I think I fixed it now

I changed the USB mode and and now the computer reads it differently, so all I have to do I guess is use a music browsing program to put music on it, I figure this because it only says writing when in the program and out of it, it says connected.

thank you for your help anyways

take er' easy

---

