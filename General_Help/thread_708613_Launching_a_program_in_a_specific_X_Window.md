---
title: "Launching a program in a specific X Window?"
date: 2008-02-26
forum: General Help
---

### Post by yochaigal on 2008-02-26
Hello. I have two screens. When Gutsy 32-bit loads, I need it to always launch gthumb slideshow (or any equivalent) in one window, and then google earth in the other.

Now, google earth is easy. It remembers the last X window it was in, and launches there every time.

The problem is the slideshow. gthumb always launches in the first X window, but randomly (5 out of every 10 times) the slideshow feature will launch in X window 2, effectively covering google earth.
I am launching it with gthumb -s -f
Sometimes I run just gthumb -s
I've installed devilspie; It only works for workspaces not X screens. I was thinking that maybe if I could tie a desktop workspace to an X screen it might work.
I think the problem is that gthumb always opens in the right workspace, but the child window (the slideshow) just does random things----

Any ideas?

thanks

---

### Post by jocko on 2008-02-26
> **yochaigal said:**
> Hello. I have two screens. When Gutsy 32-bit loads, I need it to always launch gthumb slideshow (or any equivalent) in one window, and then google earth in the other.

Now, google earth is easy. It remembers the last X window it was in, and launches there every time.

The problem is the slideshow. gthumb always launches in the first X window, but randomly (5 out of every 10 times) the slideshow feature will launch in X window 2, effectively covering google earth.
I am launching it with gthumb -s -f
Sometimes I run just gthumb -s
I've installed devilspie; It only works for workspaces not X screens. I was thinking that maybe if I could tie a desktop workspace to an X screen it might work.
I think the problem is that gthumb always opens in the right workspace, but the child window (the slideshow) just does random things----

Any ideas?

thanks

try this:
```
DISPLAY=:0.0 gthumb -s -f
```
or:
```
DISPLAY=:0.1 gthumb -s -f
```
or:
```
DISPLAY=:1.0 gthumb -s -f
```

---

### Post by yochaigal on 2008-02-26
Wow!

You know I saw those options under the gthumb help arguments list, but I always assumed they had to go after the gthumb command, I was pulling my hair out trying "gthumb -s -f --display =" and "gthumb -s -f --screen ="
Thanks!

---

