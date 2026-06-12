---
title: "Desktop wont load because of firefox?"
date: 2008-01-29
forum: General Help
---

### Post by KaiDog on 2008-01-29
I accidentally shut down Kubuntu in a hurry with a firefox window still open. Now, when I load it up, it sort of freezes for a minute when it's loading desktop and then continues. Except the desktop is blue, I can't do anything on it, and I can't open Konquerer. I haven't tried running GNOME yet, but I will see if that gives me any different results. But I'd like to fix this problem with KDE.

Firefox works fine. gThumbs freezes when I load it. Kalzium worked fine, so did Movie Player and VCL. I have Kubuntu dual booted with WindowsXP. When I restarted my computer, I restarted it to reboot into Windows. I have a 3rd partition that I keep files in. VCL and Movie Player work fine when I try to open a file from the partition Ubuntu is loaded on, but just sits there without doing anything when I try to open a file from that 3rd partition I mentioned earlier (it just sits there like it's loading).

If there's anymore info you need let me know. Thanks for your help.
Kai

---

### Post by mlissner on 2008-01-29
I'd bet this has something to do with your user profile. You might try creating another user and logging in (in KDE) as them. If that works, we will have isolated the problem a bit.

After that, you can either choose to deal with the problem some more, or you can just move your files to the new profile, and remove the old user (your current user). 

It sounds like you have corrupted the disk a bit. Did you do a hard shutdown (ie, pull the plug), or a proper shutdown (ie pressing the shutdown button)? If the former, attributing the issue to that makes sense. If the latter, then something else is amiss.

---

### Post by KaiDog on 2008-02-01
Thanks mlissner. I rebooted and tried it on gnome. It worked fine until I tried to open that one partition. But when I rebooted, it did a self diagnosis which it normally does from time to time and apparently fixed it because I'm not having any problems. I haven't tried it on KDE again since I found that gnome runs more smoothly. But I'll keep your advice in mind for future reference, thanks!

---

### Post by mlissner on 2008-02-01
No problem. Creating a new user like that is a good trick, if you're lazy with actually fixing problems. Glad to hear it worked.

---

