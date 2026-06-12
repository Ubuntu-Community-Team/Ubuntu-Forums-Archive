---
title: "SynCE woes"
date: 2007-10-04
forum: General Help
---

### Post by kamatsu on 2007-10-04
Hi everyone.

From reading around the place, I have been able to get my HTC Hermes "TyTN" running Windows Mobile 6 to communicate through ipaq + synce with linux. I disabled advanced USB functionality in the connections settings on my phone. I had installed the ipaq + usbserial modules and plugging it in assigned the device to /dev/ttyUSB0. I compiled and installed Synce 0.10 from SVN, including odccm, Then I typed:

```


$ sudo synce-serial-config /dev/ttyUSB0 192.168.0.101:192.168.0.102
$ sudo odccm
$ sudo synce-serial-start


```

It would then establish a connection on my phone, and "pls" would yield results as expected.

So, yes, I have the synCE commands working, but for one problem:

To do ANYTHING with my phone right now I have to use the commandline utils. I'm not too fussed about syncing, but I really would like to be able to browse files using nautilus. I tried using  synCEFS as in here: [http://www.lvivier.info/SynceFS/](http://www.lvivier.info/SynceFS/) but this simply didn't mount the device (I think it's because it's designed for use with dccm not odccm which is used for WM6.)

Can anyone give me some instructions on how to do this?

---

