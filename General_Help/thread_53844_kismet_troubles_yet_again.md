---
title: "kismet troubles yet again"
date: 2005-08-02
forum: General Help
---

### Post by somuchfortheafter on 2005-08-02
ok im using the latest version of kismet out of svn. all is compile and well for the moment however whenever i try to run kismet as sudo kismet i recieve this error:

```

thanatosys@darkstar:~/software/kismet-devel$ sudo iwconfig eth0 mode monitor && sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to thanatosys (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (ATHEROS): Enabling monitor mode for ipw2200 source interface eth0 channel 6...
Source 0 (ATHEROS): Opening ipw2200 source interface eth0...
Spawned channelc control process 27706
Dropped privs to thanatosys (1000) gid 1000
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
FATAL: Could not open SSID track file '/var/lib/kismet/ssid_map' for writing: Permission denied
Sending termination request to channel control child 27706...
Waiting for channel control child 27706 to exit...
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Kismet exiting.
thanatosys@darkstar:~/software/kismet-devel$

```
also im using the intel 2200b/g card with the latest drivers for it so all should be well.. any help?

---

### Post by somuchfortheafter on 2005-08-02
fixed it. all you have to do is as root edit file permissions for the folders /var/lib/kismet and /var/log/kimset for all users to read and write to and your done.

---

