---
title: "Error at boot:  udisksd[2597]: The string `&#65533;#001' is not valid UTF-8."
date: 2015-10-31
forum: General Help
---

### Post by fdo2 on 2015-10-31
I'm having errors like this:

```

Oct 31 11:33:16 gnuradio udisksd[2597]: The string `&#65533;|H&#65533;&#65533;' is not valid UTF-8. Invalid characters begins at `&#65533;|H&#65533;&#65533;'
Oct 31 11:33:16 gnuradio udisksd[2597]: The string `&#65533;Mi#002' is not valid UTF-8. Invalid characters begins at `&#65533;Mi#002'
Oct 31 11:33:16 gnuradio udisksd[2597]: The string `@&#65533;u#002' is not valid UTF-8. Invalid characters begins at `&#65533;u#002'
Oct 31 11:33:16 gnuradio udisksd[2597]: The string `&#65533;#001' is not valid UTF-8. Invalid characters begins at `&#65533;#001'
Oct 31 11:33:16 gnuradio udisksd[2597]: The string `@&#65533;u#002' is not valid UTF-8. Invalid characters begins at `&#65533;u#002'
Oct 31 11:33:17 gnuradio udisksd[2597]: message repeated 3 times: [ The string `@&#65533;u#002' is not valid UTF-8. Invalid characters begins at `&#65533;u#002']
Oct 31 11:33:17 gnuradio udisksd[2597]: The string `&#65533;|H&#65533;&#65533;' is not valid UTF-8. Invalid characters begins at `&#65533;|H&#65533;&#65533;'
Oct 31 11:33:17 gnuradio udisksd[2597]: The string `&#65533;Mi#002' is not valid UTF-8. Invalid characters begins at `&#65533;Mi#002'
Oct 31 11:33:17 gnuradio udisksd[2597]: The string `@&#65533;u#002' is not valid UTF-8. Invalid characters begins at `&#65533;u#002'
Oct 31 11:33:17 gnuradio udisksd[2597]: The string `&#65533;#001' is not valid UTF-8. Invalid characters begins at `&#65533;#001'
Oct 31 11:33:17 gnuradio udisksd[2597]: The string `@&#65533;u#002' is not valid UTF-8. Invalid characters begins at `&#65533;u#002'
Oct 31 11:33:17 gnuradio dbus[649]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Oct 31 11:33:17 gnuradio udisksd[2597]: message repeated 3 times: [ The string `@&#65533;u#002' is not valid UTF-8. Invalid characters begins at `&#65533;u#002']

```

I dont know where are they coming from and why they have started.
I'm using ubuntu 14.04 LTS fresh installed on a pendrive using  /dev/sda1 as the full pendrive, grub working on the mbr of the pendrive, and all working fine until these errors appeared.  They don't seem to make anything go wrong, but I guess having errors is not a good thing.

Any help?

regards

---

### Post by ajgreeny on 2015-10-31
Looks as if it related to **gnuradio**.  Do you have that installed and working?

I've no idea what exactly it does or is used for but it may give you a starting point in your search for an answer.

---

### Post by fdo2 on 2015-10-31
gnuradio is the name of the "computer"

---

### Post by ajgreeny on 2015-10-31
Ah.  OK!

Sorry about that but there is a package called **gnuradio** and I wondered if that was related.

Where (in what file or command output) do all those errors appear?  It looks as if it's syslog.

What locale settings do you have set?

---

### Post by fdo2 on 2015-11-02
> **ajgreeny said:**
> Ah.  OK!

Sorry about that but there is a package called **gnuradio** and I wondered if that was related.

Where (in what file or command output) do all those errors appear?  It looks as if it's syslog.

What locale settings do you have set?

At boot time (when entering in the X system) it appears one or more popups telling me there has been an error, but they dont give me more information about the error. The error I reported is extracted from syslog, and the only thing I now about it is that is related to udiskd and that it seem something extrange about some strings.

locale is spanish UTF8
```

ubuntu@gnuradio:~$ locale
LANG=es_ES.UTF-8
LANGUAGE=es
LC_CTYPE="es_ES.UTF-8"
LC_NUMERIC="es_ES.UTF-8"
LC_TIME="es_ES.UTF-8"
LC_COLLATE="es_ES.UTF-8"
LC_MONETARY="es_ES.UTF-8"
LC_MESSAGES="es_ES.UTF-8"
LC_PAPER="es_ES.UTF-8"
LC_NAME="es_ES.UTF-8"
LC_ADDRESS="es_ES.UTF-8"
LC_TELEPHONE="es_ES.UTF-8"
LC_MEASUREMENT="es_ES.UTF-8"
LC_IDENTIFICATION="es_ES.UTF-8"
LC_ALL=
ubuntu@gnuradio:~$

```

---

