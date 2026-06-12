---
title: "Virtualbox not following Dark theme and font"
date: 2017-12-06
forum: General Help
---

### Post by ardouronerous on 2017-12-06
I'm using a dark theme with Xubuntu 16.04, and Virtualbox used to follow the theme's colors and my font, but now, when I opened Virtualbox, it's all white;
[ATTACH=CONFIG]277753[/ATTACH]
What could be the cause of this?

I've already tried to uninstall and reinstall Virtualbox, that didn't help.

---

### Post by ajgreeny on 2017-12-06
No proper solution but I am wondering if the fact the VBox is a qt application instead of gtk has anything to do with this.
I have no reason to think it might but it's just me thinking out loud and I may be spouting total rubbish.

---

### Post by vasa1 on 2017-12-06
> **ardouronerous said:**
> I'm using a dark theme with Xubuntu 16.04, and Virtualbox used to follow the theme's colors and my font, but now, when I opened Virtualbox, ...
So Vbox suddenly stopped looking the way it used to? You could look at recent updates to your system. There maybe some clue there.

---

### Post by ardouronerous on 2017-12-06
I checked my history.logs, and according to them, I installed Virtualbox last August 2017 and it was version 5.0.40, and since I reinstalled yesterday, the version is still 5.0.40.

So from August to November, Virtualbox has been following my theme's colors and my font, something happened to make it stop doing that.

---

### Post by ardouronerous on 2017-12-06
I've found a solution, following this: [URL="https://www.reddit.com/r/archlinux/comments/4t4c7p/virtualbox_51_is_in_community_and_it_doesnt_use/#bottom-comments"]https://www.reddit.com/r/archlinux/comments/4t4c7p/virtualbox_51_is_in_community_and_it_doesnt_use/#bottom-comments

[/URL]Start Menu -> Settings -> Menu Editor -> System -> Virtualbox.

Copy and paste this to Command and then click on Save Launcher.
```
VirtualBox -style gtk %U
```

This causes Virtualbox to follow your GTK theme and font.

Why did this happen now though?

---

