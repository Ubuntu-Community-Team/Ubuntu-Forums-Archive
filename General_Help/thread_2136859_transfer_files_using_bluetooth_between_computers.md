---
title: "transfer files using bluetooth between computers"
date: 2013-04-18
forum: General Help
---

### Post by uzumakifahim on 2013-04-18
I want to transfer files to my laptop from my desktop using bluetooth. On my laptop Linux Mint 14 and on my desktop Ubuntu 12.04 is running. Both of the computers have working bluetooth device. How can I do that?

Thanks in advance.

---

### Post by bart.a on 2013-04-19
Why would you do that using Bluetooth?
You can easily share folders between Ubuntu machines over the (W)LAN..

---

### Post by slickymaster on 2013-04-19
> **uzumakifahim said:**
> I want to transfer files to my laptop from my desktop using bluetooth. On my laptop Linux Mint 14 and on my desktop Ubuntu 12.04 is running. Both of the computers have working bluetooth device. How can I do that?

Thanks in advance.

One of the most common ways to network Ubuntu and Windows computers is to configure Samba as a File Server. See [this]("https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html").

---

### Post by uzumakifahim on 2013-04-19
Thanks for your replies. I know that, the most easiest way is using LAN, but now I don't have any hub and extra cable to connect both computers. Both of them has bluetooth device, for that reason I'm interested about sending files between these two computers using bluetooth. Is it possible? How?

---

### Post by HermanAB on 2013-04-19
It should be possible using the serial profile.  Install all the Bluez tools, such as Blueman.  Then it is a matter of discovering the other computer (pairing) and go from there.

---

### Post by scbingham on 2013-04-19
No need for a hub or extra lead, should just be able to connect the two together. I don't think you even need a crossover lead these days.

---

### Post by uzumakifahim on 2013-04-19
@HermanAB, thanks for your advice. I'll post the result here.

@scbingham, both of the computers have only one LAN port and my desktop is connected to the Internet using a wired connection, that's why I'm unable to connect them using a ethernet cable.

---

### Post by tgalati4 on 2013-04-19
Bluetooth transfer is dreadfully slow.  It will work for one or two files, but transfering several files will be tiresome.

Basic steps:

1.  Turn on bluetooth on both devices.
2.  Install bluetooth utilities such as *blueman*.
3.  Run the utility, discover and pair the computers.
4.  Browse the files from one computer to the other.
5.  Try to copy a file from one to the other and take note of the transfer speed.
6.  Kick yourself for attempting this.

---

### Post by bart.a on 2013-04-24
> **tgalati4 said:**
> Bluetooth transfer is dreadfully slow.  It will work for one or two files, but transferring several files will be tiresome.

+1 to that.. I tried that a couple of times but it's frustratingly slow and the connection is always so so..

In my opinion you'll be better off using a USB flash-drive to transfer several files between the two..

---

### Post by carlwsnyder on 2013-08-11
+1 for using USB flash drive.  Could also use one of the USB file transfer cables if it works under Linux.  Bluetooth works for file transfer if you do it while you are asleep, maybe.  It is faster than email from a phone, but only marginally.

---

