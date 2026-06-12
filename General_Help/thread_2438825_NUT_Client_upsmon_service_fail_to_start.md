---
title: "NUT Client: upsmon service fail to start"
date: 2020-03-18
forum: General Help
---

### Post by parotter on 2020-03-18
I am trying to set-up Ubuntu 18.04 as a nut-client from a UPS server.

I first installed nut-client
```

sudo apt install nut-client

```

I was able to query UPS info by using upsc:
```

upsc ups@192.168.xxx.xxx
Init SSL without certificate database
battery.charge: 100
battery.charge.low: 10
battery.charge.warning: 50
battery.date: not set
battery.mfr.date: 2019/09/22
battery.runtime: 42300
battery.runtime.low: 120
battery.type: PbAc
battery.voltage: 13.6
battery.voltage.nominal: 12.0
device.mfr: APC
device.model: Back-UPS ES 650G1
device.serial: 4B1938P42222  
device.type: ups
driver.name: usbhid-ups
driver.parameter.pollfreq: 30
driver.parameter.pollinterval: 5
driver.parameter.port: auto
driver.version: DSM6-2-2-24922-broadwell-fmp-repack-24922-190507
driver.version.data: APC HID 0.95
driver.version.internal: 0.38
input.sensitivity: high
input.transfer.high: 139
input.transfer.low: 92
input.voltage: 116.0
input.voltage.nominal: 120
ups.beeper.status: enabled
ups.delay.shutdown: 20
ups.firmware: 906.W1 .D
ups.firmware.aux: W1 
ups.load: 0
ups.mfr: APC
ups.mfr.date: 2019/09/22
ups.model: Back-UPS ES 650G1
ups.productid: 0002
ups.serial: 4B1938P42222  
ups.status: OL
ups.timer.reboot: 0
ups.timer.shutdown: -1
ups.vendorid: 051d

```

My upsmon.conf file is set up as follows:
```

MONITOR ups@192.168.xxx.xxx 1 remoteuser xxx slave       # UPS and upsd server, user and passowrd and 
MINSUPPLIES 1                              # set we are slave. The 1 min that we depend only on 1 
                                           # power supply
SHUTDOWNCMD "/sbin/shutdown -h +0"        # Command to do the shutdown when needed

# Polling a timing
POLLFREQ 10                                # Frequency poll when online
POLLFREQALERT 4                            # Frequency poll when on battery
FINALDELAY 5                               # Delay prior to run SHUTDOWNCMD
POWERDOWNFLAG /etc/killpower

```

I checked using telnet that the login works well.

But I am not able to start the monitoring service. I could get error messages either.
```

sudo systemctl status nut-monitor.service
&#9679; nut-monitor.service - Network UPS Tools - power device monitor and shutdown controller
   Loaded: loaded (/lib/systemd/system/nut-monitor.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2020-03-18 15:59:22 EDT; 22min ago

Mar 18 15:59:22 systemd[1]: Starting Network UPS Tools - power device monitor and shutdown controller...
Mar 18 15:59:22 systemd[1]: nut-monitor.service: Control process exited, code=exited status=1
Mar 18 15:59:22 systemd[1]: nut-monitor.service: Failed with result 'exit-code'.
Mar 18 15:59:22 systemd[1]: Failed to start Network UPS Tools - power device monitor and shutdown controller.

```

I tried to use
```
upsmon -h
```

but I wasn't able to see anything from the output.

Any ideas where I should look into? Thanks for help!

---

