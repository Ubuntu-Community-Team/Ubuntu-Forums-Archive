---
title: "sharing aceess deny"
date: 2019-04-24
forum: General Help
---

### Post by m.eraj1995 on 2019-04-24
i am accessing Ubuntu shared folder in windows it says access denied, user name password is incorrect ,

---

### Post by HermanAB on 2019-04-24
Howdy,

Assuming that you are sharing a folder with Samba, there are a multiplicity of things that can be wrong with the network setup and access controls.  You need to start at the bottom and work your way up the stack.  

Start by running smbclient on the Ubuntu host and try to connect to the shared folder - the error messages will tell you exactly what is wrong - google them.

Once that works, try to connect with smbclient from Windows (you may need to install cygwin to get smbclient), using the exact same command as before.  Again google the error messages.

Only once that works, try the Windows file manager, since it doesn't give you proper error messages.

---

