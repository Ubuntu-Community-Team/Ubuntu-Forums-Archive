---
title: "Ubuntu 7.04 server + serial console?"
date: 2007-08-01
forum: General Help
---

### Post by viper52b on 2007-08-01
Hi all,

I've been looking for this for some while, and haven't found a clear answer.  

I would like to be able to login on my ubuntu 7.04 server through serial console/terminal, because the server will be used for testing.  This means it will be moved frequently and installed headless in different racks (without always knowing a working IP address in advance).

I've done this before with previous versions with ubuntu, which works just fine!  This is possible by changing some lines in the /etc/inittab file.  I've already figured out this file is not in use anymore, and it is replaced by something called upstart, in the /etc/event.d folder...

I'm already able to get the boot messaged directed also to the serial console, and I get a login prompt over the serial console for a couple of seconds.  When the server is completely booted, it stops responding.

Any ideas on how to get this working?

Thanks in advance!
Bert

---

### Post by AnRa on 2007-08-01
Why don't you just login using the hostname?

---

### Post by viper52b on 2007-08-01
Hi,

Once the server is relocated, it may as well have some IP adres which does not work on the new location (say located from 10.0.0.x to 192.168.1.x for an easy example).

The most easy sollution in the past was to just connect to the serial console with my laptop and change the IP settings...

---

### Post by viper52b on 2007-08-02
*bump*

No one ever done this on ubuntu 7.04?  I must be a strange guy :-s

---

### Post by Ploes on 2007-08-04
Your not strange! I'm trying to do it as well!

I used to have this functionally from Fedora and I want to keep it for that day when I brake something to do with networking!

Typing: **sudo getty -L ttyS0 115200 vt100 **sets up a usable serial connection, so the command still works, it where it needs to be entered that I cant quite work out!

---

### Post by viper52b on 2007-08-06
> **Ploes said:**
> Your not strange! I'm trying to do it as well!

I used to have this functionally from Fedora and I want to keep it for that day when I brake something to do with networking!

Typing: **sudo getty -L ttyS0 115200 vt100 **sets up a usable serial connection, so the command still works, it where it needs to be entered that I cant quite work out!

Indeed, I also noticed this...
The new usage of /etc/event.d instead of /etc/inittab is quite confusing regarding serial connections.

At least it's good to now that I'm not the only one who's affraid to lock himself out of his box :D.

---

### Post by Ploes on 2007-08-09
Right I think I've got it sussed!

**sudo cp tty6 ttyS0** then **sudo nano ttyS0**

Replace the last line : **exec /sbin/getty 38400 tty6** with **exec /sbin/getty -L ttyS0 115200 vt100**

**sudo start ttyS0** will now start a serial connection, that will also start when the box is rebooted.

Please let me know your result!

---

### Post by nickjqw on 2007-08-13
That worked for me, thanks!  I did choose to go with 9600 baud, though:

exec /sbin/getty -L ttyS0 9600 vt100

---

