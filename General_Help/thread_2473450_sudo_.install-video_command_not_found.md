---
title: "sudo: ./install-video: command not found"
date: 2022-04-05
forum: General Help
---

### Post by Jalke on 2022-04-05
I'm trying to install DroidCam on my Ubuntu system but am getting stuck when I punch in: sudo ./install-video
which gives me the message: sudo: ./install-video: command not found

I'm a bit of a noob when it comes to Linux and terminal commands.  Just wondering if there's anything obvious to do here.

---

### Post by yetimon_64 on 2022-04-05
That can happen if you forget to "cd" into the droidcam directory.

[[COLOR=#0000ff]--These--[/COLOR]]("https://www.dev47apps.com/droidcam/linux/") (link in blue text) are the instructions I am following, please check they are what you are using as well. When following these instructions I got the same error as yourself when I missed the "cd droidcam" part of the instructions and only used the sudo command.

You have to be in the droidcam folder to issue the "sudo ./install-video" command.

---

### Post by ActionParsnip on 2022-04-05
The working directory is important. If you run:
```

sudo updatedb
locate install-video*

```
What is the output?

---

