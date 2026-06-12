---
title: "CD Burning is impossible"
date: 2008-03-05
forum: General Help
---

### Post by ubutufan on 2008-03-05
Cannot burn any type of cd/dvd. I really need all the help i can get

I've been using k3b mostly for burning. About ten-15 days ago burning became impossible and k3b gives me this error
Cdrecord has no permission to open the device

I have searched almost everywhere but can't sort it out.
Highlight. I called Dell because i thought it was a faulty dvd. They came and replaced it. Burned once. Never again.
It sort of drives me nuts. Nautilus is not working either
Thanks for the help

---

### Post by ubutufan on 2008-03-05
Any help people???

---

### Post by Dennis on 2008-03-05
Not sure if this helps you but someone on the Kubuntu forum solved it by:
*slowing my burner to 8x and changing the write mode to TAO, *

or you could read through this

[http://ubuntuforums.org/showthread.php?t=676848](http://ubuntuforums.org/showthread.php?t=676848)

---

### Post by nlong on 2008-03-05
I'm not familiar with the product, but here's what I found.  Google is a wonderful thing :)

&#8594; go to System &#8594; Administration &#8594; Users and Groups &#8594; "your user" &#8594; Properties &#8594; User privilegies and make you sure that "Use CD-ROM Drives" is enabled

and/or:

K3bSetup, how do i do this? I have gone into the setup and made sure there are ticks next to cdrecord cdrdao.

and/or:

create a group called "Burning", and add your self and root to the Bruning group.
Now, in k3bsetup, check mark the group burning option, then set permissions.

---

### Post by ubutufan on 2008-03-05
I have tried all that. It does not work.
Funny thing is that it plays all sorts of media. Simply does not burn
Help!!!!!!!!!!!!!!!!. My work depends on this device

---

### Post by DaV|d on 2008-03-05
Try running k3b as root, maybe /dev/dvd permissions got changed?

---

### Post by ubutufan on 2008-03-05
Running as root works.

Thank you so much for this. It helps me trendously with my work.:lolflag:


I am curious as to what has happened. Any ideas?

---

### Post by DaV|d on 2008-03-05
Glad it worked :) It's probably a permissions issue. 

You can try changing the permissions of /dev/scd0 to rw for everyone:
```
sudo chmod 0666 /dev/scd0
``` 
and run k3b as a normal user. 

**DON'T do the following procedure, if the above suggestion doesn't work**, otherwise you can make the solution permanent by:
1)**[COLOR="Red"]Making a backup of /etc/udev/rules.d/70-persistent-cd.rules[/COLOR]**
```
sudo cp /etc/udev/rules.d/70-persistent-cd.rules /etc/udev/rules.d/70-persistent-cd.rules.bak
```
2)Open /etc/udev/rules.d/70-persistent-cd.rules in an editor (as root)
```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
3)Add MODE="0666" to every line beginning with ENV{ID_CDROM} so every line should look something like this:```
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.5-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1", MODE="0660"
```
4) Save and close. After a reboot, everything should be working ok :)

---

### Post by Whiffle on 2008-03-05
Try running

k3bsetup

---

### Post by ubutufan on 2008-03-05
> **DaV|d said:**
> Glad it worked :) It's probably a permissions issue. 

You can try changing the permissions of /dev/scd0 to rw for everyone:
```
sudo chmod 0666 /dev/scd0
``` 
and run k3b as a normal user. 

**DON'T do the following procedure, if the above suggestion doesn't work**, otherwise you can make the solution permanent by:
1)**[COLOR="Red"]Making a backup of /etc/udev/rules.d/70-persistent-cd.rules[/COLOR]**
```
sudo cp /etc/udev/rules.d/70-persistent-cd.rules /etc/udev/rules.d/70-persistent-cd.rules.bak
```
2)Open /etc/udev/rules.d/70-persistent-cd.rules in an editor (as root)
```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
3)Add MODE="0666" to every line beginning with ENV{ID_CDROM} so every line should look something like this:```
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.5-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1", MODE="0660"
```
4) Save and close. After a reboot, everything should be working ok :)



Thanks for this. Although I cannot call myself a Linux expert, I do know a few things.
You are suggesting to change the permissions to 0666. That makes every user authorized to access the dvd. Which is fine.
Yet my question remains on this weird situation. Why all of a sudden cd recording became impossible?

By the way you are suggesting 0666 rights but prompting for 0660. Is it a typo or something i don't get?

---

### Post by ubutufan on 2008-03-05
Whiffle

I did "k3b setup" on command line. So what next?
Thanks

---

### Post by Whiffle on 2008-03-05
Well, hmm.  k3bsetup (no space) is supposed to run and setup all the permissions for you, but for some reason I can't get it to run on either of my computers.  If i get it working I'll let you know...

---

### Post by WileyHunter on 2008-03-06
Glad that it works as root, but be sure to follow through with the fix...  From what I remember as an old school Unix admin you can really screw things up inadvertantly as a root user...

Have personally found that the folks on here are on top of their game as far as helping out.

WH

---

### Post by ubutufan on 2008-03-06
> **Whiffle said:**
> Well, hmm.  k3bsetup (no space) is supposed to run and setup all the permissions for you, but for some reason I can't get it to run on either of my computers.  If i get it working I'll let you know...

Of course I used the space. But all that happens is that I get into k3b as normal. What do you have in mind?

---

### Post by ubutufan on 2008-03-06
> **WileyHunter said:**
> Glad that it works as root, but be sure to follow through with the fix...  From what I remember as an old school Unix admin you can really screw things up inadvertantly as a root user...

Have personally found that the folks on here are on top of their game as far as helping out.

WH

I can only agree with you. That is why I am trying to understand what is going wrong.
Running as root is fine for tests or for whatever is worth for the immediate needs of my work. Can't do it for ever.

---

### Post by ubutufan on 2008-03-06
And now comes the best and weirdest part.

My cd gone crazy. After following the suggestion to run as root k3b and having a successful burn (no other measures were taken), now it is possible to burn as a regular user. For the sake of understanding I DID NOT CHANGE any permissions.

K3b now follows the correct procedure, that is unmount the cd first (which it did not do when the problem was on) and then continue to the burning process. Successfully.

It does not make any sense to me (surely I would not dare mark this a SOLVED). For any one with more knowledge than mine, I am at your disposal.

---

### Post by DaV|d on 2008-03-06
> **ubutufan said:**
> .
Yet my question remains on this weird situation. Why all of a sudden cd recording became impossible?

By the way you are suggesting 0666 rights but prompting for 0660. Is it a typo or something i don't get?

Regarding the first question, I cannot answer, as I am not knowledgeable enough :(
Regarding the permissions, it was a typo, as I tried it out on my dvd before suggesting ;) what I  intended to write was 0666. Since everything is working ok again, don't apply the fix now, as it might make it more difficult to understand what went wrong.

---

