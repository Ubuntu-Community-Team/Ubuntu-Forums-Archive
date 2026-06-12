---
title: "xfreerdp issue connecting to a Win11 machine"
date: 2023-12-28
forum: General Help
---

### Post by QIII on 2023-12-28
Specifically about xfreerdp, not networking.

I can rdp from a Win10 machine to my Win11 machine, but not from Linux using xfreerdp.  I'm wondering if there is something specific about xfreerdp vis-a-vis Win11.

Using the simplest of commands

```
nohup xfreerdp /v:192.168.10.xxx:3389 /u:<user> /p:<password>
```

it appears that I am either getting no connection or I am getting a momentary connection that disconnects immediately.  No errors are reported.

Is there anything about xfreerdp that requires any special flags for Win11?

(BTW, krdc doesn't work either.)

Edit:

telnet returns no route to host.

I can ping from the Win10 box, but not from Ubuntu.

---

### Post by QIII on 2023-12-28
Bah!  PEBKAC

I had assigned the virtual machine with a network device already being used by another VM.

Senior moment, nothing more.

---

### Post by ActionParsnip on 2023-12-29
Please mark as solved if the issue is now resolved :)

---

