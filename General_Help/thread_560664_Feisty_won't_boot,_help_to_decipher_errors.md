---
title: "Feisty won't boot, help to decipher errors"
date: 2007-09-26
forum: General Help
---

### Post by Julian David Pitt on 2007-09-26
When booting my dual boot system grub loads and I get the Ubuntu splash screen  followed by:

[B]"Starting up
Loading please wait.....
Kinit: name_to_dev_t (dev/disk/by-uuid /741eed24-d903-4b3b-9820-7638c3c010f2) = hdb5 (3,69)
kinit trying to resume from /dev/disk 741eed24-d903-4b3b-9820-7638c3c010f2) = hdb5 (3,69)
kinit: no resume image, doing normal boot
Ubuntu 7.04 tty1"
[/B]
Can someone help me to decipher that please. At the prompt I am left with above when I try to log in my password is rejected. What on earth is happening please?
Thanks in advance of any help.

---

### Post by Skerit on 2007-09-26
Well, it's apparently trying to come out of hibernation and he thinks the files are on your hdb5 disk, but then they're not.

Euhm, what keyboard layout do you use?

It sounds stupid, but maybe, when you're entering your Username & Password, the system's using the default qwarty-keyboard-settings in stead of, say, azerty
(Like, say, your username is "skerit" (no problem) but your pas is "aaz", you would be typing "qqw" if the keyboard settings where different from Azerty)

When you get in the prompt you can type "startx" to, duh, start x.

See how far you get...

---

### Post by Julian David Pitt on 2007-09-27
Thanks for your feedback but I use the qwerty keyboard layout and have had no problems at all booting until now. Can it be fixed by running a live CD do you think or would it be easier to reinstall.

---

### Post by Skerit on 2007-09-27
It's strange that you can't log in because, when I go to the tty1 screen I see the exact same message ...

Could you try going to screen number seven? (ctrl+alt+F7) and see what pops up there?

However, this still doesn't explain why you can't log in ...

---

### Post by Julian David Pitt on 2007-10-01
If I hit clt+alt+f7 at the tty 1 prompt I get nothing at all, any ideas my friend?

---

