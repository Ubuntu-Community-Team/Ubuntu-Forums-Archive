---
title: "Freecom DVB trouble"
date: 2006-11-25
forum: General Help
---

### Post by gary101 on 2006-11-25
Hi

I have had this Freecom DVB USB Stick working before in Ubuntu, but have had to do a reinstall. Apart from running with the K7 Kernel, I have done everything the same as when I managed to get the Freecom working. (I am using 6.06)

Seems like the driver gets loaded but when in Kaffeine there is no tuning option. This led me to try tuning with dvb-utils, which output the error below:

????@bunt-box:/usr/share/doc/dvb-utils/examples/scan/dvb-t$ scan dvb-t/uk-Belmont > ~/channels.conf
scanning dvb-t/uk-Belmont
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1884: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

My output from dmesg is:

[17179594.036000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
[17179594.052000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179594.052000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[17179594.136000] dvb-usb: downloading firmware from file 'dvb-usb-wt220u-01.fw' to the 'Cypress FX2'
[17179594.164000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179594.232000] ts: Compaq touchscreen protocol output
[17179594.244000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and conne cted.
[17179594.244000] usbcore: registered new driver dvb_usb_dtt200u

If anyone can point me in the right direction it would be very much appreciated.
P.S.  I am not sure what the 'Cypress FX2' is in the dmesg,

---

### Post by gary101 on 2006-11-26
Got impatient waiting for a reply.

Reinstalled and ran the setup on the stock kernel, seems to have sorted out the problem.

---

