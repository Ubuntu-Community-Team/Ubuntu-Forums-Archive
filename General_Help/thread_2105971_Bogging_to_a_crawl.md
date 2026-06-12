---
title: "Bogging to a crawl"
date: 2013-01-17
forum: General Help
---

### Post by p110011 on 2013-01-17
I have an old gforce 3-a mobo/AMD Sempron 3000 @ 1.2mhz 1G ddr400 memory and an nvidia 256Mb agp graphics card running Ubuntu 12.4.1 32bit

Problem, is after a while, (mostly looking at pic heavy sites like craiglist auto section) my computer gets really slow. Even after closing all apps, reactions like mouse clicks are about 5 seconds delay time.

I can log out of Ubuntu and it will be back to normal. I'm not sure what other info that I should put up here that would be relevant to this, but any help will be appreciated.

---

### Post by dabl on 2013-01-17
When you next log in, open a console and enter "top".  Then just let that console run, and use another virtual desktop to do your browsing/video viewing.  Or you can minimize the console window, but if the response is getting so slow, you'd like to be able to immediately see what top shows as the busiest process.  That will give a clue where the bogging is happening.

---

### Post by p110011 on 2013-01-17
> **dabl said:**
> When you next log in, open a console and enter "top".  Then just let that console run, and use another virtual desktop to do your browsing/video viewing.  Or you can minimize the console window, but if the response is getting so slow, you'd like to be able to immediately see what top shows as the busiest process.  That will give a clue where the bogging is happening.

OK, I have used system monitor before (the gui app) and it never shows anything that is glaring or standing out. But I'll keep TOP up for now, thanks.

---

### Post by dabl on 2013-01-17
You'll see a lot more with top, and probably there's only one process (the one on "top") that is the cause of trouble.

---

### Post by p110011 on 2013-01-17
Makes sense, mostly xorg on top 31%, firefox, compiz, gnome-terminal

I'll keep it going

---

### Post by ManamiVixen on 2013-01-17
Could be a problem with Compiz. What's your memory usage like, as in, how much is being used during the slowdown. I have a hunch that it's a memory leak, such from compiz.

---

### Post by p110011 on 2013-01-17
> **ManamiVixen said:**
> Could be a problem with Compiz. What's your memory usage like, as in, how much is being used during the slowdown. I have a hunch that it's a memory leak, such from compiz.

It's at about .9G now

Any way to fix it?

---

### Post by d4m1r on 2013-01-17
It's bogging to a crawl because you are running a fairly recent OS on fairly ancient hardware. I'd recommend upgrading (especially your RAM), or switching to a more lightweight distro such as 12.04 with Xfce.

---

### Post by ManamiVixen on 2013-01-17
Unfortuantly, the only real fix is using an alternate DE for ubuntu like Lubuntu or Xubuntu. Unity doesn't run too well on old hardware. Also, Compiz tends to do what is happening to you after awhile and is only fixed, I believe, in Ubuntu 12.10. So upgrade (I suggest you don't) or use an alternate desktop. Cinnamon Desktop is nice.

---

### Post by p110011 on 2013-01-17
Yeah, I've been dragging this old thing around long enough, it got me here from 6.10 though

---

### Post by dabl on 2013-01-17
You're asking the old Nvidia AGP card to do things that are far beyond its design goals.  It can't run a heavy desktop like Unity, plus run compiz, plus support a modern browser with (undoubtedly) flash running.

It would probably be a tolerable machine for a "light" user if you set it up with LXDE or Bodhi (E17) or something like that.  But don't try running fullscreen videos or anything like that.

---

### Post by dannyboy79 on 2013-01-17
you will be better off with xubuntu or lubuntu, i have 2GB of DDRII ram and even sometimes Xubuntu with 7+ tabs open in Chrome, editing in Kdenlive, skype open, and listening to music sometimes chrome pages freeze up.

1GB sure meets the min requirements but you're pushing unity with compiz, that's just too much IMO

---

