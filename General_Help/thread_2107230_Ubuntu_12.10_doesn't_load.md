---
title: "Ubuntu 12.10 doesn't load"
date: 2013-01-21
forum: General Help
---

### Post by cave2596 on 2013-01-21
Hello,

i am workin the first time with Ubuntu.
I have installed Ubuntu 12.10 and worked a bit with it.
When I wanted to restart the Computer, the Ubuntu startscreen appears, but it is not loading.
Can someone help me?
Do I have to install Ubuntu again?

Thank you for your help!
Greetings from Germany,
cave2596

---

### Post by oldfred on 2013-01-21
Welcome to the forums.

When you say start screen, do you mean grub menu, or later in boot process the colored screen just before the login, the login, or the main Ubuntu screen but missing the icons on the left for applications?

Before grub menu it is boot issues. 
Later it may be video driver or related issues. Then what video driver?

---

### Post by cave2596 on 2013-01-21
after the boot menu, before logging in, there is the Ubuntu loading screen.
(Simmilar to this: [http://i.stack.imgur.com/tOiLf.jpg](http://i.stack.imgur.com/tOiLf.jpg) )
But there the points don't light up - it doesn't load.

---

### Post by oldfred on 2013-01-21
What video card?

You can try recovery mode, and try nomodeset on boot.

At grub menu use e to edit and on linux line change quiet splash to nomodeset.

Perhaps a video driver or other update messed up video driver.  If not video try to watch scrolling boot driver entries to look for errors. All that is also in /var/log/dmesg.

---

### Post by cave2596 on 2013-02-10
I have reinstalled Ubuntu now.

And hey, it works.

Thank you for your replies!

---

