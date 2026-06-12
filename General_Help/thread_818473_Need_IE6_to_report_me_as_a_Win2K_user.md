---
title: "Need IE6 to report me as a Win2K user"
date: 2008-06-04
forum: General Help
---

### Post by puredoxyk on 2008-06-04
Okay...this sucks, and trust me, I'm as angry about it as you are.  (Probably more, since I've been wrestling with it all morning.)

After 2.5 years of online school, I have my first Completely B.S. Software to deal with, courtesy of a professor who seems to think using as much proprietary software as freaking possible is fun.  The software uses Shockwave, so I had to install IE6 for Linux, which I've never had to do before (and zow, do I miss Firefox with every second I spend on that thing).

BUT, even though I'm now running IE6, I STILL can't access the stupid page, because the whole site locks me out (I'm not kidding) because my computer doesn't run a "supported operating system" (nope, not kidding -- it really won't even let me into the site).

Now, **I know how to spoof the user data in Firefox, and I know how to do it in IE running on Windows.  But how do I do it in IE running on Wine?**

Anybody?  My grades hang in the balance, because I'm sure you can imagine how interested this company is in supporting my system...

(The company, just in case any of you are college professors, is Cengage, and their entire website and software suite is bloated, expensive, sloppily-coded CRAP.  I kinda hope they die in a fire, after what they've put me through this week...)

---

### Post by KingTermite on 2008-06-04
I don't know how to spoof it, but you could always use Virtualbox or VMWare instead of Wine (assuming you have Windows software).

---

### Post by prince_niceguy on 2008-06-04
From the ies4linux site.

5) Make ~/.ies4linux/ie6 simulate Windows XP instead of Windows 98

update: many people asked, so here it is: run WINEPREFIX=~/.ies4linux/ie6 winecfg and change Windows 98 to Windows XP.

---

### Post by bingoUV on 2008-06-04
I hear tatanka, the ies4linux creator is very helpful. Contact him.

If you mention how you do it in IE running on windows, some other wine expert here might tell you how to do it wine.

---

### Post by puredoxyk on 2008-06-04
> **prince_niceguy said:**
> From the ies4linux site.

5) Make ~/.ies4linux/ie6 simulate Windows XP instead of Windows 98

update: many people asked, so here it is: run WINEPREFIX=~/.ies4linux/ie6 winecfg and change Windows 98 to Windows XP.

Thank you for that solution!  It didn't work, but only because setting IE to report as 2000 or XP then caused some kind of error that made the site not work -- probably, again, the site's fault.

I've given up for now, since I spent 4 hours on this already today, and at this point I'm just ready to borrow somebody's stupid Windows box and be done with it.  But thank you for the answers, and I'd say this one seemed to be the best answer to my original questions.

Oh, P.S.  DIE IN A FIRE, CENGAGE!

Ahem.  Thanks.

---

### Post by kellemes on 2008-06-04
> **puredoxyk said:**
> 
Oh, P.S.  DIE IN A FIRE, CENGAGE!

I sense anger ;-)

---

