---
title: "Why does my Ubuntu 704 PC all of a sudden just boot to a &quot;GRUB&quot; CLI?"
date: 2008-04-07
forum: General Help
---

### Post by klokwyze on 2008-04-07
I didn't do anything different than normal recently. When I go to boot up my PC it just shows a prompt "grub>" idling. Above this prompt it says a bunch of **** like "[ Minimal BASH-like line editing is supported.... completetions of a device/filename.]"

I have a Super GRUB boot disk ready to use if I need to. What's wrong? How can I fix this?

---

### Post by klokwyze on 2008-04-07
I change my mind actually. Back to Windows. I'll be back in another year or two. :lolflag:

---

### Post by NightwishFan on 2008-04-07
Sorry you feel that way, you may or may not be missed.

---

### Post by Belak on 2008-04-07
When you boot into grub, type geometry (hd
and then hit TAB.
If there's only 1 HD, hd0, should pop up, so finish the command as:
geometry (hd0)

If there's more than one HD, a few hd numbers should pop up.
Use the geometry command with each HD so you can figure out which one ubuntu is installed on.

When you figure out which partition you've installed Ubuntu on, run the following command:
root (hd#,#)
Where the first # is the HD # and the second # is the partition number.
Next Run
setup (hd#)
where the # is the hard drive #.

It should hopefully be fixed now.
If it isn't then sorry... I probably forgot something.

---

### Post by klokwyze on 2008-04-07
> **NightwishFan said:**
> Sorry you feel that way, you may or may not be missed.

TBH, I was excited about learning this system. I was going to use this system as a file server (got a nice book on Samba) & live audio recording setup BUT as soon as I got the audio ALMOST working, this boot problem comes up. I simply don't understand the system too well & I really like Ubuntu (I'll be back), but I'm just running into WAY too many problems for this operating system to serve my needs.

PS. I don't give 2 shits if I'm missed or not. ;-)

---

### Post by klokwyze on 2008-04-07
> **Belak said:**
> When you boot into grub, type geometry (hd
and then hit TAB.
If there's only 1 HD, hd0, should pop up, so finish the command as:
geometry (hd0)

If there's more than one HD, a few hd numbers should pop up.
Use the geometry command with each HD so you can figure out which one ubuntu is installed on.

When you figure out which partition you've installed Ubuntu on, run the following command:
root (hd#,#)
Where the first # is the HD # and the second # is the partition number.
Next Run
setup (hd#)
where the # is the hard drive #.

It should hopefully be fixed now.
If it isn't then sorry... I probably forgot something.

thanks for the help mate, but I'm giving this one up for a while.

---

### Post by NightwishFan on 2008-04-07
I assume you know I was just messing with you. I hope you can get this all sorted out. Perhaps give Hardy a try when it is released.

---

### Post by klokwyze on 2008-04-07
> **NightwishFan said:**
> I assume you know I was just messing with you. I hope you can get this all sorted out. Perhaps give Hardy a try when it is released.

Man I love Ubuntu, but for some reason, this PC/installation has been a constant pain in the ***. I have put in like 10+ hours messing with it & right now, I just need the damn thing to work. I'll probably try again by 2009 or something. Now, back to my multiple illegal copies of Windows. :)

---

### Post by NightwishFan on 2008-04-07
Well good luck sir.

---

