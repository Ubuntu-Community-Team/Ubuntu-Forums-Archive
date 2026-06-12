---
title: "[SOLVED] Ignore certain updates"
date: 2008-05-14
forum: General Help
---

### Post by MDSmith2 on 2008-05-14
Hello, I have upgraded to Hardy and fly with FlightGear a lot but running a AMD Athlon XP I couldn't upgrade to FlightGear 1.0 so i installed 0.9.10 but now update manager keeps bugging me about the flightgear update.
Is there any way to ignore just that update without ignore new updates?

---

### Post by drs305 on 2008-05-14
> **MDSmith2 said:**
> Hello, I have upgraded to Hardy and fly with FlightGear a lot but running a AMD Athlon XP I couldn't upgrade to FlightGear 1.0 so i installed 0.9.10 but now update manager keeps bugging me about the flightgear update.
Is there any way to ignore just that update without ignore new updates?

If your version is listed in synaptic (in mine flightgear 1.0 is listed but I don't have it installed), click on the packages tab and lock the version to prevent upgrades. I think that will also eliminate the nags - if it doesn't please report back.

---

### Post by MDSmith2 on 2008-05-14
Thanks that did the trick!

---

### Post by drs305 on 2008-05-15
MDSmith,

I occurred to me that there is one more step that may be necessary for you to preserve the earlier version of flightgear.

If you tinker much with the command line, the update / upgrade commands in conjunction with sudo aptitude or sudo apt-get will NOT respect the synaptic version lock (i.e. it will update to the latest version). 

If you are apt to ever run a command line update, you can prevent this from happening by running the following command. The = sign attached to the end of the program name does the same thing as 'lock' does in synaptic. Use the flightgear name as it is listed in synaptic. Once you have run the following command, you can run future upgrade commands as you normally would.
```
sudo aptitude install program_name=
```

---

### Post by MDSmith2 on 2008-05-15
> **drs305 said:**
> MDSmith,

I occurred to me that there is one more step that may be necessary for you to preserve the earlier version of flightgear.

If you tinker much with the command line, the update / upgrade commands in conjunction with sudo aptitude or sudo apt-get will NOT respect the synaptic version lock (i.e. it will update to the latest version). 

If you are apt to ever run a command line update, you can prevent this from happening by running the following command. The = sign attached to the end of the program name does the same thing as 'lock' does in synaptic. Use the flightgear name as it is listed in synaptic. Once you have run the following command, you can run future upgrade commands as you normally would.
```
sudo aptitude install program_name=
```
Thanks will do when done compiling nautilus!

---

