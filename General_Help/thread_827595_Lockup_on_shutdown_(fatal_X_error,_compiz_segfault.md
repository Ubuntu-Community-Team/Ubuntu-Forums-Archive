---
title: "Lockup on shutdown (fatal X error, compiz segfault)"
date: 2008-06-12
forum: General Help
---

### Post by camason on 2008-06-12
Hi Guys,

I have a problem when logging out / restarting X via ctrl+alt+backspace. The system will instantly lock up, the PC speaker will beep 20-odd times, and I need to hard reboot.

Here's some extracts from my logs at the time of freezing (03:48 am)

syslog:
```

Jun 13 03:48:47 camason-ubuntu-desktop gdm[7042]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun 13 03:48:48 camason-ubuntu-desktop kernel: [ 8490.201291] compiz.real[7498]: segfault at 000002c0 eip 08055a6d esp bfe66b20 error 4
Jun 13 03:48:48 camason-ubuntu-desktop kernel: [ 8490.209680] compiz.real[7389]: segfault at 04ed000c eip 08055a6d esp bff76430 error 4

```

messages:
```

Jun 13 03:48:48 camason-ubuntu-desktop kernel: [ 8490.201291] compiz.real[7498]: segfault at 000002c0 eip 08055a6d esp bfe66b20 error 4
Jun 13 03:48:48 camason-ubuntu-desktop kernel: [ 8490.209680] compiz.real[7389]: segfault at 04ed000c eip 08055a6d esp bff76430 error 4

```

I would really appreciate any help with this issue.

Many thanks,
CaMason

---

### Post by camason on 2008-06-13
Just to add to this...

It seems compiz is not starting properly the first time I turn my PC on. I can log in, and I only get the standard desktop effects settings. My system tray icons are also 'floating' as windows. I need to restart X (risking system lockup) and log-in again.

Thank you

---

