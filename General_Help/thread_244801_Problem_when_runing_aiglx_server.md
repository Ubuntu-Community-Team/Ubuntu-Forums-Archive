---
title: "Problem when runing aiglx server"
date: 2006-08-26
forum: General Help
---

### Post by scratched on 2006-08-26
Today I tried setting up aiglx + compiz on my laptop. I have an intel 855 graphics card. I followed the instructions from [this thread]("http://www.ubuntuforums.org/showthread.php?t=145068") on how to install  xorg-aiglx + compiz exactly (at least I think so), and when I restarted gdm, I got an error screen that looks exactly like the "BSOD" on the [FixForUpgradeIssue page on ubuntu.com]("http://www.ubuntu.com/FixForUpgradeIssue").

I managed to figure out how to 'fix' the problem enough to be able to start gdm again, but I had to turn off the aiglx server to do that (by commenting out the aiglx server lines in the 'gdm.conf-custom' file).

Everything works fine except for compiz, which when turned on removes the bars from the tops of all my windows and makes it impossible to focus on any particular window. I have to switch to metacity manually to bring the top bars back and fix everything.

These lines in my 'gdm.conf-custom' file are what breaks the xorg server.
```
[servers]
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true
```

If I comment out those lines everything runs fine.

Could anyone tell me what I might need to do to fix this problem or what I possibly did wrong? 

I spent a lot of time browsing on lynx figuring out how to get xserver back up again, I don't want to give up on aiglx after all the time I put into making compiz work.

For anyone wondering, I already tried the solution on [ubuntu.com]("http://www.ubuntu.com/FixForUpgradeIssue") for the upgrade issues. That didn't help me.

---

### Post by Corvillus on 2006-08-27
I'm using an i855GM as well. I posted what I did for my setup on on my blog [here](http://corvillus.com/2006/08/03/how-to-set-up-aiglx-and-compiz-on-ubuntu-606-running-gnome/), but it's pretty much the same info as on the thread you mentioned. One thing I did differently from the suggestion in the forum was leave my xorg.conf sections completely intact and simply add the new entries as opposed to deleting the other entries as suggested in that that thread.

---

