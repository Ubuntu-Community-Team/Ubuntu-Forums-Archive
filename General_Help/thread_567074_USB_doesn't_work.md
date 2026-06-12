---
title: "USB doesn't work"
date: 2007-10-04
forum: General Help
---

### Post by ktroxe on 2007-10-04
Hi!

I have 4 usb ports, but don't work any of them. I've tried with pen drives, photo cameras, printer... but nothing.

On ubuntu start, the times it make check to filesystem, I've read an error, something about usbfs, but I don't remember it well.

Thank you.

---

### Post by mscad on 2007-10-12
Click on Applications > Accesories > Terminal (or Console)

A black console will open up and type 'dmesg' or 'sudo dmesg' without the quotes.

Note: sudo means superuser do this. If you are asked for a password, type in your password.

You should see errors in dmesg that will help you decipher what is wrong.

---

