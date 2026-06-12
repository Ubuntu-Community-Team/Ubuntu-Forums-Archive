---
title: "Pointer becomes ineffective, though still responsive"
date: 2023-09-26
forum: General Help
---

### Post by cobras on 2023-09-26
[COLOR=#232629][FONT=-apple-system]I'm running Ubuntu 22.04.3 on a Dell Precision 7510, and several days ago my cursor/pointer began acting up in several ways - dragging icons unexpectedly, ineffective clicks, etc., though the pointer would remain responsive. This is true with both the mouse and the touchpad. Sometimes it seems as if there's just a huge lag, but I don't think that's the problem. Gets to where I have to power off the machine because warm booting is not possible, nothing is.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]At times I can hit Esc to get it going again (tried that just on a lark), but mostly I need to hard boot. Sometimes letting the system sleep for a few minutes revives it.

I've got dual boot and Windows seemed fine after half an hour of use.

Please share any ideas you may have.[/FONT][/COLOR]

---

### Post by Autodave on 2023-09-26
What happens if you disconnect the mouse and only use the touchpad?

---

### Post by cobras on 2023-09-26
> **Autodave said:**
> What happens if you disconnect the mouse and only use the touchpad?

I have tried that and gotten the same results.  Also, I've gone back again to check with Windows and had the same problem this time, so I'm thinking now it's the hardware.  Though I suppose it is possible that, for example, both the Linux and Microsoft drivers might simultaneously need an update.  Or something else I can't even imagine, which is why I'm here.

---

### Post by MAFoElffen on 2023-09-27
Please attach the file this would create to a post using "Advanced Reply" to post it:
```

sudo lsusb -vvv > ~/Documents/usb_details.txt

```
It should be too large to try to post it within CODE Tags. It will be created in your Home Documents folder.

---

### Post by cobras on 2023-09-27
> **MAFoElffen said:**
> Please attach the file this would create to a post using "Advanced Reply" to post it:
```

sudo lsusb -vvv > ~/Documents/usb_details.txt

```
It should be too large to try to post it within CODE Tags. It will be created in your Home Documents folder.

```
xxxxxxxxxx:~$ sudo lsusb -vvv > ~/Documents/usb_details.txt
can't get debug descriptor: Resource temporarily unavailable
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable

```

Software is up to date.

---

### Post by #&amp;thj^% on 2023-09-27
It should be there:
```
cd Documents && ls usb_details.txt
usb_details.txt

```

---

### Post by cobras on 2023-09-27
[https://paste.ubuntu.com/p/nkbYptvpVM/](https://paste.ubuntu.com/p/nkbYptvpVM/)

---

### Post by cobras on 2023-09-29
> **cobras said:**
> [https://paste.ubuntu.com/p/nkbYptvpVM/](https://paste.ubuntu.com/p/nkbYptvpVM/)

Is this not what was requested?

---

### Post by cobras on 2023-10-08
OK, got it acting right again.  Thanks anyway.

---

