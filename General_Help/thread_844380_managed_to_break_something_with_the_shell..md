---
title: "managed to break something with the shell."
date: 2008-06-29
forum: General Help
---

### Post by Amolad on 2008-06-29
I think I did something silly...

entered this command without knowing fully what it did in an attempt to get sound working in some programs under wine:

```
sudo ln -s libjack-0.100.0.so.0.0.23 libjack.so

```

And now things don't work.

How do I undo it?

Thanks :confused:

---

### Post by brian_p on 2008-06-29
> **Amolad said:**
> I think I did something silly...

entered this command without knowing fully what it did in an attempt to get sound working in some programs under wine:

```
sudo ln -s libjack-0.100.0.so.0.0.23 libjack.so

```

And now things don't work.

How do I undo it?

Thanks :confused:

```
sudo rm libjack.so
```

---

