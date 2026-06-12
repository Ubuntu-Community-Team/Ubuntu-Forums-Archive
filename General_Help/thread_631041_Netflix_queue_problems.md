---
title: "Netflix queue problems?"
date: 2007-12-04
forum: General Help
---

### Post by AusIV4 on 2007-12-04
Today I found out I had a gift subscription to Netflix that was about to expire, so I redeemed it and I'm now trying to add movies to my queue.

I have two computers, one with Gutsy, one with Feisty. In Firefox in Gutsy, clicking the "Add to Queue" link does nothing. If I run the Windows version of Firefox under Wine (something I keep on hand for just such occasions), it works fine. Strangely, it also works fine Feisty computer, which has the same version of Firefox as the Gutsy system.

The Gutsy computer is my main computer for web browsing, so it's rather annoying that I have to load up a different web browser to use Netflix. 

Has anyone else run into this? Does anyone have tips on how to fix it?

Thanks for any help.

---

### Post by aysiu on 2007-12-04
I've used Netflix in Firefox on Gutsy with no problems.

Can you try this on your Gutsy computer?

**Step 1**
Close all instances of Firefox

**Step 2**
Press Alt-F2 

**Step 3** 
Type ```
firefox --profilemanager
```

**Step 4**
Create a new test profile

**Step 5**
Try adding something to your queue in Netflix

If that works, it has nothing to do with Gutsy but has something to do with your Firefox profile. If that doesn't work, then there's something wrong with Gutsy.

---

### Post by AusIV4 on 2007-12-06
I'll try that next time I'm at that computer, but I did run: ```
firefox --safemode
``` then start it up without any extensions and I still had the problem.

---

### Post by AusIV4 on 2007-12-08
Creating a new profile didn't seem to help. I still can't add things to my queue with the Ubuntu native Firefox.

---

