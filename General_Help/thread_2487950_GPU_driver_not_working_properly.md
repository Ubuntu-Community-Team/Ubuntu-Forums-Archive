---
title: "GPU driver not working properly"
date: 2023-06-19
forum: General Help
---

### Post by dwssapresnak on 2023-06-19
hello, I'm using Ubuntu version 22.04 and I've run into a few problems.
1 issue: Display works worse when GPU driver is installed. When you install Open Source software, screen sharing and applications work fine. but when i install nvidia's driver, there are corruptions on the screen I share. I'm watching a video on the screen that I connected with the hdmi cable, the pixels shift, some parts of the screen freeze. Applications that normally ask for nvidia drivers run worse while expecting them to work better. 2 issue: my computer has 8 gb + 8 gb of ram that I added later, 16 gb in total. When I look from the terminal, I see 16gb of RAM, but the computer feels as if it is using 8GB of RAM.

```
free -h
               total        used        free      shared  buff/cache   available
Mem:            14Gi       5.6Gi       5.2Gi       213Mi       3.6Gi       8.4Gi
Swap:          2.0Gi          0B       2.0Gi
```
Output of "free -h" command. This output should be "used + free = total", right?  The free part should be 8.4, right?

---

