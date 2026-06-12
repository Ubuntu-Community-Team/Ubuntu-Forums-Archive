---
title: "Virtual Box, Running applications on host in seamless mode (without RDP and whatnot)"
date: 2008-02-06
forum: General Help
---

### Post by ikex on 2008-02-06
Im not to sure how helpful this is, however ive used this to integrate WLM and whatnot into my panels so i can just click them and they startup. I know this is easily done with the rdp method but this is just plain seamless mode.

If your on a public network, or running without a firewall THIS IS NOT SECURE. 

First you will need to set the ports up on Virtualbox, so type the following in a terminal (changing guestname to the name of the vm your using of course)

```
VBoxManage setextradata <guestname> "VBoxInternal/Devices/pcnet/0/LUN#0/Config/runapp/HostPort" 3030
VBoxManage setextradata <guestname> "VBoxInternal/Devices/pcnet/0/LUN#0/Config/runapp/GuestPort" 3030
VBoxManage setextradata <guestname> "VBoxInternal/Devices/pcnet/0/LUN#0/Config/runapp/Protocol" TCP

```Next you will need to compile the source attached, and run it from the guest box. (Read through the comments for a bit more information).

Then (if you want) use the perl script I included in the comments on the top of server.cs.

Then its just simply:
```

remotewin <application>

```I know this is pretty dirty, but after a nice sleep i'll clean it up a little and add some sort of authorisation.

Theres probably alot more pratical solutions out there i just figured i'd share this.

:]

[IMG]http://img136.imageshack.us/img136/7829/screenshotdesktopub7.png[/IMG]

---

