---
title: "Another Thread - Accessing Email this time"
date: 2006-10-09
forum: General Help
---

### Post by puppy on 2006-10-09
Hi folks, I'm having problems accessing my email.

For about the last two weeks, neither Thunderbird or Evolution will retrieve mail from my email service (via POP) even though they are both configured correctly. The email service at the other end just "times out"... I have confirmed with my email provider that there are no problems at their end, and I can acccess the email via a web interface, but not using my email client. The pop server is accessed via the normal port 110, and Firestarter has default settings, as does my router.

Can anyone advise what might be going wrong? Please let me know if I can provide any further information to help diagnose the problem

Many thanks

---

### Post by foolsh on 2006-10-09
I use ThunderBird along with webmail extentions to check my hotmail, yahoo, and ISP provided email accounts. However hotmail and yahoo can't be checked unless ThunderBird is ran as root. i.e. gksudo thunderbird. I only asume this has something to do with user programs accessing the internal ip address "127.0.0.1".
Could this be something similar?
I would try it anyways to be sure.
goodluck!

---

### Post by puppy on 2006-10-09
It isn't either yahoo or hotmail - it's a regular pop account. I've tried running it with 

sudo mozilla-thundebird

And it continues to timeout when trying to retrieve the first message...

[EDIT] I seem to have another weird problem (which might be related I guess) when I try to access  [www.digg.com](www.digg.com) it connects but just sits there "waiting for digg.com" without loading anything... strangely this doesn't seem to be affecting any of the other websites I regularly visit...

---

### Post by puppy on 2006-10-10
I love *potentially* solving my own problems.

I didn't mention this earlier because I didn't think it was relevant but two weeks ago I swapped over to a wireless connection. Now it appears that having a network interface with an "MTU" that is too high can sometimes cause certain websites to time out and can also cause issues when accessing email when the first email to be grabbed is very large... there are timeouts etc etc

I suspect that the MTU on my wireless card is set to the maximum, 1500, and I'm going to start tuning it down using ifconfig, taking the interface down, bringing it up, and then seeing if that solves the problem. I will report back with my findings...

---

### Post by puppy on 2006-10-12
OK I have sorted it myself :p   It was the MTU setting - by a process of trial and error I have discovered that my wireless card will not talk to the router properly if it is set any higher than an MTU value of 1420 (it was previously set at the default of 1500)

---

### Post by PriceChild on 2006-10-12
Has this solved your email problem as well as digg? If so pm me and i will mark this thread as solved.

---

### Post by puppy on 2006-10-12
It has sorted all the issues I was having fortunately - it's seems to be quite a rare problem, but terribly frustrating if you don't know what's causing it!

---

### Post by AmandaKerik on 2007-02-01
> **foolsh said:**
> I use ThunderBird along with webmail extentions to check my hotmail, yahoo, and ISP provided email accounts. However hotmail and yahoo can't be checked unless ThunderBird is ran as root. i.e. gksudo thunderbird. I only asume this has something to do with user programs accessing the internal ip address "127.0.0.1".
Could this be something similar?
I would try it anyways to be sure.
goodluck!

I've heard this happens with the lower level port numbers - something about priviledges or reservations.

Can you shift the port numbers up into the 1000's? I have my e-mail's set as 1111 and 1112 and I don't need to be sudo to run TB.

It's something to try, anyways...
Amanda

---

