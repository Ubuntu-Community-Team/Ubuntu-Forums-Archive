---
title: "Wired/Wireless on a server?"
date: 2014-08-26
forum: General Help
---

### Post by dave131 on 2014-08-26
I want to build a cheap server to *try* to learn server with and set up a media center on it at the same time.  My questions about using 2 wireless adapters has already been answered, and I've been given suggestions for media server software.

Now I have a different question that I hope I can word correctly.  Can I have a local network that connects to the server "wired" port, and then have a wireless adapter for internet traffic?  If so, is there a way for devices on the local network to access the net via the wireless adapter?  I hope I've asked that in a way someone can understand.

devicea      deviceb      devicec     deviced  hard-wired to a device (is it called a switch?) which is then hard-wired to the server


broadband internet service via wireless to the server, so the server can have internet access

Can devica - deviced some how have access to the internet via that wireless connection also?

Can devices on the wireless network some how get access to devices on the servers' hard-wired connection?

I'm a newbie, so I don't even know if that makes sense.

---

### Post by nicolasdiogo on 2014-08-26
my understanding;

you want a wireless network to run your internet traffic
while the wired connection to have access only to local network.

is that correct?


if so, you need to setup the default gateway *only* on the wireless connection.
as a server, i would expect these details to be set at boot.

look in your file:
/etc/network/interfaces

i have not spoon fed you as you are learning.
there is sufficient breadcrumbs for you to follow from here.

if you are stuck let us know.

enjoy the journey!

---

### Post by dave131 on 2014-08-26
Thanks - I'll keep that handy.  I'm in the process of trying to gather "tidbits" and the hardware before I start.  Next up I'm going to check the docs site and see if there is a beginners guide to ubuntu server and one for beginning networking as well.

---

### Post by nicolasdiogo on 2014-08-26
good idea to check the hardware prior to buying


have a look at the rapsberry pi project pages.

you can buy hardware from related suppliers with confidence that it will work fine on linux.

but you also have to consider other things like speed of wireless adapter and speed of router.


keep us posted

---

