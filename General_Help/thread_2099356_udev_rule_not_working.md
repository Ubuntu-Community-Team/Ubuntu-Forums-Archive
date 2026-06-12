---
title: "udev rule not working"
date: 2012-12-29
forum: General Help
---

### Post by insecure hyena on 2012-12-29
Hi community here I am with a tricky problem related udev.
I've write the following rule but it doesn't seem to work:

ACTION=="add", ATTRS{vendor}=="SAMSUNG ", ATTRS{model}=="GT-I8150 Card   ", RUN+="sh /home/pippo/scripts/sync-music.sh"

Actually I'm trying to automatically sync a folder on my notebook with a folder on a smartphone (a Samsung GT-I8150)...
The script doesn't seem to be called...the statements written in it are not executed...at this time there's only a call to the notification system...
Calling the script from the command line works.
Before anyone ask...Yes, I give to the script the execution privilege...
Please help :(

---

### Post by steeldriver on 2012-12-29
why sh in your RUN action? It probably can't find 'sh' without the full path, /bin/sh will probably work (although remember it is likely a symlink to dash NOT bash) but if the script is executable, it should be sufficient to call it directly, i.e.

```
RUN+="/home/pippo/scripts/sync-music.sh"
```FWIW I'd suggest putting the script in /usr/local/bin instead - just because udev actions are not user-specific

---

### Post by insecure hyena on 2012-12-29
Thanks man for your quick response :).
I've already tried not specifying the sh and by specifying /bin/sh but it doesn't seem to work.
Regarding the location of the rule I've read that it could be located in /etc/udev/rules.d/.

---

### Post by steeldriver on 2012-12-29
Yes /etc/udev/rules.d is the correct place for the rule file - I was referring to the script file for your run action

I'm only taking baby steps with udev myself so I don't really know what else to suggest - fwiw here's one of mine that I know works (and fyi changing the RUN action to "sh /usr/local/bin/notify-usb" *does* break it):

```
ATTR{idVendor}=="0483", ATTR{idProduct}=="2015", SYMLINK+="bioscrypt", GROUP:="root", MODE:="0660", RUN+="/usr/local/bin/notify-usb"
```Did you use udevadm to check the attribute names match exactly? I decided to use numerical attribute ids

---

### Post by insecure hyena on 2012-12-29
Ok sorry I've misunderstood the location thing.
However yes I've used udevadm info to get and check the ATTRS values.
I'll try your rule by replacing the values accordingly.
For the moment thank you again man! ;)

---

