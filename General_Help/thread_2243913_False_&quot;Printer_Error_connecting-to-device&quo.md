---
title: "False &quot;Printer Error: connecting-to-device&quot; message: how to suppress?"
date: 2014-09-12
forum: General Help
---

### Post by weatherman2 on 2014-09-12
I'm an experienced Ubuntu user, using Ubuntu 12.04.2 with Gnome Fallback.  I'm having an annoying, minor, but nagging printer problem I can't seem to fix.  (Same problem on two different Ubuntu installations.)

I am using a router with a USB port as a USB print server.  Printing works fine - except that whenever I print I get the notification message "Printer Error:" with the printer name and "connecting-to-device."  This message soon goes away and I get the message that printing has completed successfully - and indeed, it has.

Yes, I could simply ignore the error - but I'm using this setup for a nearly computer-illiterate person who freaks out about messages like this.  I can tell her once to ignore the error and she says, "OK!" and then the next time I talk to her, she says, "I tried to print the other day but it says there's an error..."    Obviously it would make life easier to make the error go away instead of having to remind her every time and have her soon forget.

The message isn't related to the printer model.  I have tried both an HP and a Canon printer.  The Canon printer (which I'm using to test) has its own WiFi and when I print to it that way, I don't get this error message.  Only when printing via the print server, which uses Device URI "socket://192.168.1.1:9100" do I get this message.  Same problem with the HP, which is using a different driver.

I've already done some googling on this - a few people mention the same problem but no good solutions are suggested.

I'm thinking I might simply find a way to suppress the message instead of trying to "fix the problem," but I don't know where to start to do that.  Any suggestions?

---

### Post by sandipahire007 on 2014-11-14
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Test_Sandip (default)>,
 'cups_instance': None,
 'cups_queue': 'Test_Sandip',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/lp0',
                       'printer-info': u'Test_Sandip',
                       'printer-is-shared': True,
                       'printer-location': u'Sandip',
                       'printer-make-and-model': u'WeP LQ DSI 5235',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8531972,
                       'printer-uri-supported': u'ipp://localhost:631

---

