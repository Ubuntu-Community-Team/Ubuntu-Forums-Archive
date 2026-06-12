---
title: "no passkey agent registered, bluetooth"
date: 2007-01-06
forum: General Help
---

### Post by PetePete on 2007-01-06
im trying to get my bluetrek g2 headset working with kubuntu (6.10) bit of trouble though....

when clicking on the kbluetoothd icon i see my headset, so i open it and kbluetoothd says "pairing not allowed" I inspected my syslog file and it said ...

pin_code_request (sba=MyMACaddress dba=myHeadsetMACaddress)
call_passkey_agent(): no agent registered

i've installed the latest bluez-utils and runinng a fully updated/patched kubuntu

heres a snippit of my hcid.conf file

```
# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security user;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        #passkey "BlueZ";


        # Default PIN code for incoming connections
        #passkey 0000;

        pin_helper /usr/bin/bluez-pin;
        #pin_helper /usr/lib/kdebluetooth/kbluepin;
        #pin_helper /usr/bin/bluez-pin;

        # D-Bus PIN helper
        #dbus_pin_helper;
}
```


i've tried changing the pin_helper to kbluepin, and also tried setting security to auto and enabling teh defualt 0000 pin but nothing seems to work  ](*,)

---

### Post by PetePete on 2007-01-06
very strange .. 
i installed bluez-utils manually , then kubuntu told me there were updated packages avaliable for it so i installed from addept manager, restarted and now the kde pin thingy comes up :D

---

### Post by canard on 2007-01-07
hi
i had pretty much the same kind of problem under ubuntu.
I installed all the bt packages, and tried to connect my bt headset but kbluetoothd was unable to find it and the command 
```
sudo hcitool cc xx:xx:xx:xx
```
returned me an error.....
I then reinstalled bluez-utils and it worked!!!!
When i switched on the bt adapter on my computer i got a popup message, i then put my headset into pairing and scanned with hcitool and then retried the previous command.
I then got another popup saying it was pairing with my headset and then asked for the key.

i then tested it with a wav file by doing:
```
aplay -B 1000000 -D plughw:Headset sound.wav
```
and it was working!!!!!:mrgreen:

---

### Post by rockprincess on 2007-01-20
> **canard said:**
> hi
i had pretty much the same kind of problem under ubuntu.
I installed all the bt packages, and tried to connect my bt headset but kbluetoothd was unable to find it and the command 
```
sudo hcitool cc xx:xx:xx:xx
```
returned me an error.....
I then reinstalled bluez-utils and it worked!!!!
When i switched on the bt adapter on my computer i got a popup message, i then put my headset into pairing and scanned with hcitool and then retried the previous command.
I then got another popup saying it was pairing with my headset and then asked for the key.

i then tested it with a wav file by doing:
```
aplay -B 1000000 -D plughw:Headset sound.wav
```
and it was working!!!!!:mrgreen:


hey,

are using Ubuntu 6.10 (Edgy Eft) or are you using Dapper Drake?

---

### Post by dvo on 2007-06-23
This is how I got the PIN popup working for feisty: call (even as a normal user)
```
passkey-agent --default /usr/bin/bluez-pin
```
before initiating the connection. This will register bluez-pin as the pin helper,
as you may check with ```
tail -f /var/log/syslog
```

N.B. Including in /etc/bluetooth/hcid.conf a line like
```
pin_helper /usr/bin/bluez-pin;
```
does not help - for some reason, this option is not recognized any more :(

---

