---
title: "Xubuntu 6.10 not completely shutting down"
date: 2006-10-30
forum: General Help
---

### Post by Cable on 2006-10-30
When I shut down my computer with Xubuntu 6.10 on it, it does not completely shut down.  All of the fans and everything stop and nothing is running in the computer except for the fact that the power light is still on, and the usplash screen is still showing.  It does not go away until I physically push the computer's power button, then it's actually off.  Any ideas on how to fix this?  It worked perfectly with 6.06.

---

### Post by Cable on 2006-10-30
Bump.

---

### Post by Auric_Falc0n on 2006-10-31
I had the same problem on a laptop I put Edgy on. I thought it was a problem with how Edgy interacted with the hardware - it didn't see my modem either.

---

### Post by turo on 2006-10-31
I am having the same problem on my home PC.  Installed Xubuntu 6.10 (originally had 6.06, but I did a fresh format/install), and now the computer will not shut all the way down.  The monitor at least goes into standby, but the pc remains running (fans active also) until I manually power it down.

---

### Post by wasert on 2006-11-02
I have the same problem. Before I installed Xubuntu Edgy Eft, I had Ubuntu Breezy Badger and It worked fine.

any help would be greatly appreciated.

---

### Post by TwiceOver on 2006-11-03
I have the same problem on an old laptop that I put Xubuntu on.  Not that I know what I am talking about, but it seems like an ACPI problem.  My entire computer shuts down and leaves the screen sitting at the usplash progress bar (bar is empty because it finished shutting down).

It's like back with windows when you had an ACPI problem and at shutdown the computer would say "It is now safe to turn off your computer"...

---

### Post by kddsean on 2006-11-03
Had this exact problem when I first installed 6.10. Hasnt happened on last 8 reboots though. Dont know what may have changed it just hasnt happened.

---

### Post by Auric_Falc0n on 2006-11-03
I had thought it might be ACPI related too, but the packages for acpi were installed the same as Dapper, and Dapper worked fine on my laptop.

---

### Post by doobit on 2006-11-03
> **Auric_Falc0n said:**
> I had thought it might be ACPI related too, but the packages for acpi were installed the same as Dapper, and Dapper worked fine on my laptop.

It is probably an ACPI problem and there is a solution that has been discussed already here, and I tried it, and it worked for me.
Edit the /boot/grub/menu.lst file and put acpi=force at the end of the linux boot command line

---

### Post by TwiceOver on 2006-11-03
I'll have to try this when I get home.  Thanks for the info.

---

### Post by sloggerkhan on 2006-11-05
I tried that end of bootline fix and it didn't seem to work. However, she can just push the power button after it says system halted and it finished shutdown perfectly. What I don't get it that restart works correctly.

I installed Xubuntu for a friend and her comp is having this problem. It's a really low powered HP. I think it has an intel, but not sure what. Only 256 megs of RAM.

---

### Post by freshofftheufo on 2006-11-05
Bump.

I'm having this problem too. It seems there are loads of people with this exact same problem, it only fully shut down once; the first shutdown after install.

Are there any people that aren't having this problem?

---

### Post by doobit on 2006-11-06
> **sloggerkhan said:**
> I tried that end of bootline fix and it didn't seem to work. However, she can just push the power button after it says system halted and it finished shutdown perfectly. What I don't get it that restart works correctly.

I installed Xubuntu for a friend and her comp is having this problem. It's a really low powered HP. I think it has an intel, but not sure what. Only 256 megs of RAM.

Make sure you put acpi=force, not apci=force.
Edit your /boot/grub/menu.lst

kernel /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash acpi=force

save it, then reboot.

---

### Post by Cable on 2006-11-06
> **doobit said:**
> Make sure you put acpi=force, not apci=force.
Edit your /boot/grub/menu.lst

kernel /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash acpi=force

save it, then reboot.
This worked perfectly for my Xubuntu box.  Thanks!

---

