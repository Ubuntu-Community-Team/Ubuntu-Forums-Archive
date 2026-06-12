---
title: "Compiler Installation Problem"
date: 2005-10-18
forum: General Help
---

### Post by xtacocorex on 2005-10-18
Yesterday I put Breezy on my new harddrive for my laptop since the old one crashed on Sunday. I was running Hoary, but since I got the new drive I figured I'd install Breezy.

I'm having a problem though, I'm trying to install the compilers and I keep getting dependency like problems saying that stuff won't install because something is there that is needed (libstdc++6 for example). I find it odd that if it is dependent on that library and the library is installed, why can't it install what I need.

I did uncomment all repos in my /etc/apt/sources.list file except for back-ports. 

If I remove libsdtc++6, it wants to remove pretty much everything from the system, including apt which is needed, but with it removed, I would be able to install. I had to take this route with amaroK to get certain arts support in there.

I normally would be able to figure it out, but I don't really have the time due to school and needing a working machine asap. 

Any ideas?
Thanks for any and all help.

---

### Post by thumper on 2005-10-18
What exactly are you trying to install?

The compilers?  Have you just tried the package build-essential?

---

### Post by xtacocorex on 2005-10-18
I tried build-essential this morning, same result. When I'm able to use my computer, I'll post the error message.

I also read that the default sources.list is a little off, so I'm going to correct that and see if it works.

---

### Post by xtacocorex on 2005-10-18
Fixed with the repository listing at: [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

