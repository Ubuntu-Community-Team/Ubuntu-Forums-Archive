---
title: "Is it me, or are the repositories slow?"
date: 2008-02-13
forum: General Help
---

### Post by ibuclaw on 2008-02-13
Hi all, only a small question, but have we been experiencing slow speeds of most (if not all) the ubuntu servers over the past several days?

My son has found a sudden interest in Linux, and I thought I might be kind and get him a few stuff for him to play with, and upon download/updating my repository, I noticed that speeds are immensely slow.

Now I come from a Debian Etch background, and am used to seeing 400Kb/s UK servers streaming all my needs in minutes.

But, notibly, the average speed I've had so far is around the 3Kb/s speed, with some fluctuations up to 25Kb, but nothing impressive...

here's a screenshot... I've still got about 3 hours or so for the download to end, and I'm still on the first file.
[IMG]http://img138.imageshack.us/img138/4107/screenshothe4.png[/IMG]
I don't remember it being this bad...

post your thoughts, thank-you...

Iain

---

### Post by brennydoogles on 2008-02-13
Holy Crap that's slow! If you go to System -> Administration -> Software sources, you should be able to check an option to find a mirror... the problem could be that you are downloading from a server on a different continent!! If you are in the UK (which I think you said you were) then maybe you could get such poor speeds from a server in southeast asia or maybe south America. I hope this helps!!

---

### Post by Woodgar on 2008-02-15
I can't really help, but I can at least say that I am having the same problem.

I'm in the UK and my software source is set to "server for United Kingdom"  which is as it should be. My updates etc are downloading at sometimes less than 30kbs, and rarely get above 56kbs. In other words I'm downloading at the sort of speeds you would expect on a dial up account, even though I'm on cable.

If it helps, my ISP is Virgin/NTL and I'm on the 4M package.

---

### Post by taurus on 2008-02-15
> **Woodgar said:**
> I can't really help, but I can at least say that I am having the same problem.

I'm in the UK and my software source is set to "server for United Kingdom"  which is as it should be. My updates etc are downloading at sometimes less than 30kbs, and rarely get above 56kbs. In other words I'm downloading at the sort of speeds you would expect on a dial up account, even though I'm on cable.

If it helps, my ISP is Virgin/NTL and I'm on the 4M package.

Try switching to the Main Server to see if your download speed's increasing in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.

---

### Post by Woodgar on 2008-02-16
I had another look at the "software sources" option (system -> admin -> software sources) and rather than just pick the top level of "main server" or "server for uk" I took the "other" option.

In there I clicked on "select best server" and the app did its thing and pinged all the servers in the list and picked one for me with the best response time. In my case it ended up with ubuntu.positive-internet.com.

My downloads of updates/new packages are now maxing out my cable connection, so it's now going as fast as it ever will. :)

I know that this can be a temporary internet congestion thing, but maybe those experiencing similar slowdowns can get an equally positive outcome by letting the app select the best server for them as well.

---

### Post by PmDematagoda on 2008-02-16
I usually face these problems during the mid-day, I am not too sure myself but it may be due to the high magnitude of Ubuntu users using the repositories Sri Lanka(though I have never met anyone save a few, emphasis on few;)).

---

