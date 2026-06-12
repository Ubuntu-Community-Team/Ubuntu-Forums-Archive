---
title: "iFolder client in Edgy"
date: 2006-11-18
forum: General Help
---

### Post by valorin on 2006-11-18
Has anyone been able to install iFolder Client in Edgy and get it working?
I've done everything I did with Dapper and it refuses to start.

When I try to run it, I get the following errors:

```
valorin@grouch:/opt/novell/ifolder3/bin$ ./ifolder 
[: 7: ==: unexpected operator

Unhandled Exception: System.DllNotFoundException: libsimiasbonjour
  at (wrapper managed-to-native) Simias.mDns.Browser:BrowseMembersInit (Simias.mDns.Browser/MemberBrowseCallback,intptr&)
  at Simias.mDns.Browser.BrowseThread () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
[: 7: ==: unexpected operator
Error: Cannot start the local web services.
Error: The Simias process failed to initialize.
       Use the command line switch --showconsole to view the error.

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Novell.iFolder.iFolderApplication.StartiFolder () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

```

I am trying to run the latest RPM's (Alien'ed) from the Novell site.

---

### Post by temcat on 2006-11-18
> **valorin said:**
> Has anyone been able to install iFolder Client in Edgy and get it working?

Looks like you hit the good old dash vs. bash problem. Ideally, you should replace all #!/bin/sh links in the iFolder client with #!/bin/bash, but I'm afraid there's too many places to look in. I think your safest best is to run

```
sudo dpkg-reconfigure dash

```
and answer "No" when asked on the command line whether to install dash.

---

### Post by valorin on 2006-11-18
Thanks :) Unfortunantly, it didn't work :(

Ok, I just tried that and its still giving me an error. This one is slightly different, but I remember seeing this one before.

```
valorin@grouch:/opt/novell/ifolder3/bin$ ./ifolder --showconsole

Unhandled Exception: System.DllNotFoundException: libsimiasbonjour
  at (wrapper managed-to-native) Simias.mDns.Browser:BrowseMembersInit (Simias.mDns.Browser/MemberBrowseCallback,intptr&)
  at Simias.mDns.Browser.BrowseThread () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

Unhandled Exception: System.ApplicationException: The local web service is not responding.
  at Simias.Client.LocalService.Start (System.Web.Services.Protocols.HttpWebClientProtocol webClient, System.Uri webServiceUri, System.String simiasDataPath) [0x00000] 
  at Novell.iFolder.iFolderApplication.StartiFolder () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
```

---

### Post by temcat on 2006-11-19
> **valorin said:**
> Thanks :) Unfortunantly, it didn't work :(

Ok, I just tried that and its still giving me an error. This one is slightly different, but I remember seeing this one before.


Can't really help you with these, but dash seems to have been a part of the problem anyway (the "unexpected operator" error that is gone now).

---

### Post by valorin on 2007-01-01
I figure I will try again...

> Unhandled Exception: System.UriFormatException: Invalid URI: The format of the URI could not be determined.
  at System.Uri..ctor (System.String uriString, Boolean dontEscape) [0x00000] 
  at System.Uri..ctor (System.String uriString) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Uri:.ctor (string)
  at Simias.Client.Manager.get_WebServiceUri () [0x00000] 
  at Novell.iFolder.iFolderApplication.StartiFolder () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()


That is the error message I receive when trying to run iFolder in Edgy. It's almost enough to make me go back to using Dapper :(

---

### Post by valorin on 2007-01-01
I've done some fiddling and I believe the problem is the fact that
libapache-mod-mono is version 1.1.13 while EVERY OTHER mono&apache package is version 1.1.17... Therefore I cannot install libapache-mod-mono, and thus I believe iFolder will not work.

Is there a way to force it to install, or get the 1.1.17 version? It's just stupid being there at all if it can't be installed.

---

### Post by flickerfly on 2007-02-22
I tossed a bug into launchpad hoping for iFolder to get into the repositories:

[https://bugs.launchpad.net/ubuntu/+bug/87122](https://bugs.launchpad.net/ubuntu/+bug/87122)

---

