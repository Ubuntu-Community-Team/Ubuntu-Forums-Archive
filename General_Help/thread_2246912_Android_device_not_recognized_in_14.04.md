---
title: "Android device not recognized in 14.04"
date: 2014-10-04
forum: General Help
---

### Post by jmriverofernandez-4 on 2014-10-04
Hi,

I was trying to connect my Android phone to my laptop as an MTP device. Two days ago I had tried it and it had worked fine. 
This time it was recognized in PTP mode but not in MTP. I ran this commands:
"sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9" and "sudo apt-get install mtpfs"

Then I realized that if I connected the phone on the usb port of the other side it was recognized and everything ran fine. But then I decided to do something dumb and I ran
"sudo apt-get remove libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9" and "sudo apt-get remove mtpfs"


And then the phone wasn't recognized anymore, not even as a PTP device. I ran again
"sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9" and "sudo apt-get install mtpfs"

but that didn't solve the issue.

Any ideas of how to fix this?

Kind regards.

---

### Post by fly-by-night on 2014-10-04
My phone (S2) is finicky about the USB cable I use. I don't use Blackberry or random cables that don't fit nice and firmly in the micro USB slot. I do not install any software in Xubuntu (on 2 different computers) to connect MTP to my Galaxy S2 and a cheap Alcatel.

edit: and Samsung Tab 3

---

### Post by jmriverofernandez-4 on 2014-10-04
This has nothing to do with the cable. As I said before, the phone used to be recognized, and now it doesn't and it has to do with something I did in Ubuntu. By the way, I also right clicked the icon of the phone in the launcher and pressed unlock from launcher. Does that have to do with what is happening?

---

### Post by Jonor on 2014-10-04
If it is any help try using one of the file transfer apps that work through a web browser over wifi to get connected.

---

