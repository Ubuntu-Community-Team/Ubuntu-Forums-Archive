---
title: "Viewing Gutsy shutdown messages"
date: 2007-12-12
forum: General Help
---

### Post by DavidS on 2007-12-12
When my computer boots or shuts down, I like to see the messages so that I know what is going on.  

But since I changed from Feisty to Gutsy, on shutdown I just see "System is shutting down", instead of the detailed list of events.

I decided to try to sort this problem out this evening, and discovered that when shutting down using the Gnome shutdown button, which is what I do most often, I get switched to tty1 which carries the "System is shutting down" message.  But the detailed messages are being printed to tty7.

So how do I get either the display to stay on tty7, or the messages to be printed on tty1?  It was never a problem before Gutsy.

---

### Post by Existentialist on 2007-12-13
If you go to your grub menu you can remove the splash screen and quiet options to see the standard output.  If you run

>sudo nano /boot/grub/menu.lst

near the end you should see something like this:

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro **quiet splash**
initrd /boot/initrd.img-2.6.17-10-generic
**quiet**
savedefault
boot

Remove the parts in bold and save something like this:

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro
initrd /boot/initrd.img-2.6.17-10-generic
savedefault
boot

Make sure to not copy this exactly as your root partition may be different just remove the two quiets and the splash parts.  You can restart and you will no longer have splash screens covering up what is happening.

---

