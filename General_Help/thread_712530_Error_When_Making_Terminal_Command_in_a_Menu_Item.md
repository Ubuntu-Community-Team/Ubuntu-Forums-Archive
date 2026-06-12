---
title: "Error When Making Terminal Command in a Menu Item"
date: 2008-03-01
forum: General Help
---

### Post by Roanoke on 2008-03-01
In my applications menu, I have a custom launcher that makes a command in the terminal. The command is an alias that points to:

```
vkeybd --octave 6 & seq24 --manual_alsa_ports & zynaddsubfx -r 48000 -b 128 & hydrogen -d jack &
```

And when I click on it, a terminal opens, and I get this error message:

```
There was an error creating the child process for this terminal
```

Any ideas?

---

### Post by dcstar on 2008-03-01
> **Roanoke said:**
> In my applications menu, I have a custom launcher that makes a command in the terminal. The command is an alias that points to:

```
vkeybd --octave 6 & seq24 --manual_alsa_ports & zynaddsubfx -r 48000 -b 128 & hydrogen -d jack &
```

And when I click on it, a terminal opens, and I get this error message:

```
There was an error creating the child process for this terminal
```

Any ideas?

You are trying to use shell features outside of a shell.

---

