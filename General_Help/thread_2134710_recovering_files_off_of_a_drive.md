---
title: "recovering files off of a drive"
date: 2013-04-12
forum: General Help
---

### Post by bbk24 on 2013-04-12
so last night i was downloading some movies and some cad files on my ubuntu machine and when i woke up this morning it had a message saying that the hard drive was full. when i tried to log back in it restarted and put the computer into low graphics mode. i was wondering if their is a way to get the files that i downloaded last night and some others on to a portable hard drive. i booted from a live cd via usb but i cant mount the drive. i am fairly new to ubuntu and am not the greatest with terminal. any help would be appriciated. if you need more info just ask.

---

### Post by bbk24 on 2013-04-12
anyone?

---

### Post by papibe on 2013-04-12
Hi bbk24. Welcome to the forums ):P

Yes. You can use the installation media as a live CD/USB to access your disk.

Once you boot into the media, choose 'Try Ubuntu' instead of 'Install'. You'll get into a live desktop. Open the file manager (Nautilus) and go to 'Computer'. There you sould be able to see your laptop hardrive. If you double click on it you'll mount it, and have access to your files.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by bbk24 on 2013-04-12
when i try to mount it it says:

Unable to mount 156 GB Volume
Adding read ACL for uid 999 to `/media/ubuntu' failed: Operation not supported

---

### Post by papibe on 2013-04-12
I believe you are using 12.10 as a live media?

There's a little bug on that version. You can solve it by running this commands before trying to mount your partitions/disks:
```
sudo mkdir /media/ubuntu

sudo chown ubunut.ubuntu
```
Let us know how it goes.
Regards.

---

### Post by bbk24 on 2013-04-12
thank you so much. i searched all day yesturday trying to find a solution and to find out it was something as simple as that. i just have one more question. when i go into the drive and go to media it says:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "myname"

and when i go under properties and permissions it says:

you are not the owner, so you cannot change these permissions.

how can i change the permissions so i can move some of these files to free up space.

---

### Post by papibe on 2013-04-12
Once you have the drive mounted, try this:
```
gksudo nautilus /media/ubuntu
```
That should open the file manager on the directory where the disk is mounted using root privileges (to avoid permission problems). 

Let us know how it goes.
Regards.

---

### Post by bbk24 on 2013-04-12
that worked but when i open the "myname" file its blank and i know their should be files there

---

