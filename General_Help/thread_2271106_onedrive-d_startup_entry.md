---
title: "onedrive-d startup entry"
date: 2015-03-27
forum: General Help
---

### Post by capemayal on 2015-03-27
14.10

I have installed onedrive-d and can execute from terminal.  Sync is performed as expected.

I would like to add a entry to startup applications.

I've made every entry I could think of, and rebooted between each.

Upon executing sudo onedrive-d status, the result is onedrive-d not running.

Can anyone provide the entry for the startup application?

Thanks in advance,
Al



Ubuntu 14.10

---

### Post by slickymaster on 2015-03-27
Have you tried [this way]("http://www.howtogeek.com/189995/?PageSpeed=noscript").

---

### Post by capemayal on 2015-03-27
Thanks for your quick response.

I should have noted that I did try the startup applications.

I think the problem is with the direction to the path.

In terminal the command is sudo onedrive- start

It's not a necessary startup command, but just makes it easier.  If I don't remember to start from the terminal, which I'm prone to do, then things don't sync.

Al

---

### Post by slickymaster on 2015-03-27
> **capemayal said:**
> Thanks for your quick response.

I should have noted that I did try the startup applications.

I think the problem is with the direction to the path.

In terminal the command is sudo onedrive- start

It's not a necessary startup command, but just makes it easier.  If I don't remember to start from the terminal, which I'm prone to do, then things don't sync.

Al
Why are you starting it with sudo? From [https://github.com/xybu/onedrive-d](https://github.com/xybu/onedrive-d)```
# Run onedrive-d
# start as a daemon
onedrive-d start
# or start as a regular process
onedrive-d start --debug
```

---

