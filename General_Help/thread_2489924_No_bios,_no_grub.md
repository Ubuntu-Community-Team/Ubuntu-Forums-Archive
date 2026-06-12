---
title: "No bios, no grub"
date: 2023-08-15
forum: General Help
---

### Post by xinuzi on 2023-08-15
After a recent lubuntu installation on a laptop I'm wondering why it's impossible to enter the system bios with F2 or anything else.

---

### Post by yancek on 2023-08-15
The operating system install should not have any effect on access to the BIOS.  Are you saying you accessed the BIOS earlier to set the device on which you had the Lubuntu installer  to first boot priority but cannot do so now?  What type of computer/hardware do you have?  Have you looked online for a manual with instructions?

If Lubuntu is using Grub to boot and is the only OS installed, there will be no Grub menu by default.  You can change that in the Grub config files.

---

### Post by xinuzi on 2023-08-15
It's a Toshiba Satellite.

Before F2 opened the bios menu when the system splash screen appeared.

Not anylonger.

---

### Post by Rubi1200 on 2023-08-15
Is the laptop only running Lubuntu or also Windows?

---

### Post by somebodeez on 2023-08-15
I'm not sure whether I should or am aloud to answer this, but I've had this exact problem myself in the past, after installation I was no longer able to access BIOS during the boot proccess.

The solution for me was to reinstall Grub from a live USB, personally I had to adapt the instructions from this thread to fit my own needs accordingly, and I could then access BIOS normally again. 

[https://askubuntu.com/questions/1012332/manually-install-grub-on-efi-partition?f=331](https://askubuntu.com/questions/1012332/manually-install-grub-on-efi-partition?f=331)

---

### Post by Rubi1200 on 2023-08-15
> **somebodeez said:**
> I'm not sure whether I should or am aloud to answer this, but I've had this exact problem myself in the past
This is a community forum and we all help as we can and all contributions are worthy because we can learn something new.


@xinuzi: I recommend booting from a liveUSB and then open a terminal and paste the output from this command:
```
sudo fdisk -l
``` lowercase L not i

---

### Post by tea for one on 2023-08-15
> **xinuzi said:**
> After a recent lubuntu installation on a laptop I'm wondering why it's impossible to enter the system bios with F2 or anything else.
From your running session, open a terminal and try this:-
```
sudo systemctl reboot --firmware-setup
```

---

### Post by xinuzi on 2023-08-15
> **Rubi1200 said:**
> Is the laptop only running Lubuntu or also Windows?

Windows, what's that? ;-)

Nope, for the moment only Lubuntu.

Have created a Mint xfce boot disk in the meantime...

Maybe install that next to Lubuntu, or fully.

I wonder if the fact that I can't enter the bios to select usb boot will hinder...

The system uses systemd.
I'll try this first: 

```
systemctl reboot --firmware-setup
```

---

### Post by tea for one on 2023-08-15
> **xinuzi said:**
> I'll try this first: 

```
systemctl reboot --firmware-setup
```

```
[COLOR="#0000FF"]sudo[/COLOR] systemctl reboot --firmware-setup
```
Don't forget elevated privileges

---

### Post by xinuzi on 2023-08-15
> **tea for one said:**
> ```
[COLOR=#0000FF]sudo[/COLOR] systemctl reboot --firmware-setup
```
Don't forget elevated privileges

Elevated privileges indeed...

Now, would you believe it worked without them!

And that boot code line brought the solution and told me what was the probable problem with the bios not opening.

Namely, an attached HDD NTFS drive.
In the bios boot menu it was situated on top of the hard drive as first boot option.
I manually placed the hard drive on top of it as first boot option (F5-F6), saved, exited.
After that, when I relaunch the machine, with that drive still attached, the bios does open upon system splash with F2.

Good to know, also for others.

Compared to another machine with the same Lubuntu desktop and version.
Bios normally accessible there.
So I consider it a unique, resolvable phenomenon.

Thanks for the support and such, but the problem is solved herewith.


Have a nice day [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

---

### Post by xinuzi on 2023-08-15
> **tea for one said:**
> From your running session, open a terminal and try this:-
```
sudo systemctl reboot --firmware-setup
```

(see next, double post, sorry, thought it didn't pass)

---

### Post by xinuzi on 2023-08-15
> **tea for one said:**
> From your running session, open a terminal and try this:-
```
sudo systemctl reboot --firmware-setup
```

Yes. I came to the same conclusion in the meantime at the same time.

And it worked.

Without sudo (my god, have to check that...)

---

### Post by tea for one on 2023-08-15
It is a nice gesture to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

