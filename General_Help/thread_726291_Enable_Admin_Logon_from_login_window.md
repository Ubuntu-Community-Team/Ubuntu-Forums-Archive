---
title: "Enable Admin Logon from login window"
date: 2008-03-16
forum: General Help
---

### Post by Funky91 on 2008-03-16
Anyone know how to allow root login. 

From looking at other posts it seems you can do it in System, Administration and Login Window.

However when I tick allow local system administrator login (in the security tab) and click close when I reopen it it has unticked it so I cannot login as root.

Anyone know why this is?

---

### Post by scragar on 2008-03-16
it's under the local tab of the login prefs, it say's something like "enable system administrator to log in"

---

### Post by justleen on 2008-03-16
you need root permission to grant root login access

```
 gksudo gdmsetup 
```

---

### Post by bapoumba on 2008-03-16
[Please read this]("http://ubuntuforums.org/showthread.php?t=716201").

---

### Post by Funky91 on 2008-03-17
ooo, I didn't know that. 

In that case, how do I open a File Browser (showing 'computer') as root?

---

### Post by dboot on 2008-03-17
From the above link:

If you want to drag and drop files to system folders, you can run one of the following commands to launch a file browser as root. You can run the command from the Run dialogue by pressing Alt-F2. You can run it from the terminal. Or you can run it as keyboard shortcut or launcher command.

For Ubuntu
```
gksudo nautilus
```

Nautilus is the file browser for Ubuntu.

---

