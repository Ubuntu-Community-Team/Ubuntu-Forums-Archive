---
title: "CUPS 1.7.2 remote printing problem"
date: 2016-03-17
forum: General Help
---

### Post by auburn on 2016-03-17
I've recently upgraded half my computer lab's macs from OSX 10.6 to 10.9 and they can no longer print to the Ubuntu 14.04 CUPS server.
The print jobs arrive with 0 bytes on the Ubuntu CUPS server.
They CAN print to the printer (lexmark ms810) directly.

On the macs, the printer was installed like this ipp://10.201.195.50:631/printers/ComputerLab with a raw driver.

On the server the printer was installed like this:
socket://10.201.195.24
with this driver: Lexmark Optra E - CUPS+Gutenprint v5.2.10-pre2

Both of them, ubuntu and OSX, have cups version 1.7.2

I'm tearing my hair out because I've tried raw/ms810 drivers on both and neither, on one or the other, I've tried replacing the mac client's cupsd.conf with the osx10.6's cupsd.conf.
Meanwhile the OSX10.6 macs continue to print just fine.
The cups version on osx10.6 is 1.4.7

I ****think**** the clue is the 0 bytes of the print job when it gets to the cups server. It's NOT zero bytes on the mac's cups.

---

### Post by dragonfly41 on 2016-03-17
I don't have Mac computers .. but have you looked through [http://localhost:631](http://localhost:631) for any clues ..

