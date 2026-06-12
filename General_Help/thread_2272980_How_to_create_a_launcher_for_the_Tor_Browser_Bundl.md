---
title: "How to create a launcher for the Tor Browser Bundle?"
date: 2015-04-09
forum: General Help
---

### Post by klundermann on 2015-04-09
I've been using the Tor Browser Bundle (TBB) for a long time, but I've never installed it.  Now I'd like to install it and create a desktop launcher for it.

If I understand correctly, I should extract the TBB package to a location like /usr/local/bin and then create a launcher that links to the start-tor-browser script.  The question is, how do I create a launcher?  I found [this YouTube video]("https://www.youtube.com/watch?annotation_id=annotation_443450&feature=iv&src_vid=6UBb3BTthJc&v=Pw15EOjSFbM"), but it relies on a tool -- Create Launcher -- which I don't find in the Ubuntu Software Center.  How should I attack this?

---

### Post by tjiagoM on 2015-04-10
Maybe this official link could help you: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by klundermann on 2015-04-11
Thanks, tiago-manuel -- that was exactly the hint that I needed!

Let me mention one trick I learned, in case it helps somebody else.  Within the .desktop that defines the launcher, I had no luck specifying an icon with ```
Icon=~/my.icon.directory/my.icon
```  When I gave the absolulte path of my home directory instead of using ~, I got the icon I wanted.

---

