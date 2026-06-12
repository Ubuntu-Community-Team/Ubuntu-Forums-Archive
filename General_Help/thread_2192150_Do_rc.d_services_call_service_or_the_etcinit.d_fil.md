---
title: "Do rc.d services call service or the /etc/init.d files directly?"
date: 2013-12-06
forum: General Help
---

### Post by helloworld1215 on 2013-12-06
It would appear from certain general documentation that the /etc/init.d scripts are called directly. Are there configuration options or instances where, or perhaps they are in fact called with service? Presumably this is handled by upstart. 

This is relevant in the context of the environment that that the scripts receive.

---

### Post by ian-weisser on 2013-12-06
There are three ways to read your question:

1) Can an Upstart or Init file use the **service** command?

No. The **service** command does not magically know how to start/stop a job. It needs instructions from the /etc/init/ or /etc/init.d file.

Those instructions should not include the **service** command because that would make it recursive ("Start the car. You do that by starting the car") 


2) Can my non-Upstart script use the **service** command to start/stop a different service?

Yes, but.... Your scripts and processes can use the **service** command, however, it's considered hacky because it should be run as sudo or root. Generally, the **service** command is intended for human use. Scripts and processes should be emitting or listening for Upstart events, or querying dbus.


3) Can my Upstart job use the **service** command to control a different service?

It probably could...but it's very unwise to do so. Your job should be emitting or listening for the appropriate Upstart events to start/stop a different Upstart-supervised service. That use case is *exactly* what Upstart events are for.

---

### Post by helloworld1215 on 2013-12-06
Thanks. I dunno why I posted this. Services are generally symlinked into the rc dirs and are called directly. 

I guess I was under the sleep deprived impression that perhaps in some instance init/upstart takes as input a name and calls it with service, which would generally not result in recursion. Thanks

---

