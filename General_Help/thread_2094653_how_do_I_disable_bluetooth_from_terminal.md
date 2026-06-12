---
title: "how do I disable bluetooth from terminal"
date: 2012-12-14
forum: General Help
---

### Post by Buntu Bunny on 2012-12-14
Xubuntu 12.04 
Dell Inspiron 700m laptop

The bluetooth launcher icon shows in the panel, but when I open it and select "turn bluetooth off", nothing happens. The icon remains as does the option to turn it off. Can someone please tell me how to disable bluetooth from Terminal?

---

### Post by haqking on 2012-12-14
> **Buntu Bunny said:**
> Xubuntu 12.04 
Dell Inspiron 700m laptop

The bluetooth launcher icon shows in the panel, but when I open it and select "turn bluetooth off", nothing happens. The icon remains as does the option to turn it off. Can someone please tell me how to disable bluetooth from Terminal?

Try

```
 rfkill block bluetooth
```

unblock to re-enable

---

### Post by Buntu Bunny on 2012-12-14
> **haqking said:**
> Try

```
 rfkill block bluetooth
```

unblock to re-enable

Haqking, I appreciate the response. Here's what I get though

```
 Can't open RFKILL control device: Permission Denied
```

---

### Post by haqking on 2012-12-14
> **Buntu Bunny said:**
> Haqking, I appreciate the response. Here's what I get though

```
 Can't open RFKILL control device: Permission Denied
```

```
sudo rfkill block bluetooth
```

---

### Post by Buntu Bunny on 2012-12-14
> **haqking said:**
> ```
sudo rfkill block bluetooth
```

Well, duh on me, I should have known that. :o

With that, terminal returns to the $ symbol with no other response. The bluetooth icon on the panel remains the same. I don't have a bluetooth device to test, but can I assume it's off?

---

### Post by haqking on 2012-12-14
> **Buntu Bunny said:**
> Well, duh on me, I should have known that. :o

With that, terminal returns to the $ symbol with no other response. The bluetooth icon on the panel remains the same. I don't have a bluetooth device to test, but can I assume it's off?
```

service bluetooth status
```Using sudo ;-)

You can also do ```
sudo service bluetooth stop
```

---

### Post by Buntu Bunny on 2012-12-14
> **haqking said:**
> ```

service bluetooth status
```Using sudo ;-)

With that I get

```
bluetoot start/running, process 514
```

> You can also do ```
sudo service bluetooth stop
```

A separate message window pops up

> Connection to BlueZ failed. Bluez daemon is not running, blueman-man manager cannot continue. This probably means that there were no Bluetooth adapters detected or Bluetooth daemon was not started.

Also, Bluetooth applet icon is gone. That has to mean success. :p

---

### Post by haqking on 2012-12-14
> **Buntu Bunny said:**
> With that I get

```
bluetoot start/running, process 514
```

A separate message window pops up



Also, Bluetooth applet icon is gone. That has to mean success. :p

it does.

Welcome

Peace

---

### Post by jlh68 on 2012-12-14
Instal "Jupiter" and you will have a nice applet to control Bluetooth, WiFi, performance, screen resolution, screen orientation, choose internal screen, external screen, both screens,ans some other screen options.

You won't need the termainal to turn off Bluetooth.

---

### Post by haqking on 2012-12-14
> **jlh68 said:**
> Instal "Jupiter" and you will have a nice applet to control Bluetooth, WiFi, performance, screen resolution, screen orientation, choose internal screen, external screen, both screens,ans some other screen options.

You won't need the termainal to turn off Bluetooth.

so rather than type a 3 word command which has already been done and achieved the goal, the OP should install some more software ? LOL

---

### Post by oldos2er on 2012-12-14
> **Buntu Bunny said:**
> Well, duh on me, I should have known that. :o

With that, terminal returns to the $ symbol with no other response. The bluetooth icon on the panel remains the same. I don't have a bluetooth device to test, but can I assume it's off?

If you want to permanently disable bluetooth, run ```
sudo mv /etc/init/bluetooth.conf /etc/init/bluetooth.conf.disabled
``` That command can be reversed if you want to enable it again.

---

### Post by Buntu Bunny on 2012-12-14
> **haqking said:**
> it does.

Welcome

Peace

Haqking, thank you for your help! Much appreciated.

---

### Post by Buntu Bunny on 2012-12-14
> **oldos2er said:**
> If you want to permanently disable bluetooth, run ```
sudo mv /etc/init/bluetooth.conf /etc/init/bluetooth.conf.disabled
``` That command can be reversed if you want to enable it again.

Ann, I appreciate that. I read somewhere about someone having problems because bluetooth was activated by default at login. I will have to see about that next time I do login. If so, your advice will help.

---

### Post by Buntu Bunny on 2012-12-14
> **jlh68 said:**
> Instal "Jupiter" and you will have a nice applet to control Bluetooth, WiFi, performance, screen resolution, screen orientation, choose internal screen, external screen, both screens,ans some other screen options.

You won't need the termainal to turn off Bluetooth.

Jlh68, I've been looking at Jupiter. I noted that it is for Fuduntu and Ubuntu (gnome). I should be able to install it on Xubuntu then?

---

### Post by Psil0cybin on 2013-03-16
> **haqking said:**
> so rather than type a 3 word command which has already been done and achieved the goal, the OP should install some more software ? LOL

Everyone's different, looks like some prefer a GUI..Excepted I just switched from Windows 7 to Ubuntu to get rid of the GUI.
I love the terminal. Quick Easy, Love.:KS
But thanks for the post!
Still came in useful for me today!! much love ubuntuforums!

---

