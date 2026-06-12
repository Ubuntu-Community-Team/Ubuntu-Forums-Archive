---
title: "CUPS/pycups: not receiving all subscribed events"
date: 2018-09-16
forum: General Help
---

### Post by Argonisius on 2018-09-16
[COLOR=#242729][FONT=Arial]Hi, I'm having trouble with receiving subscribed events from CUPS. It might be a programming question, but I think it's rather an issue of configuration. 

I'm using the [pycups]("https://github.com/AIWIP/pycups") python library to communicate with CUPS. So far I have done following:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]1) Subscribed for all CUPS events (I have a simple http server listening on [http://localhost:9988]("http://localhost:9988/") for incoming events and CUPS is using [cups-http-notifier]("https://github.com/AIWIP/cups-http-notifier") to send those events):[/FONT][/COLOR]
```
connection = cups.Connection()
connection.createSubscription(
    uri="http://localhost:631/printers",
    recipient_uri="http://localhost:9988",
    events=['all'],
    lease_duration=0
)
```
[COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]2) Printed file:[/FONT][/COLOR]
```
connection = cups.Connection()
connection.printFile(printer, file_path, job_id, options)
```

With this setup I'm receiving all kinds of events regarding printers and the job being printed - this works well, as expected.


The issue arises when canceling the job programatically:
```
connection = cups.Connection()
connection.cancelJob(job_id,False)
```
[COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]The job gets cancelled (checked in CUPS web interface), **but I don't receive the event**. [/FONT][/COLOR][COLOR=#242729][FONT=Arial]When I cancel the job **via the web interface**, **the event is received** as any other. The other strange thing is that I get system notification about the job being cancelled - so at least dbus notification is sent...
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm thinking that there could be an issue with users - subscription owner vs job owner vs cancellation owner, but I'm doing all those things from one python script (under one user) and I have really no idea what to configure.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any ideas what could be wrong? Thanks in advance![/FONT][/COLOR]

---

