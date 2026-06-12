---
title: "Evolution does not start in Ubuntu 7.10"
date: 2007-12-06
forum: General Help
---

### Post by hrafninn on 2007-12-06
I just upgraded to Ubuntu 7.10.  I was running Evolution mail in Ubuntu 7.04 without any problems.  When I try to start it in 7.10, I get the messages below.  Any ideas?

CalDAV Eplugin starting up ...

** (evolution:13681): WARNING **: Unexpected kerberos error -1765328164

(evolution:13681): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:13681): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:13681): libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault (core dumped)

---

### Post by Damanther on 2007-12-06
I use evolution and did not have an issue after the upgrade. I know that doesn't help you much, but that looks like a fairly critical error. If you can make a backup of your stored messages I would try to remove/reinstall evolution.

---

### Post by hrafninn on 2007-12-07
> **Damanther said:**
> I use evolution and did not have an issue after the upgrade. I know that doesn't help you much, but that looks like a fairly critical error. If you can make a backup of your stored messages I would try to remove/reinstall evolution.

I had already tried that - got the same error message again :(

---

### Post by hrafninn on 2007-12-12
I just installed Ubuntu 7.10 from scratch on a new Dell Precision Laptop.  I tried to use Evolution to connect to a Microsoft Exchange Server at work and after I input the OWA (during the configuration phase in Evolution) Evolution core dumpes with the exact same messages as I got earlier on a different machine (see earlier posting):

(evolution:6575): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:6575): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:6575: libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault (core dumped) 

Has anybody encountered something similar?

---

### Post by timbellomo on 2007-12-12
@hrafninn

Yes, I get a similar error (sans kerberos warning) when I try to configure Exchange.

---

### Post by hrafninn on 2007-12-13
FYI: I switched to Mozilla Thunderbird Mail and use it to connect to Microsoft Exchange.  No problems so far.

---

### Post by hrafninn on 2007-12-15
In Thunderbird, I used IMAP to connect to the Exchange server.

Using Server type = IMAP in Evolution (instead of Server type = Microsoft Exchange) works.
In that case, however, I do not have access to the Exchange calendar, contacts, tasks, etc.

---

### Post by Damanther on 2007-12-26
I'm a little late on this one. But are the folks getting this error sure they have the evolution-exchange package installed??

---

### Post by hrafninn on 2007-12-28
> **Damanther said:**
> I'm a little late on this one. But are the folks getting this error sure they have the evolution-exchange package installed??

Yes.

I just tried setting up the connection a minute ago and after having input the OWA and hit the "Authenticate" button, I finally received the following error message (instead of a core dump):

[COLOR="Red"]The Exchange server is not compatible with Exchange Connector.

The server is running Exchange 5.5. Exchange Connector 
supports Microsoft Exchange 2000 and 2003 only.[/COLOR]

This explains it all!

---

### Post by stabface on 2008-01-14
> **hrafninn said:**
> I just upgraded to Ubuntu 7.10.  I was running Evolution mail in Ubuntu 7.04 without any problems.  When I try to start it in 7.10, I get the messages below.  Any ideas?

CalDAV Eplugin starting up ...

** (evolution:13681): WARNING **: Unexpected kerberos error -1765328164

(evolution:13681): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:13681): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:13681): libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault (core dumped)


i have the exact same problem. i was trying to use evolution to connect to the exchange hosted by intermedia.

after plugin in the info and clicking  next it dies. and  i get the same errors when i run that in terminal

---

