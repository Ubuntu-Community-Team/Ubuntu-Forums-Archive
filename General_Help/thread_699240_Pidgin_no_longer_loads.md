---
title: "Pidgin no longer loads"
date: 2008-02-17
forum: General Help
---

### Post by Trapper Dave on 2008-02-17
I used to have Pidgin loading up along with Ubuntu. Now it doesn't at all. If I manually select Pidgin to load, it will show up in the bottom panel telling me that it's loading, but then that will vanish and it won't load.

I've tried reinstalling it through Synaptic, but I still can't get it to work. Does anyone have any ideas?

---

### Post by chrisccoulson on 2008-02-17
What happens if you type
```
pidgin
```
in a terminal? What is the output?

---

### Post by staticvoid on 2008-02-17
System>Preerences>Sessions... did you add pidgin there?

sv

---

### Post by Trapper Dave on 2008-02-17
Typing in pidgin gets;

```
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
```

I did have Pidgin in the sessions for start up, but removed it when I realised it wasn't working.

However I have just received a message over Google Talk through Pidgin and it's opened a conversation window. It seems that it cannot load the window with all my contacts in. This is rather odd, I have no idea what to do.

---

### Post by Flyingjester on 2008-02-17
I would try reinstalling, try removing pidgin, pidgin-data, and libpurple0 in synaptic and reinstalling them. If that doesn't work, try removing them again, and going to getdeb.net and downloading the newest version of pidgin.

---

### Post by chrisccoulson on 2008-02-17
> **Trapper Dave said:**
> Typing in pidgin gets;

```
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
```

I did have Pidgin in the sessions for start up, but removed it when I realised it wasn't working.

However I have just received a message over Google Talk through Pidgin and it's opened a conversation window. It seems that it cannot load the window with all my contacts in. This is rather odd, I have no idea what to do.

is Network Manager running?

---

### Post by viralbus on 2008-03-22
I have the same problem with Pidgin, and I no, I'm not using Network Manager because I switched to wicd (had to to access my wireless network).

---

### Post by surfed on 2008-03-22
Seems like pidgin depends on NetworkManager, had same problem and installing it helped.

---

