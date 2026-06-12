---
title: "[SOLVED] Calculator gives incorrect results"
date: 2008-03-21
forum: General Help
---

### Post by gwoodruff on 2008-03-21
When using the standard calculator installed with Ubuntu I get incorrect results. 20+8%=20.08 (on multiple installs 32bit and 64). What am I missing?

Gary

---

### Post by Oldsoldier2003 on 2008-03-21
> **gwoodruff said:**
> When using the standard calculator installed with Ubuntu I get incorrect results. 20+8%=20.08 (on multiple installs 32bit and 64). What am I missing?

Gary

8% = .08

20 * 8%= 1.6

20 +(20*8%)= 21.6

---

### Post by newagelink on 2008-03-21
It appears you're misusing the % button. (Thanks for the post; I've never bothered with the Calculator before ...)

Switched it to scientific mode and I see the % button.

20+8% appears to actually be "20+1*8%", which would give you 20.08. E.g., entering "20*8%" gives you 8% of twenty. I'm guessing you're wanting "20+20*8%"?

I dunno. Sounds kind of silly; might as well just enter "20*+20.08", or rather "20*1.08"... but as the above user said, 8% acts as .08 ...

See also the Help menu: Help -> Help (F1) ... click "Usage". It describes the % there.

---

### Post by Oldsoldier2003 on 2008-03-21
> **newagelink said:**
> It appears you're misusing the % button. (Thanks for the post; I've never bothered with the Calculator before ...)

Switched it to scientific mode and I see the % button.

20+8% appears to actually be "20+1*8%", which would give you 20.08. E.g., entering "20*8%" gives you 8% of twenty. I'm guessing you're wanting "20+20*8%"?

I dunno. Sounds kind of silly; might as well just enter "20*+20.08", or rather "[COLOR="Red"]20*1.08[/COLOR]"... but as the above user said, 8% acts as .08 ...

yep thats the best way to do it.

---

### Post by gwoodruff on 2008-03-21
Last I knew 8% of 20 was 1.6  :)

---

### Post by newagelink on 2008-03-21
last i knew, 8% of 20 was your face.

---

### Post by ad_267 on 2008-03-21
> Last I knew 8% of 20 was 1.6

Yes but if you want 8% of 20 you would type 8% * 20

8% just by itself is 0.08

If you say 20 + 8%, you're saying 20 + 0.08

If you want 20 + 8% of 20, you need to enter "20 + 8% * 20"

---

### Post by gwoodruff on 2008-03-22
I have used this with many different calculators and this is the only one that has ever produced this result. try Kcalc for instance.

---

### Post by ad_267 on 2008-03-22
20 + 8% is definitely 20.08

Most actual calculators don't even have a % button anyways, all % means is divide by 100. Like people said before, the best way to add 8% of 20 to 20 is 20*1.08

---

### Post by gwoodruff on 2008-03-22
Actually most calculators do have a % key. All that I have used function as I have described, with the exception of this one! Pick up any other calculator or add one with package manager and give it a try.

---

### Post by ad_267 on 2008-03-22
Hmm, none of my calculators have a % key, and the % in the gnome calculator works how I would expect it to, but then I would never use a % key.

I guess you could just use a different calculator if this is a big deal

---

### Post by gwoodruff on 2008-03-22
I do use a different calculator. As this is an application that is packaged with Ubuntu I just thought someone would like to know this calculator produces a different result than any other calculator on the planet.

Gary

---

### Post by ad_267 on 2008-03-22
I just found this:
[https://answers.launchpad.net/ubuntu/+source/gcalctool/+question/19449](https://answers.launchpad.net/ubuntu/+source/gcalctool/+question/19449)

I'm an engineering student so I agree with the way the gnome calculator treats percentages, but I guess people used to financial calculators expect different behaviour. Someone had a good suggestion of changing the function of the % key when switched to financial mode, but then that could get confusing switching between modes and then getting different results.

---

### Post by chewearn on 2008-03-22
> **gwoodruff said:**
> As this is an application that is packaged with Ubuntu I just thought someone would like to know this calculator produces a different result than any other calculator on the planet.


That's a big sweeping statement you are making; I have to post to refute it.

If in doubt, ask Google:
[http://www.google.com/search?hl=en&q=20%2B8%25&btnG=Google+Search](http://www.google.com/search?hl=en&q=20%2B8%25&btnG=Google+Search)

---

### Post by ad_267 on 2008-03-22
OpenOffice Calc gives 20.08 too

---

### Post by gwoodruff on 2008-03-22
OK, I am willing to retract the "every other calculator on the planet" statement :smile:.The post on gcalctool says it all. I was just worried about the reputation of Linux and Ubuntu after seeing that you-tube video where they do this calc with a TI calculator and Ubuntu to claim it is a defective product. (They then do it with windows and the result matches the calc)
Thanks, Gary

---

### Post by Oldsoldier2003 on 2008-03-22
> **gwoodruff said:**
> Last I knew 8% of 20 was 1.6  :)

8% of 20 :) that means 8% times 20.... i think the whole thing about this thread is the OP wasn't thinking about order of operations and what exactly he was keying in.

---

### Post by ad_267 on 2008-03-22
Yes well 20 + 8% doesn't equal 21.6 in any mathematics or base that I've ever used, but apparently some calculators (financial calculators?) use this to mean 20 + 8%*20.

I think anyone who can see that 20 + 8% does not equal 21.6 would never use a % key on a calculator anyways, but maybe someone should post a reply on youtube showing that google says 20+8% equals 20.08 so obviously it is microsoft that has a flawed calculator.

---

### Post by gwoodruff on 2008-03-22
Try it on any just about any hardware calculator. I am fully aware of the order of operations. This is the way almost all non scientific or engineering calculators function, as I keep on saying pick one up and try it. I now fully understand why linux has a reputation that it is only for geeks. If I wanted to add .08 to something I would not use a % key for that operation, thus modern calculators understand that (x + y%) = (x*y%+x). Think of it as intuitive programming. If a $5 calculator from Walmart is capable of it, so should gcalctool (at the very least in financial mode). Did you guy's ever wonder WHY this is the most asked question about gcalctool.

---

### Post by Topsiho on 2008-03-22
20 + 8% is a little ambiguous, and therefore should be avoided..

The percentage sign means a division by 100, but to say that 8% means 8 divided by 100 is not so IMHO.
Usually percentages are used in the sense of 8% of 50, which means 8*50/100 = 4.

So I understand that some would argue that 20 + 8% = 20 + 8% of 20, which is 21.60

But I equally understand that others claim that it means 20 + 8/100 = 20.08

I really think therefore that to calculate 20 + 8% is just sheer nonsense, because of this ambiguity, and should produce an error message.

A calculator that produces a result from 20 + 8% is faulty and should not be used. One never knows what other erroneous results it produces.
Fortunately a Linux calculator can be mended after a bug report.

The thing to do is to send a bug report for any software calculator one finds that does not produce an error when asked to calculate this 20 + 8% thing ....

My two cents :)

Topsiho

---

