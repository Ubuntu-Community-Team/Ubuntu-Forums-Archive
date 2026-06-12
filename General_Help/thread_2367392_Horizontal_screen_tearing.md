---
title: "Horizontal screen tearing"
date: 2017-07-29
forum: General Help
---

### Post by crouchy89 on 2017-07-29
Hi,
I am running Ubuntu 16.04 LTS on a Dell Precision 5510 laptop. I get bad horizontal screen tearing, but only in specific circumstances:
- Some videos when viewed full screen on YouTube and Netflix (the same video doesn't tear when not full screen)
- External monitor has bad horizontal tear

Graphics card:
```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)

```



The laptop also has a Nvidia Quadro M1000M Graphics card, but I don't know how to switch over to it. I cannot run nvidia-xconfig, but I know that nvidia-settings and nvidia-current are up to date:
```

nvidia-settings is already the newest version (375.26-0ubuntu1).
nvidia-current is already the newest version (304.135-0ubuntu0.16.04.1).

```

I have been doing a lot of searching, and there are so many links and threads and things to try that I just don't know where to start. If anybody can help give me tips on how to proceed it would be greatly appreciated.

---

### Post by zerubbabel on 2017-08-23
I searched far and wide for a remedy for screen tearing, which I experienced while scrolling in LibreOffice using the Ctrl-Down action to go from paragraph to paragraph. Continually this resulted in lines of text being fractured, which was very annoying. I tried everything I could find in dozens of forum entries, but the only thing that has worked is switching from Ubuntu/Linux Mint to Debian 9.1. I made the switch to Debian, which was tedious, for other reasons, but was very pleasantly surprised to find that the screen tearing does not happen anymore.

---

