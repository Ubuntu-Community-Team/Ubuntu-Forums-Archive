---
title: "FreeNX does not work for some users"
date: 2005-08-17
forum: General Help
---

### Post by Sushi on 2005-08-17
I'm having a strange problem with FreeNX. I had set it up before and it worked beautifully, even on my corporate XP_machine at work. But when I now try to connect to my machine, it doesn't work. Here's what happens:

I type in the username/passowrd in to the NX-client on the XP_machine. The default desktop I have selected is KDE. It authenticates like it should, and it then displays the NoMachine-window, where the remote session should run. It stay there for few seconds, and then it simply disappears. Nothing happens after that. If I switch the session to Gnome, it terminates with an error-message "Session Ubuntu Failed". The log looks like this:

```
NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '2808'.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Remote proxy doesn't support fake authentication.
Info: Forwarding the real X authorization cookie.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using adsl link parameters 8192/8/1/5.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
```

As you can see, it doesn't display any error. Now, the funny thing is that if I try to log in as different user, it works like it should :?. 

I can SSH in to the machine with my username, but if I try to create a NX-session with that same username, it fails. I have tried removing the .nx-directory from my home, letting NS to re-create it, but it doesn't help.

---

### Post by DancingSun on 2005-09-01
There should be an error log somewhere in the .nx directory.

I have the exact symptoms that you have with the KDE session, although I was trying to connect to a GNOME session.  My GNOME session doesn't give me any error messages.

This is how my error log looks like:
```
Loop: WARNING! Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.

```

I have no idea what this means.

---

### Post by btdown on 2005-09-02
Hrm...Here's my details...

It looks like we've all downloaded the new NX client, (1.5) while FreeNX is still at 1.4..Wonder if it makes a difference. Anybody have the old Windows 1.4 NX client?

Thanks
BT

Here my details:

 >  
Info: Proxy running in client mode with pid '884'.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Remote proxy doesn't support fake authentication.
Info: Forwarding the real X authorization cookie.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using adsl link parameters 8192/8/1/5.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.


---

### Post by crajm on 2005-09-10
Yes... had this problem and researched for several months... finally found a post buried 10 pages deep with this line in it.

"I think in my case it was caused by a locking problem with my .Xauthority file. On the machine you are connecting to, check for files called ".Xauthority-l" and ".Xauthority-c" in your home dir. Delete them if they exist."

It did the job for me. I am now happily using NXclient on my XP box to connect to my Ubuntu machine.  Hope this helps. 

Cheers. \\:D/

---

### Post by DancingSun on 2005-09-10
[QUOTE=crajm]Yes... had this problem and researched for several months... finally found a post buried 10 pages deep with this line in it.

"I think in my case it was caused by a locking problem with my .Xauthority file. On the machine you are connecting to, check for files called ".Xauthority-l" and ".Xauthority-c" in your home dir. Delete them if they exist."

It did the job for me. I am now happily using NXclient on my XP box to connect to my Ubuntu machine.  Hope this helps. 

Cheers. \\:D/[/QUOTE]
OH SHIT! Thanks crajm!  I'll try this out!

Alas, those files don't exist in my computer at all...maybe my problem is a bit different.:(

---

### Post by timw on 2005-09-13
I had exactly the same problem as above with the "End of session requested by remote proxy"

Tried removing those three ".Xauthority*" files and it now works like a treat!

Thanks crajm

---

