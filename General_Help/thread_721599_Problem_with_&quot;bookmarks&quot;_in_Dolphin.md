---
title: "Problem with &quot;bookmarks&quot; in Dolphin"
date: 2008-03-11
forum: General Help
---

### Post by jpc2769 on 2008-03-11
Greetings,

I am running Kubuntu 7.10 on a Panasonic Toughbook CF-52. Today, when closing Dolphin, I started getting the following error message:

"Unable to save bookmarks in /home/jason/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive."

The partition is nowhere near being full. I have no idea what this message is referring to, can someone please give me some assistance?

Thanks.

Jason

---

### Post by linuxwizard on 2008-03-11
This is a known bug with Dolphin. In konsole type > sudo chown jbaerbock:jbaerbock /home/jbaerbock/.kde/share/apps/d3lphin/bookmarks.xml > replace jbaerbock with your user name.

---

### Post by jpc2769 on 2008-03-12
Thanks for your prompt help, I really appreciate it.

Regards,
Jason

---

