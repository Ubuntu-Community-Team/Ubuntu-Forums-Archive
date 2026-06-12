---
title: "nvidia-settings outputs &quot;ERROR: Unable to load info from any available system&quot;"
date: 2021-09-20
forum: General Help
---

### Post by fab1can on 2021-09-20
I have Ubuntu 20.04.3, I installed nvidia-drive-470, my video card is GTX 1050Ti.
As I said in title nvidia-settings outputs
```

ERROR: Unable to load info from any available system


(nvidia-settings:8026): GLib-GObject-CRITICAL **: 11:41:14.621: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 11:41:14.623: PRIME: No offloading required. Abort
** Message: 11:41:14.623: PRIME: is it supported? no

```
and the nvidia-settings window is empty. The graphics in my system details is "llmvpipe (LLVM 12.0.0,256 bits)" instead of my graphics card.

[IMG]https://i.ibb.co/4drgM1Z/Screenshot-from-2021-09-20-11-49-25.png[/IMG]

---

### Post by ActionParsnip on 2021-09-20
If the system has that switching GPU nonsense then try:
```

prime-run nvidia-settings

```
Does that help any?

---

### Post by fab1can on 2021-09-20
> **ActionParsnip said:**
> If the system has that switching GPU nonsense then try:
```

prime-run nvidia-settings

```
Does that help any?
This outputs
```

prime-run: command not found

```

---

### Post by Bashing-om on 2021-09-20
fab1can - Hello

Seems that the driver (module) is not loaded. What method did you use to install the driver ?
What have we available to work with - post the outputs of terminal commands:
```

sudo lshw -C display
lspci -k | grep -iEA5 'vga|3d'
dpkg -l | grep -i nvidia

```

From these diagnostics we see what it will take to make things right.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

