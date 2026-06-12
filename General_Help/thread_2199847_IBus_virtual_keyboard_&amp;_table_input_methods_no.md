---
title: "IBus virtual keyboard &amp; table input methods not working [13.10]"
date: 2014-01-16
forum: General Help
---

### Post by nithinmkurien on 2014-01-16
Hi, ibus-keyboard is not working properly in my Ubuntu installation. The keyboard is visible but pressing the keys do not output characters in the window. Also I cannot switch the input method to the IPA-X-SAMPA and Compose table methods. When I do it over the command-line as:

ibus engine ipa-x-sampa
or
ibus engine compose

the output is:

(process:10026): IBUS-WARNING **: ibus_bus_call_sync: org.freedesktop.IBus.SetGlobalEngine: GDBus.Error: org.freedesktop.DBus.Error.Failed: Set global engine failed.
Set global engine failed.

Super+Space also does not work with these methods. Has anyone encountered the same problem?

OS: Ubuntu 13.10 64-bit
Affected Packages: ibus-xkbc, ibus-table-ipa-x-sampa, ibus-table-compose, ibus-table

---

