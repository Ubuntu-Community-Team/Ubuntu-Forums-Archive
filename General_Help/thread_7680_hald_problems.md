---
title: "hald problems"
date: 2004-12-09
forum: General Help
---

### Post by boobytrapped on 2004-12-09
I am running into problems with the hal daemon.  I am unable to get my camera/usb-key automounted.  Also, I am finding that when I run hal-device-manager (from the System Configuration menu) I get an error message about hal service not running.  Even lshal does not run.  I get error messages like the following:

```

ali@bini:/var/run $ lshal
lshal version 0.2.98
libhal.c 696 : org.freedesktop.DBus.Error.ServiceDoesNotExist raised
"Service "org.freedesktop.Hal" does not exist"

*** [DIE] lshal.c:dump_devices():70 : Couldn't obtain list of devices
```

I know that hald is running -- as is shown below.

```
ali@bini:/var/run $ ps ax | grep hal
 4910 ?        Ds     0:00 /usr/sbin/hald --drop-privileges
```

Google is not turning up anything on this issue - so I am really really stumped by this.  Does anyone have any idea about what is going on here?  

Any kind of help will be very appreciated.

---

### Post by nzgreen on 2004-12-10
You should try running hald in a console to see it's output.

First kill the HAL daemon:
```
sudo killall hald
```

The start it in non-daemon verbose mode:
```
sudo /usr/sbin/hald --daemon=no --verbose=yes
```

This should output a LOT of text to your console.  This should give you some idea of where it's failing.

---

### Post by randy on 2004-12-10
Are you running the experimental version of Network Manager that is available for Ubuntu? When I ran that I had a problem similiar to yours.

---

### Post by boobytrapped on 2004-12-10
Okay - the hal deamon just won't die for some reason..

```
ali@bini:~ $ sudo killall -9 hald
ali@bini:~ $ ps ax | grep hald
 4965 ?        Ds     0:00 /usr/sbin/hald --drop-privileges
ali@bini:~ $ sudo kill -9 4965
ali@bini:~ $ ps ax | grep hald
 4965 ?        Ds     0:00 /usr/sbin/hald --drop-privileges
24134 pts/1    R+     0:00 grep hald
```

I am not runing any experimental version of the hal daemon or of the network manager applet.

---

### Post by boobytrapped on 2004-12-10
[QUOTE=boobytrapped]
```
4965 ?        Ds     0:00 /usr/sbin/hald --drop-privileges
```
[/QUOTE]

The process state is "Ds":
D = uninterruptible sleep (usually IO)
s = is a session leader

Does this provide any hints to what the cause may be?

---

### Post by nzgreen on 2004-12-11
[QUOTE=boobytrapped]The process state is "Ds":
D = uninterruptible sleep (usually IO)
s = is a session leader

Does this provide any hints to what the cause may be?[/QUOTE]
Not to me it doesn't.  Can you edit the D-BUS init script (/etc/init.d/dbus-1 IIRC) and comment out the line that starts HAL.  Then you should be able to reboot and start HAL manually.

Just out of interest, is this running on a laptop?

---

### Post by burlap on 2004-12-11
It is not going to help at all, I guess, but it seems to be a common problem. Look at bugs [1727](https://bugzilla.ubuntu.com/show_bug.cgi?id=1727) and [1891](https://bugzilla.ubuntu.com/show_bug.cgi?id=1891). If you think it is the same problem - I suppose the only way is to comment on the bug and provide some information there 	(as I did with my USB key).

---

### Post by brush4me6879 on 2007-05-15
> **burlap said:**
> It is not going to help at all, I guess, but it seems to be a common problem. Look at bugs [1727](https://bugzilla.ubuntu.com/show_bug.cgi?id=1727) and [1891](https://bugzilla.ubuntu.com/show_bug.cgi?id=1891). If you think it is the same problem - I suppose the only way is to comment on the bug and provide some information there 	(as I did with my USB key).


[Skin care Paris Hilton Bankruptcy mapquest Tsunami](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

