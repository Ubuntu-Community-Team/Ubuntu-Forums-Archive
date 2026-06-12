---
title: "Services (services-admin)"
date: 2006-10-31
forum: General Help
---

### Post by lordgibbness on 2006-10-31
Hi,

I was looking into turning off a few services that I do not use (mail fetcher, bluetooth, etc.) but I accidentally stopped a required service (sub-system, I think, down near the bottom) and now I can't open the services menu.

Is there any way that I can get back into the services menu so that I can re-enable this service?

Also, where are the list of services and their current states (on/off) held?

Many thanks,
Rob.

---

### Post by lordgibbness on 2006-10-31
Okay, so maybe this week wasn't a great time to start playing around with system settings...

(with everyone upgrading and posting lots of upgrade issues on the forums - I think my post got lost down the bottom in a couple of mins!)

But, if anyone does have the patience to look at this I would much appreciated.  As stated above I accidentally turned off the sub-system... (I can't remember exactly) and can no longer access the services menu.

I receive the following error every time I log in:-

```
Internal error
failed to initialize HAL!
```

And if I try to run the services-admin command I get the following errors:-

```
The configuration could not be loaded
You are not allowed to access the system configuration.
```

```
(services-admin:4675): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
4675: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
4675: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:4675): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
4675: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.
```


Help would be much appreciated - I don't want to have to format/reinstall if at all possible!

Thanks.

---

### Post by lordgibbness on 2006-10-31
Looks like I've solved it!  Thought I'd add the solution in case anyone else makes the same mistake!

1) Run the following command at the terminal:-

```
sudo /etc/init.d/dbus start
```

2) Then run services-admin and enable the System Communication Bus (dbus).

Found the solution [here]("http://ubuntuforums.org/showthread.php?p=1643993")

---

### Post by Icarosaurus on 2006-11-18
Thank you...
you saved my day! :mrgreen:

---

### Post by zorkerz on 2007-03-26
Im about to try this. Sorry no one was able to help you but im glad you figured it out yourself and you deserve a medal for posting your solution here!

---

### Post by th0rn on 2007-04-20
> **lordgibbness said:**
> Looks like I've solved it!  Thought I'd add the solution in case anyone else makes the same mistake!

1) Run the following command at the terminal:-

```
sudo /etc/init.d/dbus start
```

2) Then run services-admin and enable the System Communication Bus (dbus).
...
Thank you, thank you, thank you!

I also cut off the limb I was sitting on, by disabling the dbus service while trying to t-shoot a simple boot failure problem (related to proper PnP recognition).

Was also getting the HAL failure error after login too. Must've spent two hours reading forums and reinstalling every *dbus* package, confirming admin priv's for my user name, checking menu items in alacarte, etc., all without success.

This single term' command did it!  Yes!  I was also starting to hate Ubuntu for not warning me that I was about to create a situation that might be very hard to rectify. This is supposed to be the ultimate "user friendly" Nix distro, darn it.

---

### Post by Tom Chaudoir on 2007-04-26
Thank you. I was in the same boat. I think this should be a known issue. When I turned the thing off I figured I'd just turn it back on again if things got flaky. They did and I couldn't.

Before I clicked that one, I tried another which gave me a very stern warning and asked if I was sure. That made me even more confident when turning off Dbus. (Whatever that is.)

It makes me wonder how many others are lost in the woods.

Thanks again,
Tom

---

### Post by jeandersen on 2007-05-31
What happens when you try to run services-admin and get the following error...?

```
(services-admin:6185): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(services-admin:6185): Liboobs-WARNING **: There was an unknown error communicating with the backends: Process /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl exited with status 127

```

...

I am still stuck in the woods...  heh...


...

---

### Post by lledurt on 2007-06-12
Dude,
You saved me.  Thanks
P.J.

---

### Post by highcliff on 2007-06-23
Thanks....Thanks....I did it with your solution and save my ubuntu

---

### Post by meindian523 on 2007-07-11
Thanks a lot lordgibb,I did the same thing as you and got everything was the same.Even root login couldn't access the services!Thanks,man,I was resigned to a reinstall and had even backed up my packages using APTonCD!

---

### Post by pichvajz on 2007-08-20
Thank You - You are save me :lolflag:

---

### Post by morpheus01 on 2007-08-22
Thanks loads for this...

Should users have the option to disable this service I wonder? I'm introducing a lot of non-techies to Ubuntu and I don't think they're fond of the command line or trawling through  forums for solutions.

