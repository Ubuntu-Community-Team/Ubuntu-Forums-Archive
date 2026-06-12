---
title: "Testers needed for a Dell Bluetooth 355 Howto =)"
date: 2007-04-11
forum: General Help
---

### Post by weijie90 on 2007-04-11
Hi,

I managed to get my Dell Bluetooth 355 to work in my Inspiron 6400, after some command line hacks. I want to share my solution, buy I need to test it first. If you have this bluetooth card, and preferably an Inspiron 6400, please help me to help other 6400 users by trying this Howto:

```


sudo hciconfig hci0 reset

sudo /etc/init.d/bluetooth restart

sudo gedit /etc/rc.local


```


add "hciconfig hci0 reset" to /etc/rc.local
add "hciconfig hci0 inqmode 0" to /etc/rc.local
Both lines should be above "exit 0".

```

sudo gedit /etc/bluetooth/hcid.conf

```

change security user to security auto
change passkey

```

sudo /etc/init.d/bluetooth restart

sudo aptitude install gnome-bluetooth

```

Run gnome-bluetooth from Applications-> Bluetooth File Sharing. You can receive files sent over BT only when gnome-bluetooth is running.

Send files by right-clicking on them in nautilus or the gnome desktop and selecting "Send". You will have the option to send the file via BT.

Command line file transfers (send only):

```

'hcitool scan'  to get bluetooth address
gnome-obex-send -d <bt_address> <file>

```

Thank you very much for trying this. Please tell me whether it works for you.

---

### Post by cstaats4 on 2008-01-26
Hello,

I know its an old thread (almost a year) but I just tested this on my Dell Inspiron 6400 w/Dell 355 and it works fine with my T-Mobile Dash. My Dash gives an error about the passkey, but it sends the file fine.

Cheers,
Charlie

---

### Post by weijie90 on 2008-01-26
Cool, thanks!

I have a feeling that my howto is obsolete, as Bluetooth probably works out of the box with Gutsy.

---

