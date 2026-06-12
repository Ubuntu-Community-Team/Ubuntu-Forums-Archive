---
title: "How do I find the current screen brightness on the command line (X.Org)?"
date: 2024-01-14
forum: General Help
---

### Post by Paddy Landau on 2024-01-14
I have searched this query, but the only results that I get are how to *set* the brightness. I already know how to do that with xrandr.
```
xrandr --output [monitor] --brightness 0.5
```
What I want to know is how to *get* the current brightness from the command line (in Bash).

I'm using Ubuntu 22.04 in X.Org (not Wayland) mode.

Thank you

---

### Post by dragonfly41 on 2024-01-14
You might have missed my post#13 in your previous thread.
[https://ubuntuforums.org/showthread.php?t=2494260&page=2](https://ubuntuforums.org/showthread.php?t=2494260&page=2)


But I continued my Phind.com session and received this answer to my supplementary queries/prompts. 
 
There is method in crafting prompts - search &#8220;prompt engineering&#8221; to reduce risks of &#8220;hallucinations&#8221;.


My opening prompt:


> In Ubuntu 22.04 Xorg session how can xcalib be used to modify screen brightness by bash script in command line?



My follow up prompt:
> How can current brightness level be monitored via command line?
which returned this (plus more expansion and links)


> Here's an example of how you can do this:
> [COLOR=#07070d]
current_brightness=$(xrandr --verbose | [/COLOR][COLOR=#0e0573]grep[/COLOR][COLOR=#07070d] -i brightness | [/COLOR][COLOR=#0e0573]awk[/COLOR][COLOR=#50fa7b]'{print $2}'[/COLOR][COLOR=#07070d])[/COLOR]
[COLOR=#0e0573]echo[/COLOR] [COLOR=#07070d]$current_brightness[/COLOR]

---

### Post by Paddy Landau on 2024-01-14
> **dragonfly41 said:**
> You might have missed my post#13 in your previous thread.
I did! Thank you. I'll be going over that thread from the beginning!

I've marked this thread as solved.

---

