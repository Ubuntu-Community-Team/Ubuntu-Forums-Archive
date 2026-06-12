---
title: "unable to open ssh:// links with firefox"
date: 2020-03-18
forum: General Help
---

### Post by phantombrew on 2020-03-18
Hello all, sorry if this has already been solved but I've spent a while trying to find anything related to this to no avail.
Basically, my company uses ssh:// links to access remote devices so that we can manage them remotely. On Windows, I can use KiTTY to access these links easily once I run their registry file. However, on linux, I can't seem to find any way to open these links in PuTTY or similar. I've tried almost all suggestions that I've found online, from creating bash scripts that specify opening terminals to simply switching network.protocol-handler.expose.ssh to "false." None of these have worked at all, with the closest I've come being from installing the "IP Protocols" extension and specifying /usr/bin/putty, which opens putty up but spits out an error reading "unable to open connection to ssh://(username@ip address)/: name or service not known."

Is there something simple that I'm missing? Sorry if this is in the wrong spot.

---

### Post by TheFu on 2020-03-18
This is the first time I&#8217;ve ever heard of ssh links ever.  sftp:// works in most Linux file managers to make sftp connections.

Google found : [https://github.com/mimecuvalo/firessh](https://github.com/mimecuvalo/firessh)
> After 13 years and 25 million downloads later, Firefox has officially removed FireFTP and FireSSH support from the browser. Thus, I've ended support / development of the addons. I recommend switching to Waterfox to continue using the addons.

Seems counter-security to me.  Either you have an ssh login on a server and know it or you don't.  if the server needs to change, move where the DNS points.

Perhaps i need to shave my neckbeard?

---

