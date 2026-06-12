---
title: "ZED does not run after Install, with 4.2.30-generic recently updated on my Laptop!"
date: 2016-03-01
forum: General Help
---

### Post by William_Griff_Hage on 2016-03-01
Hello friends, I recently was trying to install the ZED IDE, which I have had wonderful experiences from being an open source IDE used on the Chrome App Store. However, I updated my laptop to the recent kernel 4.2.30-generic, which people say they have issues with. I expected the Zed to install and run on start, but upon installation, the terminal kept trying to find a initial module for the 4.2.30-generic kernel to run ZED on, it would go to dpmod everytime, and kept making me go to a system mail screen which I denied everytime in fear it would compromise my security. After the installation, I typed zed into my unclosed terminal, and it told me I have to run as root in order to run ZED, I did so by doing sudo bash. I typed in the zed again into the terminal and it gives me this everytime I do so.

```
Found PID 30490 bound to PID file "/var/run/zed.pid"
```

I'm confused about this, what is causing Zed not to run, and how can it be fixed. I know I can delete it, but how can  I?

---

