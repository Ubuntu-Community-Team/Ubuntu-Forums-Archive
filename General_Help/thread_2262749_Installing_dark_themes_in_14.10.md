---
title: "Installing dark themes in 14.10"
date: 2015-01-27
forum: General Help
---

### Post by Cleaver on 2015-01-27
Hello everyone,

I had no problems installing dark themes in 14.04, but now that I've upgraded to 14.10, I get this message when trying to do so via terminal:
 E: ```
Unable to locate package zen-suite
```

With other packages, it displays that, with [package name] in place of "zen-suite."

Here's the tutorial I was using to get those commands, and which I've used successfully for months up until now(code for installing them is shown in the description when "show more" is clicked.)  

[https://www.youtube.com/watch?v=kq6d5KEdXB8](https://www.youtube.com/watch?v=kq6d5KEdXB8)

Any idea why it's doing this now? I'm unaware of this happening in other flavors such as Mint 17.  Thanks!

---

### Post by raptir on 2015-01-27
[https://launchpad.net/~noobslab/+archive/ubuntu/themes?field.series_filter=utopic](https://launchpad.net/~noobslab/+archive/ubuntu/themes?field.series_filter=utopic)

The PPA that the tutorial tells you to add does not have that package for Utopic (14.10). That said, there's not much of a need to have a PPA for themes. If you download the theme itself from the source you can install it by dropping GTK/window manager themes in ~/.themes and icon packs in ~/.icons.

---

