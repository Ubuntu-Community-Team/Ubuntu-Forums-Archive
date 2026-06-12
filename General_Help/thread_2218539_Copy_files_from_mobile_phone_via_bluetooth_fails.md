---
title: "Copy files from mobile phone via bluetooth fails"
date: 2014-04-21
forum: General Help
---

### Post by Byrial_Jensen on 2014-04-21
I am trying to copy files from a Nokia 3110 phone [SIZE=2][FONT=Tahoma]to my laptop running lubuntu 14.04 using bluetooth. I use blueman and can make a connection to the phone and browse the files on it [/FONT][/SIZE]and see their names and sizes etc. But I cannot transfer the files to the laptop.

If I try to copy/paste in the file browser, I get an error message saying "Another operation in progress" when I try to paste.

Opening the phone files in other programs also fails. E.g. firefox says: "Firefox doesn't know how to open this address, because the protocol (obex) isn't associated with any program." The Image Viewer says "Failed to open file '/run/user/1000/gvfs/obex:host=%5B00%3A1E%3AA3%3ADE%3AA3%3A73%5D/Billeder/Billede001.jpg': Input/output error".

Please help. What I am missing?

---

### Post by gtriderxc on 2014-08-10
I have exactly the same problem! On 12.04 everything was correct. On Debian works perfectly. Only 14.04 makes problems. I also try to connect with a Nokia but 5550.

---

### Post by hendrik-0 on 2014-10-03
same here. i found out that it is a bug.
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1284308](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1284308)
the workarounds posted there also did not help (as acknowledged in the bugreport)

---

