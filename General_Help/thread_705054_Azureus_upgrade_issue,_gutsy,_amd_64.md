---
title: "Azureus upgrade issue, gutsy, amd 64"
date: 2008-02-23
forum: General Help
---

### Post by thinman1189 on 2008-02-23
I'm having some trouble with azureus. I opened it up and I got a message saying to download an update. Then when I went to reopen it gave me the option again, this time a window popped up in the corner saying it had shutdown wrong. Now whenever I open it it closes within 2 seconds of showing the main screen. The update seemed weird because it mentioned OSX but I wasn't sure.

---

### Post by chajuram on 2008-03-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020](https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, 

I have the same problem. I tried following this post but it did not help me. 

[https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020](https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020)

Chajuram

---

### Post by cozmicharlie on 2008-03-21
Some people have reported that Azuerus updates load the Iced tea version of java.  This version does not work very well in Ubuntu (see this thread [http://ubuntuforums.org/showthread.php?t=725926&highlight=azureus](http://ubuntuforums.org/showthread.php?t=725926&highlight=azureus)).  You can check which version of Java you are using and change it using this command:
```
sudo update-alternatives --config java
```

You need to be using the Sun-java6-jre version not Iced tea.  For some reason, simply changing the version does not work with Iced Tea so I recommend if it is installed to uninstall it.  Once you are using Sun-Java6-JRE you should be good to go.

Post back if you are still having the problem because there is another possibility also - hopefully this will fix it.

---