e.g.  [http://localhost:631/help/ref-error_log.html?TOPIC=References&QUERY=](http://localhost:631/help/ref-error_log.html?TOPIC=References&QUERY=)

---

### Post by auburn on 2016-04-08
Thank you for replying dragonfly.

I can't seem to make much of the logs. Im getting a whole lot of this on the client mac (the one sending the print job:
```

D [08/Apr/2016:17:03:02 -0400] Discarding unused job-progress event...
D [08/Apr/2016:17:03:10 -0400] [Job 252] update_reasons(attr=1(none), s="(null)")
D [08/Apr/2016:17:03:10 -0400] [Job 252] Get-Printer-Attributes: successful-ok (successful-ok)
D [08/Apr/2016:17:03:10 -0400] [Job 252] (monitor) Get-Job-Attributes: successful-ok (successful-ok)
D [08/Apr/2016:17:03:10 -0400] [Job 252] (monitor) job-state=pending-held
D [08/Apr/2016:17:03:10 -0400] [Job 252] update_reasons(attr=1(none), s="(null)")
D [08/Apr/2016:17:03:10 -0400] [Job 252] Get-Printer-Attributes: successful-ok (successful-ok)
D [08/Apr/2016:17:03:10 -0400] [Job 252] Get-Job-Attributes: successful-ok (successful-ok)
D [08/Apr/2016:17:03:10 -0400] [Job 252] update_reasons(attr=0(), s="+cups-remote-pending-held")
D [08/Apr/2016:17:03:10 -0400] [Job 252] PAGE: total 0


```

And on the server it's really hard to find any errors or clues. Here are some snippets:


```

D [08/Apr/2016:17:28:20 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"

d [08/Apr/2016:17:28:20 -0400] [Client 18] cupsdReadClient error=0, used=0, state=HTTP_STATE_WAITING, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=0, request=(nil)(), file=-1
D [08/Apr/2016:17:28:20 -0400] [Client 18] POST /printers/ms810genericPS HTTP/1.1
D [08/Apr/2016:17:28:20 -0400] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
d [08/Apr/2016:17:28:20 -0400] cupsdFindBest: uri = "/printers/ms810genericPS"...
d [08/Apr/2016:17:28:20 -0400] cupsdFindBest: Location /admin/conf Limit 7f

d [08/Apr/2016:17:28:20 -0400] [Client 18] con->uri="/printers/ms810genericPS", con->best=0x7fc5302ae140(/)
d [08/Apr/2016:17:28:20 -0400] [Client 18] Authorization=""
D [08/Apr/2016:17:28:20 -0400] [Client 18] No authentication data provided.
d [08/Apr/2016:17:28:20 -0400] cupsdIsAuthorized: con->uri="/printers/ms810genericPS", con->best=0x7fc5302ae140(/)
d [08/Apr/2016:17:28:20 -0400] cupsdIsAuthorized: level=CUPSD_AUTH_ANON, type=None, satisfy=CUPSD_AUTH_SATISFY_ALL, num_names=0
d [08/Apr/2016:17:28:20 -0400] cupsdIsAuthorized: auth=CUPSD_AUTH_ALLOW...
D [08/Apr/2016:17:28:20 -0400] [Client 18] 2.0 Get-Printer-Attributes 27
d [08/Apr/2016:17:28:20 -0400] cupsdProcessIPPRequest(0x7fc53046f1c0[18]): operation_id = 000b
D [08/Apr/2016:17:28:20 -0400] Get-Printer-Attributes http://10.201.195.50:631/printers/ms810genericPS
d [08/Apr/2016:17:28:20 -0400] get_printer_attrs(0x7fc53046f1c0[18], http://10.201.195.50:631/printers/ms810genericPS)
d [08/Apr/2016:17:28:20 -0400] cupsdFindPolicyOp(p=0x7fc5302aef60, op=b(Get-Printer-Attributes))
d [08/Apr/2016:17:28:20 -0400] cupsdFindPolicyOp: Found wildcard match...
d [08/Apr/2016:17:28:20 -0400] cupsdIsAuthorized: con->uri="/printers/ms810genericPS", con->best=0x7fc5302b0cf0((null))

d [08/Apr/2016:17:28:20 -0400] cupsdIsAuthorized: auth=CUPSD_AUTH_ALLOW...
d [08/Apr/2016:17:28:20 -0400] add_printer_state_reasons(0x7fc53046f1c0[18], 0x7fc5302f1430[ms810genericPS])

D [08/Apr/2016:17:28:20 -0400] [Client 18] Returning IPP successful-ok for Get-Printer-Attributes (http://10.201.195.50:631/printers/ms810genericPS) from 10.201.195.112

D [08/Apr/2016:17:28:20 -0400] [Client 18] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0

D [08/Apr/2016:17:28:20 -0400] [Client 18] Waiting for request.
request=(nil)(), file=-1
D [08/Apr/2016:17:28:20 -0400] [Client 18] HTTP_STATE_WAITING Closing on EOF
D [08/Apr/2016:17:28:20 -0400] [Client 18] Closing connection.
D [08/Apr/2016:17:28:20 -0400] SSL shutdown successful!

```

Any help is appreciated...

---

### Post by auburn on 2016-04-08
And the jobs page on web interface shows this:
[block]
ms810genericPS-141370  	testprint  	admin  	0k  	Unknown  	held since
Fri 08 Apr 2016 05:41:23 PM EDT 
[/block]

---

### Post by auburn on 2016-04-14
Here's my latest clue from the cups error log:
 Aborting job because it has no files.

---

### Post by auburn on 2016-04-14
Whew! I found a solution. Working on the assumption that since I upgraded from 12.04 to 14.04, and maybe even 10.04 before that...perhaps my cupsd.conf file had bad or deprecated lines in it. So I re-created my cupsd.conf file like this: 
```

sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf-bkup && sudo cp /usr/share/cups/cupsd.conf.default /etc/cups/cupsd.conf

```

I'm adding the printer on the macs with raw drivers like this:
```

pname="ComputerLab"; lpadmin -p $pname -m raw -E -v http://10.201.195.50:631/classes/ComputerLab -D "ComputerLab" ;  cupsenable "$pname"; cupsaccept "$pname"; lpoptions -d $pname; echo "**** Installed Printers: ****" ; lpstat -p

```

And on the server I've added the printer with the gutenprint Lexmark Optra E driver....but not because it's necessarily the best...I just haven't bothered to upgrade it yet.

---

