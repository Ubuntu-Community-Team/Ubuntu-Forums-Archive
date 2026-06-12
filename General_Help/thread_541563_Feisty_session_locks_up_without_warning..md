---
title: "Feisty session locks up without warning."
date: 2007-09-03
forum: General Help
---

### Post by GenuineXP on 2007-09-03
It seems that at arbitrary times my session seems to lock up while using Feisty on my desktop. Often, the cursor will continue to follow mouse movement, but I can't interact with anything. It's almost as if the keyboard has been entirely disconnect (hitting the *lock keys don't toggle the keyboard lights) and the mouse is just "lost", not letting me click on anything.

Sometimes it's very obvious that the computer is still running merrily, because content in the background will continue to run, whether it be playing sounds and music or displaying some graphics.

I also know that the machine is not dead because I can ssh into my desktop using my laptop. In fact, this is what I've been doing to get around the problem, but it's getting very annoying because it happens almost twice a day! To fix it, I usually kill the x-session-manager process and the desktop jumps right back to the login screen.

Once the same thing happened while I was using a manually installed copy of Eclipse 3.3. I couldn't interact at all with the keyboard/mouse except for moving the cursor around the screen, yet a newly opened window continued to flash in the window list. That time, killing the java process seemed to fix the problem. I'm not sure what's going on.

Not too long ago, I was playing Sauerbraten and it suddenly froze. I know that could be an entirely different issues, but I noticed the same entries in the log I usually see before the session locks up too. Here's the recurring part that worries me:

```
Sep  2 13:41:09 omega kernel: [ 6420.971456] warning: many lost ticks.
Sep  2 13:41:09 omega kernel: [ 6420.971459] Your time source seems to be instable or some driver is hogging interupts
Sep  2 13:41:09 omega kernel: [ 6420.971467] rip default_idle+0x29/0x50
Sep  2 13:55:12 omega -- MARK --
...
Sep  2 22:55:18 omega -- MARK --
Sep  2 23:05:15 omega syslogd 1.4.1#20ubuntu4: restart.
```

It's the warning about the lost ticks and instable time source that almost always show up after a lock up. I don't get it. Any ideas what the problem might be?

Thanks!

---

