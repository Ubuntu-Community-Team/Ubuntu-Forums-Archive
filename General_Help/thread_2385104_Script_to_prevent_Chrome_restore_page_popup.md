---
title: "Script to prevent Chrome restore page popup"
date: 2018-02-16
forum: General Help
---

### Post by giorsoine on 2018-02-16
I work at a public library in Denmark, and we are using Ubuntu 16.04 on our info screens. They run in kiosk mode so no keyboard or mouse.

Whenever we have a power failure or some "funny" person pulled the plug on the screens they reboot as set in the BIOS, but when Chrome starts it comes up with the restore page and pop-up.

Is it possible to make a script that runs before Chrome restarts to set the crash values so Chrome think it closed the right way and start up normally?

I have seen some people suggest making a script to simulate a click on the restore button of the pop-up, but then I need to make several scripts due to us using different sizes of screens so that won't do.

I am really new to Linux, so a How to for Dummies are appreciated.

EDIT: Forgot to mention that we can't use incognito mode because each Chrome needs to remember a specific cookie with a screen ID

---

