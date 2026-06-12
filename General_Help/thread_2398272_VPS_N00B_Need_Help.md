---
title: "VPS N00B Need Help"
date: 2018-08-09
forum: General Help
---

### Post by joshhazzord on 2018-08-09
So I'm going to be buying a VPS running Ubuntu so that I can run a console client for a game. There is a video tutorial for what I want to do, in the video, he uses mono to open the application however in order to run more than one he uses another software/tool called screen. I really don't like the sound of using this it looks like a pain and would rather just run one script.

So in windows, the script I would run in a batch file would be like this

```

start /min MinecraftClient.exe email password IP
timeout 5

start /min MinecraftClient.exe email password IP
timeout 5
```



however, there is no start so it would be this

```
mono MinecraftClient.exe email password IP
```



This is the batch file he uses in the video, however, he then changes screen and opens it again and it seems like a long process and you have to change between the screens so I'm just wondering if I would be able to run this multiple times with one script like I would on windows.

Thanks, Josh!

---

### Post by QIII on 2018-08-09
Since the issue is less about server operation than a particular package, moved to General Help per user request.

---

### Post by joshhazzord on 2018-08-09
Thank you.

---

