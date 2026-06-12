---
title: "Running Ubuntu Server Windows 10 and Quickbooks"
date: 2016-08-22
forum: General Help
---

### Post by francoismoolman on 2016-08-22
Hi to all my fellow Ubuntu friends.

I wanted to know the following.

1) Is it possible to install for example  Windows 10 on Ubuntu 16.04 LTS server ?
2) And when install Quickbooks 2015/2016 on windows 10 ? I need to take my laptop with me on a business trap and need to do some transactions with Quickbooks, and want the Quickbooks files to be backup over the internet. And to see what transactions my office staff did wail I was out the office and senc with their daily transactions on the Ubuntu server running Windows 10 with Quickbooks.

Please if any one can help me with the above questions and give me some suggestions I will appreciated it very much.

Regards,

Francois

---

### Post by TheFu on 2016-08-22
Welcome to the forums.

So ... Ubuntu Servers don't have a GUI. That's the first issue. Running any GUI program on it will be very hard unless you break the "server" by installing a GUI. I wouldn't do that, but lots of people do.

There are multiple ways to accomplish the results you describe.
a) using a virtual machine
b) using remote access through a VPN 

Both of these things are non-trivial to get working for someone really new to Linux.  A few hours of background learning will be the most helpful for you at this stage, before you attempt either of these things.  About 1 hour of reading will be very helpful at this point: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)  - use Linux, not Win10 to view this page.

I suspect there is some confusion about terminology. "Ubuntu server running Windows 10 with Quickbooks." doesn't really make sense.  Ubuntu doesn't run Windows programs without either WINE or a VM. Quickbooks is very hard (might be impossible) to get working under WINE. [https://appdb.winehq.org/objectManager.php?sClass=application&iId=120](https://appdb.winehq.org/objectManager.php?sClass=application&iId=120) has the details for that method. The recent results all say "garbage".  That leads me to believe that quickbooks is running on Windows in your office and that the best way to view that information is by using remote access through a VPN to the same machine.  This way, you won't take any of that sensitive data with you and won't need to make your laptop run a big heavy VM.  Using remote access will be better for many reasons - just be certain to use a full VPN like openvpn to connect from anywhere in the world back to your office network (and the Quickbooks system).

Hope all this is clear.  This is one of the times when being in the same room really would make the explanation easier.

---

