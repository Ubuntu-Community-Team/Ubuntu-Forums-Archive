---
title: "Chrome displaying all weird, and so unable to use it"
date: 2023-05-26
forum: General Help
---

### Post by Paddy Landau on 2023-05-26
[B]

EDIT: I came back to my computer a few hours later. There were some new pending updates, which I ran. Now everything is working. I have no idea why.
[/B]


I wish that one day, I'd start the day and nothing would go wrong!

**This morning's problem:**

I started the computer as normal, and Chrome isn't displaying its contents properly. This is seriously affecting every page that I visit. See the two screenshots for examples. Even the settings page itself is unusable.

The pages are working correctly &#8212; as I move my mouse around, I see the correct tooltips, and clicking where the links should be correctly changes pages. But I still can't see what's going on.

**What I've tested:**

[LIST]
[*]Does it work on a different computer? Yes, it does! So, it's just this computer where I have a problem.
[/LIST]

[LIST]
[*]Does this affect all profiles (I have a few profiles on Chrome)? Yes, it does, so it's not just this profile.
[/LIST]

[LIST]
[*]Does it happen when I disable extensions? I start with this command:
```
google-chrome-stable --disable-extensions
```
Yes, it does, so it's not an extension causing the problem.
[/LIST]

[LIST]
[*]Does another browser (e.g. Firefox) work? Yes, it does, so it's just Chrome.
[/LIST]

[LIST]
[*]Is my system full? The drive still has 400 Gb free; RAM still has 12 Gb free; the CPUs are all running normally (low).
[/LIST]

** What I've done to try to fix this:**

[LIST]
[*]Cleared all caches (as Settings was unreadable, I had to manually do this):
```
rm --recursive ~/.cache/google-chrome/Default/*
rm --recursive ~/.cache/google-chrome/'Profile '?/*
```
[/LIST]

[LIST]
[*]Uninstalled Chrome:
```
sudo apt remove --purge google-chrome-stable chrome-gnome-shell
```
[/LIST]

[LIST]
[*]Reinstalled chrome-gnome-shell (from the standard repositories) and google-chrome-stable (directly from [Google's website]("https://www.google.com/intl/en_uk/chrome/")).
[/LIST]

[LIST]
[*]Restarted the computer. This worked, a little &#8212; the pages are now mainly readable, but there are still problems, e.g. some areas flash; most images display nothing; text overlays other areas. (I'm writing this post on Firefox.)
[/LIST]

** More information:**

[LIST]
[*]Ubuntu 22.04, running X.Org (not Wayland)
[*]The system is fully updated
[/LIST]

What can you suggest for me, please?

---

