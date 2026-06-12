---
title: "Cannot access Services in administration"
date: 2007-03-14
forum: General Help
---

### Post by Blandust on 2007-03-14
I was configuring which apps would run at start up of ubuntu I guess i un-checked the wrong one now at startup I get a pop-up window, reading : "Failed to initialize HAL."
Also I cant access services anymore, it reads " The Configuration could not be loaded, you are not allowed to access system configuration."
How can I fix this? Thanks.

---

### Post by useResa on 2007-03-14
> **Blandust said:**
> Also I cant access services anymore, it reads " The Configuration could not be loaded, you are not allowed to access system configuration."
Have you tried starting Services by issuing the following command in a terminal?
```
sudo services-admin
```
Does it start then?

---

### Post by ComputerGuy56 on 2007-03-14
> **Blandust said:**
>  "Failed to initialize HAL."

I used to get the same error message. When it shows the little Ubuntu thing and what's it's loading, it usually waits at Windows for a long time. I went into Terminal, then typed:
```
sudo iptables -F
```

Yes I know that it's used for IPTables but it worked for me and now it doesn't wait at the Windows thing and doesn't show the HAL thing.

---

### Post by jessika_kaos on 2007-04-13
I'm having the same issue. I disabled some startup services in System>Administration>Services, and now whenever I log in I get a warning that Hal failed to initialize and I am unable to open the the services dialog again. I unchecked the printing and speech synthesis services.

I tried sudo services-admin and get this:> (services-admin:4391): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
4391: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
4391: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:4391): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
4391: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.


---

### Post by Tom Chaudoir on 2007-04-26
I had the same problem. Drove me nuts. The fix is simple and it's here:
[http://ubuntuforums.org/showthread.php?t=289654]("http://ubuntuforums.org/showthread.php?t=289654")

Hope that helps.
Tom

---

