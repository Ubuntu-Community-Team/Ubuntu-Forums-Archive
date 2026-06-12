---
title: "Ubuntu 16.04 Constant UPS &quot;Low Battery&quot; messages in terminal!"
date: 2018-12-22
forum: General Help
---

### Post by t4nd4r on 2018-12-22
Hey all,

Hoping someone can help me stop these annoying messages.

I recently set up a Cyberpower UPS, and installed NUT to monitor them on Ubuntu 16.04.

I did my best to configure the service and settings, and it definitely works when I pull the power cord out of the wall (begins the shutdown process).

My only complaint is that whenever I'm logged into a terminal, I keep a message every now and then like this:

```
Broadcast message from root@TandarLinux (somewhere) (Sat Dec 22 12:51:19 2018):


UPS cyberpower@localhost battery is low

```

But... I don't believe the battery is low? Either way, I don't want these interrupting my terminal session. 

I went into my /etc/nut/upsmon.conf file and tried to find the source of the message, which I believe I found and commented out... but I'm still getting the message after reloading/restarting the upsmon service


```
# Example:
# NOTIFYCMD /bin/notifyme
NOTIFYCMD /usr/local/bin/nut-notify.sh
# NOTIFYFLAG ONLINE SYSLOG+WALL+EXEC

```

The nut-notify.sh is just a script that should send me an e-mail if power failure occurs (which doesn't work either :()

What could I be missing?

I wouldn't mind the terminal message if the battery was actually in a low power state, but I believe it is falsely reporting that?

```

root@TandarLinux:/etc/nut$ upsc cyberpower
Init SSL without certificate database
battery.charge: 100
battery.charge.low: 35
battery.charge.warning: 20
battery.mfr.date: CPS
battery.runtime: 300
battery.runtime.low: 300
battery.type: PbAcid
battery.voltage: 14.1
battery.voltage.nominal: 12
device.mfr: CPS
device.model: UPS OR500
device.type: ups
driver.name: usbhid-ups
driver.parameter.pollfreq: 30
driver.parameter.pollinterval: 2
driver.parameter.port: auto
driver.version: 2.7.2
driver.version.data: CyberPower HID 0.3
driver.version.internal: 0.38
input.transfer.high: 140
input.transfer.low: 90
input.voltage: 121.0
input.voltage.nominal: 120
output.voltage: 121.0
ups.beeper.status: enabled
ups.delay.shutdown: 20
ups.delay.start: 30
ups.load: 77
ups.mfr: CPS
ups.model: UPS OR500
ups.productid: 0601
ups.realpower.nominal: 300
ups.status: OL LB
ups.test.result: Done and passed
ups.timer.shutdown: -60
ups.timer.start: -60
ups.vendorid: 0764

```

---