ps. I set up a auto start up for KTorrent, it seems to be gone from the services menu though. Any ideas why?

---

### Post by morpheus01 on 2007-08-22
Sorry ignore the above post. I had it set up in system-preferences-sessions, can't remember how i did it.

---

### Post by kimguru on 2007-08-30
> **lordgibbness said:**
> Looks like I've solved it!  Thought I'd add the solution in case anyone else makes the same mistake!

1) Run the following command at the terminal:-

```
sudo /etc/init.d/dbus start
```

2) Then run services-admin and enable the System Communication Bus (dbus).

Found the solution [here]("http://ubuntuforums.org/showthread.php?p=1643993")
thank you very much for help.you saved my day.you angel

---

### Post by alesh on 2007-11-02
> **lordgibbness said:**
> Looks like I've solved it!  Thought I'd add the solution in case anyone else makes the same mistake!

1) Run the following command at the terminal:-

```
sudo /etc/init.d/dbus start
```

2) Then run services-admin and enable the System Communication Bus (dbus).

Found the solution [here]("http://ubuntuforums.org/showthread.php?p=1643993")

I seem to be in the same boat as the rest of you, I disabled dbus in the Services panel - oops - I did the same thing as listed here to fix it, and it seems to work, but when I restart the computer I once again get the failed to start HAL message. In addition to that, even after starting hal manually (which works just fine) I cannot get a network connection, the network management app just doesn't seem to be behaving.

Disabling dbus seems to have thrown HAL for a loop. And enabling dbus again didn't fix it.

---

### Post by alesh on 2007-11-02
This seemed to solve my problem.

```
sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus
```

Found it here:
[http://ubuntuforums.org/showthread.php?t=588950](http://ubuntuforums.org/showthread.php?t=588950)

---

### Post by spiderman101 on 2007-12-30
Thank you so much  **lordgibbness**

I have the same problem like you, glad i'm not alone :)

and thank you **alesh** too. the code

sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus


help me out from   that HAL error   :lolflag:

---

### Post by ayharano on 2008-01-14
I didn't try yet, but if this solves the dbus/HAL initialization problem, I'll thank you all in advance!

---

### Post by saurabh kakkar on 2008-01-31
> **lordgibbness said:**
> Looks like I've solved it!  Thought I'd add the solution in case anyone else makes the same mistake!

1) Run the following command at the terminal:-

```
sudo /etc/init.d/dbus start
```

2) Then run services-admin and enable the System Communication Bus (dbus).

Found the solution [here]("http://ubuntuforums.org/showthread.php?p=1643993")

Thanks buddy u made my day :)

---

### Post by MrJokester on 2008-03-06
> **lordgibbness said:**
> Okay, so maybe this week wasn't a great time to start playing around with system settings...

(with everyone upgrading and posting lots of upgrade issues on the forums - I think my post got lost down the bottom in a couple of mins!)

But, if anyone does have the patience to look at this I would much appreciated.  As stated above I accidentally turned off the sub-system... (I can't remember exactly) and can no longer access the services menu.

I receive the following error every time I log in:-

```
Internal error
failed to initialize HAL!
```

And if I try to run the services-admin command I get the following errors:-

```
The configuration could not be loaded
You are not allowed to access the system configuration.
```

```
(services-admin:4675): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
4675: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
4675: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:4675): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
4675: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.
```


Help would be much appreciated - I don't want to have to format/reinstall if at all possible!

Thanks.

just reinstal hal and it must work like it usual
use this comand
```
sudo apt-get --reinstall install hal
```
and restart your mashin whit CTRL+ALT+BACKSPACE
after do this
start nautilus as a root
go to /etc/ look for the folder rc2.d rename s12hal to s13hal, or S50dbus to S12dbus.
then
```
sudo gedit /etc/init.d/rc
```
and change this line 
"CONCURRENCY=shell"
to "CONCURRENCY=none"
save it and thats it

---

### Post by Nchalada on 2008-06-20
> **lordgibbness said:**
> Looks like I've solved it!  Thought I'd add the solution in case anyone else makes the same mistake!

1) Run the following command at the terminal:-

```
sudo /etc/init.d/dbus start
```

2) Then run services-admin and enable the System Communication Bus (dbus).

Found the solution [here]("http://ubuntuforums.org/showthread.php?p=1643993")
Thanks Lordgibbness! worked for me :D

---

