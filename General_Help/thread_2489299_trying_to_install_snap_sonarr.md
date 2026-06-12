---
title: "trying to install snap sonarr"
date: 2023-07-25
forum: General Help
---

### Post by jgw on 2023-07-25
When I try to install I get:
error: cannot communicate with server: Post "http://localhost/v2/snaps/sonarr

I had just removed sonarr and, I suspect, I also deleted /snaps/sonarr

How do I get that back?

Thank you...............

---

### Post by Xian on 2023-07-25
Can you get snap to function with this command?

```
sudo systemctl restart snapd 
```

---

### Post by MAFoElffen on 2023-07-25
Trick question? Do not try and remove applications by deleting directories. You will most likely end up with a broken system caused by orphaned packages or broken dependencies. I cannot stress how dangerous this is as a practice.

You should have removed it via
```

sudo snap remove sonarr

```
How to fix that? Try the above command. If it simply fails, saying it is not there, install it via snaps. If not, post the error.

You started out asking how to connect to it... Which the Snap Page for it said:
> 
The web interface is accessible by default at [http://localhost:8989](http://localhost:8989)

If you go to the developer's website, there is also a support forum for it, and instructions for it's use and configuration...

---

### Post by jgw on 2023-07-26
Thank you for the help!

What I did was to first delete and then install and it was all fine.

Tlhanks again!

---

