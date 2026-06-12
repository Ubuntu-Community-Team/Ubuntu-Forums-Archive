---
title: "Apt Dependency Errors &amp; What Do They Mean?"
date: 2016-09-02
forum: General Help
---

### Post by neu5eeCh on 2016-09-02
So, I get these gnomic, geek-speak, truncated error messages from Apt defying all norms of English syntax & order. Wondering exactly what they  mean, For example:

```
The following packages have unmet dependencies:
 digikam5 : Depends: libkf5kipi31.0.0 but it is not going to be installed
            Depends: libmarblewidget-qt5-23 (>= 4:15.12.0) but it is not going to be installed
            Recommends: kipi-plugins5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

So, let's start with line one: "but it is not going to be installed"

Does that mean. 

A.) Yeah, I *could*, if you pay the ransom. What have you got?
B.) No, and who's libkf5kipi31.0.0 anyway? Never met the guy. Try a different Repo.
C.) No. I just don't like you. Besides, you're an idiot. Why are you even trying to do this? It's just _not going to be installed_. Okay? Capish? Now go away.
D.) Yeah, I *could*, but it would be like cutting that the wrong wire. The whole thing goes ka-blewey. I can't do that, Dave.

And then this:

"Recommends: kipi-plugins5 but it is not going to be installed". What the freak does that mean?

A.)  Yeah, I totally know "kipi-plugins5". Got her address and phone number  too. She's really hot, right? I'd recommend her but she's not that into  you---you know? You and those loser dependencies you hang out  with. Sorry, mate, not going there.
B.) She would totally fix this for you, but she's on vacation right now. Spa. R&R. When she comes back, she's going to be *so totally* kipi-plugins5_**.1**_. Try giving her a call when she's back.
C.)  Yeah, she'd totally fix this for you, but she didn't leave a forwarding  address. Did you try the Debian repo? She's totally into Debian. Hangs out  there all the time.
D.) I'm sorry Dave, I can't do that.

"you have held broken packages." Held?

A.) Yeah, drop the gun. Just drop the gun. Let go of it. Once you stop holding it, we'll talk.
B.)  It's all those loser, bonehead, broke "friends" you hold onto. You  know? Lose them and she might consider a date. Just think about it. Give  me a call when you've grown up, got a job, a little income. You know  what I mean...
C.) Okay, you're a freakin' hoarder. I mean, have you  looked at the junk in your attic? Dude, it's all broken. I mean, look at  that broken toaster. You wanna' burn your house  down? Nah. Not happening. Get rid of he junk. Send me a  postcard.
D.) You have issues. I mean --- I don't know.  Packages. Monkeys on your back. I can't help you, dude. Go somewhere  else. There's a guy by the  name of "aptitude". Check him out. Don't tell him I sent you.
E.) Might I suggest a space-walk, Dave?

---

### Post by ajgreeny on 2016-09-02
*Thread moved to **General Help**.* which is more appropriate for the problem.

The cafe is for discussion subjects only and not for support queries.

---

### Post by ian-weisser on 2016-09-02
Quite simply, the error message means you have introduced a *version conflict*.
This sometimes happens when you introduce PPAs and other non-Ubuntu sources.
In Debian/Ubuntu, software version numbers matter. A lot. (Your know that already). You are trying to install software with a version that is *incompatible *with other software already on your system. So apt refuses and throws the error at you.

The package 'digikam5' is not in the Ubuntu repositories for any release of Ubuntu. So that's a good place to start when looking for version conflicts. What source are you getting it from?

---

### Post by neu5eeCh on 2016-09-03
Oh... my install is a scraggly mut. :) It's a 15.04 Kubuntu installation that was upgraded to 15.10, that was upgraded to 16.04, that was upgraded to Kubuntu Backports, that was upgraded to KDE Neon. 

And it all works beautifully -- love Linux.

I get apt error messages like these all the time. I was just wondering how to parse them. They seem to cover a variety of possibilities and their meaning is somewhat counter-intuitive.

---

### Post by mc4man on 2016-09-03
"is not going to be installed" generally is a depend issue, apt gives some info but up to you to explore further, ex.
apt-cache policy libkf5kipi31.0.0 or apt-cache policy libkf5kipi* 
If libkf5kipi31.0.0 was available then one would try to install it to see what the hangup is, if not available then that's why it won't be installed.

The 'referred by blah-blah' message is usually a source issue (update sources or enable a source) or possibly a version change.

The 'but whatever-xxxx is to be installed' usually means whatever-xxxx is already installed.

In some cases you'd find aptitude to be a bit more informative about package install issues

---

