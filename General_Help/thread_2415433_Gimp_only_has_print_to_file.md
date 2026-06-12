---
title: "Gimp only has print to file"
date: 2019-03-25
forum: General Help
---

### Post by raleigh3 on 2019-03-25
If I try to print from Gimp, it only shows print to file.

It offers none of my printers.

---

### Post by #&amp;thj^% on 2019-03-25
Can you try:
```

sudo snap refresh gimp --edge
sudo snap connect gimp:cups-control
```
On ubuntu 18.10, I noticed my printers weren't visible. "snap connect gimp:cups-control" fixed it though. 
```
System:
  Host: me-ThinkPad-T430 Kernel: 4.18.0-16-generic x86_64 bits: 64 
  Desktop: Unity Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 

```

---

### Post by Autodave on 2019-03-25
Are you using the *export* function?

---

### Post by raleigh3 on 2019-03-25
> **1fallen said:**
> Can you try:
```

sudo snap refresh gimp --edge
sudo snap connect gimp:cups-control
```
On ubuntu 18.10, I noticed my printers weren't visible. "snap connect gimp:cups-control" fixed it though. 
```
System:
  Host: me-ThinkPad-T430 Kernel: 4.18.0-16-generic x86_64 bits: 64 
  Desktop: Unity Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 

```

Thanks so much.

Works great now.

---

### Post by raleigh3 on 2019-03-25
> **Autodave said:**
> Are you using the *export* function?

I had opened an existing image.

---

