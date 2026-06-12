---
title: "i broke X with iptables (I think)"
date: 2005-10-27
forum: General Help
---

### Post by Samuel on 2005-10-27
i was reading the forums and saw suggestions to run both firestarter and gaurdDog firewalls together, so i installed firestarter, all seemed ok.

 then i installed gaurdDog, which brought alot of kde libs with it, i went through the gaurdDog setup checking the boxes of programs i use and blocking net access to programs i dont use.
  X was one of the ones blocked, i coudlnt think of a reason for it to acess the network and it said it was high risk, so i blocked it..
  then i realised that synaptic couldnt connect to the repos so i thought i obviously dont understand this firewall well enough and uninstalled it along with the libs it brought along.

  all was fine until i rebooted and i can no longer log into GDE.
Im at work now so i cant post my xsessions-error log for a couple of hours but im wondering if booting from the live disk and copying the iptables file over from there to replace mine would work, or if its even related at all...

any suggestions or thoughts on how to handle this would be appreciated

---

### Post by Samuel on 2005-10-27
here is my .xsession-errors
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sam"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:10171): WARNING **: Unable to read ICE authority file: /home/sam/.ICEauthority
```
anyone any ideas??

---

### Post by Samuel on 2005-10-27
wow i was so far wrong its not even funny, something had changed the ownership of my ~/.ICEauthority file 
```
chown sam /home/sam/.ICEauthority
``` 
fixed it, so glad, i was one try away from a reinstall.
another problem solved another thing learned :)
what a thing to happen on the day i give up smoking haha

---

