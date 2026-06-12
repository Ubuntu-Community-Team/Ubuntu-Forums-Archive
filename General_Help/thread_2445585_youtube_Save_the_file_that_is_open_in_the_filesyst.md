---
title: "youtube: Save the file that is open in the filesystem?"
date: 2020-06-16
forum: General Help
---

### Post by seeker.k3 on 2020-06-16
I used to be able to start a youtube video, then find it in the filesystem by searching for open files,

```
$ lsof -n | grep Flash
```

and then save the flash file to one of my directories on the drive.

Either I can't now remember the method correctly, or the world has changed---I can't do it anymore. Can anyone tell me where the open file is or how I can find it in the filesystem (and access it).

Note: Please don't tell me I can download youtube videos using a browser add-on or some particular software---that's not my question.

Cheers.

---

### Post by TheFu on 2020-06-16
Doesn't downloading content from youtube violate their ToS?

> The following restrictions apply to your use of the Service. **You are not allowed to**:

    access, reproduce, **download**, distribute, transmit, broadcast, display, sell, license, alter, modify or otherwise use any part of the Service or any Content except: (a) as expressly authorized by the Service; or (b) with prior written permission from YouTube and, if applicable, the respective rights holders;
[https://www.youtube.com/static?template=terms](https://www.youtube.com/static?template=terms)

Yes, the world has changed.

---

### Post by monkeybrain20122 on 2020-06-17
Also youtube hasn't used flash for years.   In fact very few websites still use flash.

---

### Post by gdesilva on 2020-06-17
As @TheFu mentioned above it may be illegal to download but the simplest technical solution is to use youtube-dl, either from the repo or from [https://ytdl-org.github.io/youtube-dl/](https://ytdl-org.github.io/youtube-dl/) which will give you the latest version. Again, legality is something you will need to consider before using it.

---

### Post by coffeecat on 2020-06-17
> **gdesilva said:**
> Again, legality is something you will need to consider before using it.

And forum rules and policy are something that need to be considered before posting about it: [https://ubuntuforums.org/showthread.php?t=2439118](https://ubuntuforums.org/showthread.php?t=2439118)

Thread closed.

---

