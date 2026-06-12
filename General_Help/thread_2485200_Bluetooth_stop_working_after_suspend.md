---
title: "Bluetooth stop working after suspend"
date: 2023-03-22
forum: General Help
---

### Post by marrocs on 2023-03-22
Hello everyone

So, my bluetooth stop working after suspend (is that the correct word?) my laptop and close it's screen. In the morning, after woke it up of suspension, i've noticed the same problem, but a simple 'init 6' has resolved. Now, it does nothing.

IDK if it matters, but after installing the OS (22.04) the bluetooth had problems. Every time it connect, the wifi was dropped. i got it resolve  by adding 

'options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8'

at the end of /etc/modprobe.d/iwlwifi.conf file.



So, I've already tried:

```

marrocs@marrocs-Vostro-3550:~$ sudo systemctl start bluetooth
[sudo] senha para marrocs: 
marrocs@marrocs-Vostro-3550:~$ rfkill unblock bluetooth
marrocs@marrocs-Vostro-3550:~$ 
```

and:

```

marrocs@marrocs-Vostro-3550:~$ ps aux | grep blue
marrocs     5748  0.0  0.0   9104  2360 pts/0    R+   18:15   0:00 grep --color=auto blue
marrocs@marrocs-Vostro-3550:~$ systemctl | grep blue
marrocs@marrocs-Vostro-3550:~$ 
```

My laptop is a Dell vostro 3550, with 5.19.0-35-generic kernel.



So, does anybody got any idea?


(This is my first post, so sorry if i made something wrong)

---

### Post by MAFoElffen on 2023-03-22
Try this:
```

hci_id=$(rfkill list | grep hci | cut -d: -f1)
rfkill block $hci_id
rfkill unblock $hci_id

```

---

