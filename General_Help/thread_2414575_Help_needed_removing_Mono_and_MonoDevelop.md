---
title: "Help needed removing Mono and MonoDevelop"
date: 2019-03-12
forum: General Help
---

### Post by tomdkat on 2019-03-12
So, a while ago, I installed MonoDevelop with the intent of experimenting with C# on Linux.  The installation went pretty smoothly but I never got around to doing any C# work.  lol  Anyway, I recently ran an update of Ubuntu (18.10) and a ton of Mono-related packages were downloaded and installed.  I think the gac utility executable had a problem such that the Mono update didn't fully complete.  Right now, I'm stuck where I can't remove Mono (the runtime or anything) nor can I remove MonoDevelop.  This isn't a huge deal but this is preventing *other* Ubuntu updates from being installed.  *That* is why I'm posting this thread here.

I've searched around for help on removing a "broken" Mono package and none of the suggested methods worked.

For example:
[https://askubuntu.com/questions/1104286/mono-broken-after-attempt-to-upgrade-unable-to-use-apt](https://askubuntu.com/questions/1104286/mono-broken-after-attempt-to-upgrade-unable-to-use-apt)

Anyway, I'm at the point of simply removing the Mono related files from the filesystem.  Of course, this won't update the repository of installed applications and packages such that apt probably won't work correctly.   If I were to manually remove the Mono related files from the filesystem, how could or should I update the repository of installed packages such that apt will work and I can update other parts of my system?

Thanks in advance!

Peace....

---

### Post by Impavidus on 2019-03-12
In other words: your package management is messed up.

Let's find out why the package manager cannot recover:```
sudo apt install -f
```And let's list the packages in an improper state:```
dpkg --list | egrep -v '^rc|^ii'
```

---

### Post by tomdkat on 2019-03-12
Thanks for the reply!  The output from both commands is pretty long, so what's the best way to post it?

Peace...

---

### Post by Impavidus on 2019-03-13
Paste it in a post here, in code tags. Unless you're talking about hundreds of lines. In that case a pastbin may be more appropriate.

If even the second command gives a very long output, there's something seriously wrong with your system.

---

### Post by tomdkat on 2019-03-13
Thanks!   The output is quite long, so I'll post links to pastebin posts.

Here's the output from the "sudo apt install -f" command:  [https://pastebin.com/AgFr8jpb](https://pastebin.com/AgFr8jpb)

Here's the output from the "dpkg --list" command:  [https://pastebin.com/3U63JMJ7](https://pastebin.com/3U63JMJ7)

Everything is related to Mono, which is what I'm trying to remove.

Thanks!

Peace...

---

### Post by tomdkat on 2019-03-15
Well, this situation has worked itself out.  Apparently, some Mono updates were released such that running "sudo apt --fix-broken install" corrected the issue I was having and now I'm able to run Ubuntu 18.10 updates.

Peace...

---

