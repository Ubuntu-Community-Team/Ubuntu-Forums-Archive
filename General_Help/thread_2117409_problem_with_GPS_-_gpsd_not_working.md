---
title: "problem with GPS - gpsd not working"
date: 2013-02-18
forum: General Help
---

### Post by briggers on 2013-02-18
I am trying to use an external Bluetooth (BT) GPS reciever through a BT USB dongle.

The  BT element all seems to work OK. I can pair the devices and connect.  The connection comes up on /dev/rfcomm0. If I ```
cat  /dev/rfcomm0
``` I can see a stream of NMEA data from the GPS. Also,  because Viking, which is the program I would like to use, only seems to  connect on that file I have made a syslink from /dev/ttyUSB0 to  /dev/rfcomm0. Again a ```
cat /dev/ttyUSB0
``` produces a stream of  data

Next I try to connect using gpsd. It did not work at all  despite the deamon running. So I kill the deamon with ```
killall  gpsd
``` and restart it in non-deamonised debug mode with ```
gpsd  -N -b -D 3 /dev/ttyUSB0
```This shows:
```
$ sudo gpsd -b -N -D 3 /dev/ttyUSB0
gpsd:INFO: launching (Version 3.4)
gpsd:INFO: listening on port gpsd
gpsd:INFO: NTPD ntpd_link_activate: 1
gpsd:INFO: stashing device /dev/ttyUSB0 at slot 0
gpsd:INFO: running with effective group ID 20
gpsd:INFO: running with effective user ID 65534
gpsd:INFO: startup at 2013-02-18T14:38:56.000Z (1361198336)
```which looks to me to be correct.

Then I start **cgps** in another terminal and got the following added to the above in the first terminal:

```
gpsd:INFO: opening read-only GPS data source type 4 and at '/dev/ttyUSB0'
gpsd:ERROR: device open failed: Device or resource busy - retrying read-only
gpsd:ERROR: read-only device open failed: Device or resource busy
gpsd:ERROR: /dev/ttyUSB0: device activation failed.
gpsd:INFO: reconnection attempt on device 0
gpsd:INFO: opening read-only GPS data source type 4 and at '/dev/ttyUSB0'
gpsd:ERROR: device open failed: Device or resource busy - retrying read-only
gpsd:ERROR: read-only device open failed: Device or resource busy
gpsd:ERROR: /dev/ttyUSB0: device activation failed.
gpsd:INFO: reconnection attempt on device 0
gpsd:INFO: opening read-only GPS data source type 4 and at '/dev/ttyUSB0'
gpsd:ERROR: device open failed: Device or resource busy - retrying read-only
gpsd:ERROR: read-only device open failed: Device or resource busy
gpsd:ERROR: /dev/ttyUSB0: device activation failed.
gpsd:INFO: reconnection attempt on device 0
gpsd:INFO: opening read-only GPS data source type 4 and at '/dev/ttyUSB0'
gpsd:ERROR: device open failed: Device or resource busy - retrying read-only
gpsd:ERROR: read-only device open failed: Device or resource busy
gpsd:ERROR: /dev/ttyUSB0: device activation failed.
gpsd:INFO: detaching 127.0.0.1 (sub 0, fd 6) in detach_client
```

```
ps aux | grep gpsd
```

shows that gpsd is running

xgps also gives a blank with the same error messages 

So  it all looks as though I have a good connection to the GPS receiver and  am getting data correctly but just can't get gpsd to read it.

Any ideas would be gratefully received

PS running with Xubunto 12.04
and both gpsd and gpsd-clients installed from apt-get

Thanks

---

