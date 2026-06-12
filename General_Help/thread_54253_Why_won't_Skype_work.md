---
title: "Why won't Skype work?"
date: 2005-08-04
forum: General Help
---

### Post by RyaninZion on 2005-08-04
I have installed Skype via apt.  But am basically unable to use it.  Whenever I try to place a call, it shows that it is trying to connect to the other user, but on their end nothing happens.

The other user can see me online, but there is no activity from me.

Are there any steps I can take to remedy this?

Thanks

---

### Post by bunced on 2005-08-04
You need to install libqt3c102-mt from Synaptic.

---

### Post by RyaninZion on 2005-08-04
I have libqt3c102-mt installed.

---

### Post by nocturn on 2005-08-04
[QUOTE=RyaninZion]I have installed Skype via apt.  But am basically unable to use it.  Whenever I try to place a call, it shows that it is trying to connect to the other user, but on their end nothing happens.

The other user can see me online, but there is no activity from me.

Are there any steps I can take to remedy this?

Thanks[/QUOTE]

Maybe something is blocked by your firewall/proxy?

---

### Post by RyaninZion on 2005-08-04
I gave Skype its own arbitrary port number, and then went into Firestarter and set "Allow service" for "Everyone" for that port.  

I have also tried turning the firewall off and using Skype.  No help.

---

