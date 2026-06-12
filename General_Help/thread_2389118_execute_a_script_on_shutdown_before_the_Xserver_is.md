---
title: "execute a script on shutdown before the Xserver is terminated"
date: 2018-04-11
forum: General Help
---

### Post by Wolfhart on 2018-04-11
Hello,

I am using Ubuntu 16.04. I am trying to solve the problem that Chromium tells me on every startup that it "didn't shut down correctly". There is a long thread about this issue here:

[https://ubuntuforums.org/showthread.php?t=1453302](https://ubuntuforums.org/showthread.php?t=1453302)

But the solution proposed there, which is to put the command ```
kill -TERM $(pgrep chromium)
``` in the script /sbin/shutdown does not work in my case. Another proposed solution, namely to put the said command in a script in /etc/rc0.d does not work either. I guess, from what I have read in other threads, that the reason why these solutions don't work is that the command needs to be executed before the Xserver is terminated (given that Chromium is killed when the Xserver is terminated), but in the proposed solutions it is executed afterwards. The command in itself appears to work: When I execute it manually and then shutdown and restart, Chromium does not produce the "didn't shut down correctly" message. So my question is this: Is there a way to execute a script on shutdown before the Xserver is terminated?

Thanks in advance for your help!

---

### Post by Wolfhart on 2018-04-18
There has been no reply. Is what I would like to do impossible? Or is this not the appropriate forum?

---

### Post by cruzer001 on 2018-04-18
I did not read through your link so may have been mention.

Settings->Advanced Settings->System-> uncheck

[https://superuser.com/questions/873381/how-can-i-disable-the-chromium-didn-t-shut-down-correctly-message-when-my-brow](https://superuser.com/questions/873381/how-can-i-disable-the-chromium-didn-t-shut-down-correctly-message-when-my-brow)

---

### Post by Wolfhart on 2018-04-19
Thank you, cruzer, for the reply. But the solution you propose does not work either in my case. I think that what I need is what I said in the original post, namely to have the command
```
 kill -TERM $(pgrep chromium) 
``` be executed on shutdown *before anything else happens*. Is that possible? I.e., is there a way to affect the shutdown process at the very beginning?

---

