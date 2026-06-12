---
title: "Can't run Windows applications under Wine, can't reinstall Wine"
date: 2007-11-30
forum: General Help
---

### Post by Eric Weir on 2007-11-30
I recently decided to give Wine a try. I installed two applications that I've used on Windows for years. Immediately after installing, both ran fine. After that, though, I couldn't get them to run from the menu. 

I decided to try the run window available in the  menu. [KDE] The result I got when I did that was that the folder  specified by the path "doesn't exist," even though I'd copied the path  from the Konqueror address bar. 

Subsequently, I uninstalled then reinstalled Wine. [Don't ask me why.] After installation, the only thing in the /.wine folder was two registry files. The Windows folders that Wine installs were missing. 

My guess now is that whatever's causing the first result is also preventing Wine from  being installed properly, i.e., something used in both processes thinks the needed folders don't exist.

But what could that be? Any ideas?

---

### Post by Eric Weir on 2007-11-30
> **Eric Weir said:**
> But what could that be? Any ideas?

An intuition that came to me as I was wrting the original post proved to be right. When I uninstalled Wine the /.wine folder was left in place. It occurred to me that maybe the system thinks that folder doesn't exist, so that anything that tries to access it will fail.

So I deleted the empty /.wine and reinstalled Wine. At first I thought it had failed again, but I checked /usr/bin to see if the Wine files that are installed there were there. They were, so I tried running Winefile from the terminal. It ran, and when I browsed it to where the missing folders should be, it created them. 

I'm feeling brilliant. [Nah, it was luck!] Anyway, it's solved.

Regards,

---

