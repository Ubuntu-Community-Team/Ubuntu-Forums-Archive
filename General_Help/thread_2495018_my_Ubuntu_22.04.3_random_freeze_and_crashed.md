---
title: "my Ubuntu 22.04.3 random freeze and crashed"
date: 2024-02-04
forum: General Help
---

### Post by mh737 on 2024-02-04
Hello
  I ran into a problem: ubuntu 22.04.3, at some point it started to freeze and crash.
 my hardware is not old, and there is always enough operative time.  turned off all bluetooth adapters physically.  after reinstalling the system cleanly, I want to start mozila forefox and the system also starts to hang and shut down.
 my config:
 i5 11400f
 32gb ram
 1tb ssd m2
 thought that the problem was in xmp, but it turned out that it was not.
 how can this be fixed?
 reinstalling ubuntu from scratch didn't help.
 even on another SATA-type SSD it did not give results.
my logs file:
&#1089;&#1110;&#1095; 28 16:24:18 mh737-System-Product-Name dbus-daemon[907]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
&#1089;&#1110;&#1095; 28 16:24:18 mh737-System-Product-Name pulseaudio[10734]: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
&#1089;&#1110;&#1095; 28 16:24:24 mh737-System-Product-Name systemd[1]: fprintd.service: Deactivated successfully.

---

### Post by MAFoElffen on 2024-02-05
You did not mention what brand and model of computer.

You did not mention which GPU you are using. The F series iCores have no integrated graphics.

---

