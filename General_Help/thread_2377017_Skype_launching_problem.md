---
title: "Skype launching problem"
date: 2017-11-08
forum: General Help
---

### Post by jobtmp on 2017-11-08
Skype used to work normally. Suddenly stopped launching without visible reasons. It actually starts, but after filling in ID and password closes without further notification. Tried it many times with the same result. It's Skype 5.5.0.1.
Please advise.

---

### Post by chocholusik on 2017-11-08
Version 5.x (Skype for linux beta) is not supported anymore, you have to update to newer version (not beta). Currently version  8.10.0.4: [https://www.skype.com/en/get-skype/](https://www.skype.com/en/get-skype/)

---

### Post by jobtmp on 2017-11-08
TY for the reply. Additional question: Do I have to remove the previous version of Skype manually before installing the new or it will be upgraded automatically?

I've removed the Skype 5.... and installed (?) the new version (8....). But the latter wont start normally. Please advise further actions

---

### Post by kostkon on 2017-11-08
Try running it from the terminal, i.e.:
```
skypeforlinux
```
see if you'll get any error messages.

Also, keep in my that the latest 8.x version of Skype requires a CPU with SSE3 support. You could check if your CPU is SSE3 capable.

---

### Post by ajgreeny on 2017-11-08
Also see [https://ubuntuforums.org/showthread.php?t=2376306](https://ubuntuforums.org/showthread.php?t=2376306) which I started after a problem with the autostart in skype Tools menu, which began in skype-8.9.0.1 but continues still though slightly easier to get working in the 8.10.0.4 update that I got today and another thread about the same thing at [https://ubuntuforums.org/showthread.php?t=2376539](https://ubuntuforums.org/showthread.php?t=2376539) 

There are a lot of complaints about this skypeforlinux package on the skype support site at [https://answers.microsoft.com/en-us/skype/forum/skype_linux](https://answers.microsoft.com/en-us/skype/forum/skype_linux) so it may be worth you adding a new thread or replying to an existing thread there.

---

