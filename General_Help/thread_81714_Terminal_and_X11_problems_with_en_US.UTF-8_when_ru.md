---
title: "Terminal and X11 problems with en_US.UTF-8 when run application in a remote machine"
date: 2005-10-25
forum: General Help
---

### Post by jfosorio on 2005-10-25
Hello,
I am using ssh to launch remote applications in a Solaries 8  machine, the applications run remotely and are displayed back using the X11 server in the Ubuntu machine. It seems that the terminal configuration provided with Ubuntu is not compatible with Solaries.  When I run a graphic application I have the next error:
"XView warning: Locale en_US.UTF-8 has codeset that XView is not supporting;
Use "en_US" locale by having an option "-lc_basiclocale en_US. (Server package)"
In some cases this error do not allow the application to behave properly.
I have tried to resolve the problem by changing the terminal > set character encoding  values in the Gnome terminal in the Ubuntu machine but any of the sets provided seems to resolve the problem. Any ideas ?
Felipe

(I apologize for post this message again, but it seems to me It was not clear the first time. )

---

