---
title: "problem with wireless lan"
date: 2008-02-26
forum: General Help
---

### Post by onemanclapping on 2008-02-26
hi,

at my university, their wireless network uses a weird sistem to connect and everytime I turn the computer on, I need to do this:

[http://img235.imageshack.us/img235/2497/screenshotcm0.png](http://img235.imageshack.us/img235/2497/screenshotcm0.png)

what can I do for it to connect automatically?

thanks in advance

---

### Post by Prospero2006 on 2008-02-26
Write a script.

iwconfig ethX key XXXXXXXXXXX
dhcpcd ethX


or whatever.

I connect to several wireless access points throughout the week, and I have scripts for each of them. Make it executable. It's not really an inconvenience to type a program name at the command line to fire up the network for me. 

(If you are always connecting to that particular wireless point, add the script to your X startup.)

---

