---
title: "Ubuntu log in screen really slow"
date: 2018-09-02
forum: General Help
---

### Post by festeringdoubt on 2018-09-02
Hi, I just installed Ubuntu 18.04 lts onto a dell r510 server, specifically onto 2 Kingston 240gb ssds in raid 1, the install went fine, but the login screen is incredibly slow, as I can press a button and it takes a couple of seconds for it to register, it isn't lagging as far as I know, if it helps I could post a video of it in action.

The strange thing is that once I have logged in everything is fine, even the lock screen. Any help would be greatly appreciated

---

### Post by sgian on 2018-09-02
Some terminal tools to help analyze slow boot time...
```

systemd-analyze time
systemd-analyze blame

```

---

### Post by alecz20 on 2018-10-13
Same with a Dell PowerEdge T610.

I think it has something to do with the Matrox Video Adapter and the driver is not loaded properly.

Though it made progress on desktops and laptops, too bad Ubuntu doesn't work well even on server grade hardware (unless you use Ubuntu Server of course)

---

