---
title: "Kaffeine locking"
date: 2006-11-01
forum: General Help
---

### Post by gary101 on 2006-11-01
Hi All
I am new to Ubuntu having installed 6.10 today. I must say that I am extremely impressed, especially after some of the other distros I have tried.  :-D 

I have managed to get my usb freeview stick set up today and installed kaffeine so I can watch TV. I managed to scan successfully for the channels from my local transmitter but when I open Kaffeine to veiw a channel the OS locks up, no response from keyboard, mouse etc and I have to do a reset to get going again. :-k 

I have noticed that most times I have to click on Kaffeine several times before it will open. :confused: 

Has anybody experienced this or have a solution?

TIA

Gary

---

### Post by gary101 on 2006-11-01
Just a bit more info if anyone can lend an opinion.

Checked dmesg and got the following output:

[17179596.572000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[17179596.572000] dvb-usb: will use the device's hardware PID filter (table count: 15).
[17179596.576000] DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom)).
[17179596.576000] DVB: registering frontend 0 (WideView USB DVB-T)...
[17179596.576000] input: IR-receiver inside an USB DVB receiver as /class/input/input3
[17179596.576000] dvb-usb: schedule remote query interval to 300 msecs.
[17179596.576000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[17179598.876000] dvb-usb: recv bulk message failed: -110

So... I am left wondering if this is a problem with kaffeine or is it to do with the error on the last line.
Either way I will need to get this error fixed, any ideas??

---

### Post by gary101 on 2006-11-04
Hi All

Figured out where my problems were!

Had built this computer out of bits laying around, totally forgot to check the spec of the USB ports on the mainboard. Turns out they are USB 1.1 and while the freecom DVB was installed and recognised I had problems with freezing/crashing while using it.

Installed a USB 2 PCI board I found in a cupboard and tuning and playback are fine.

Just goes to show how when you get stuck into complexities you can easily overlook the simple solutions.

Hope this oversight will stop anyone else having the trouble that I have had.

Gary

---

