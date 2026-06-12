---
title: "What are some good performance tuners?"
date: 2008-01-01
forum: General Help
---

### Post by agim on 2008-01-01
What are some solid ways to increase performance. I have followed the bootup procedures on these two posts:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

I also have switched to the Xubuntu desktop for performance reasons, even though I own a new computer.

But I haven't been able to find anything else. If someone could point me to a good tutorial or two (or ten) I would really appreciate it.

---

### Post by oldos2er on 2008-01-01
I've tried this: [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

 These tweaks work for me on Gutsy too.

---

### Post by ~LoKe on 2008-01-01
> **oldos2er said:**
> I've tried this: [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

 These tweaks work for me on Gutsy too.

I wouldn't trust Softpedia with anything serious....

---

### Post by oldos2er on 2008-01-02
> **~LoKe said:**
> I wouldn't trust Softpedia with anything serious....

 I don't understand. I've used these tweaks for months now, with no ill effects I'm aware of. Basically all they consist of is setting swappiness to a low number, enabling writeback in the file system, and disabling IPv6.

---

### Post by ~LoKe on 2008-01-02
> **oldos2er said:**
> I don't understand. I've used these tweaks for months now, with no ill effects I'm aware of. Basically all they consist of is setting swappiness to a low number, enabling writeback in the file system, and disabling IPv6.

For starters, they suggested opening graphical applications with sudo rather than gksu/kdesu.  I stopped there.  But yes, those tweaks are legit but I'd prefer it if people followed them from a guide that made mention of the risks.

---

### Post by oldos2er on 2008-01-02
Ok, good point about gksu. I hadn't actually looked at that article for awhile.

 I know I made a backup of each file i altered before I altered it--I assume anyone who's going to tweak their system would do the same. But that's never mentioned in the article.

---

### Post by ~LoKe on 2008-01-02
> **oldos2er said:**
>  I know I made a backup of each file i altered before I altered it--I assume anyone who's going to tweak their system would do the same. But that's never mentioned in the article.
Yeah, it's different for experienced users.  You'd be pretty much aware of what the changes are, and how to restore them.  A beginner might be clueless, not know how to restore a backup, reverse the steps, or, hell, perhaps they might even make a typo. ;)

---

