---
title: "Email application madness"
date: 2007-11-06
forum: General Help
---

### Post by rosslaird on 2007-11-06
I was a fan of Thunderbird until it started to crash routinely in Gutsy. And I'm worried about the recent changes in the design team for TB. So, for now, I have decided to switch to another email application until things get sorted out with TB or another app becomes the clear winner in this category. But I have to say that so far I'm shocked at the continuing low quality of email applications. I've used most of them over the years, and as I look at them again now I see that they have not imporved much:

Evolution crashes, and it eats the odd IMAP mail.

Kmail just does weird stuff with my imap account and also deletes emails without warning (and we're talking full imap delete, not just hide from view like in Evo).

Sylpheed (now called Claws-mail), though otherwise excellent, hangs if I leave it on overnight.

Gnus (under emacs) actually works very well, but fails to notice new email as fast as the other apps (it seems not to notice the new emails for a long time, even when set to check every 10 minutes).

Mutt, of course, just works. Always has. But I don't want to spend all day in a terminal.

And the Opera mail client works too. No problems of any kind so far.

So why are the the applications that are least used by regular (i.e. non-technical) users and least well-known (mutt and opera mail, respectively)  the best applications? That seems very odd.

And why, after years and years of development, are kmail and evolution still so poor? Email is a keystone application on any desktop.

Ross

---

### Post by x1a4 on 2007-11-06
Try Balsa (it's in the repos).

---

### Post by rosslaird on 2007-11-06
It's been a while since I tried balsa, but I do remember it (way back when it was a gtk 1 application).
I'll take another look.

---

### Post by sstusick on 2007-11-06
I gave up on email clients and now I just sign into the website to check my email.

---

### Post by rosslaird on 2007-11-06
I have used the squirrelmail interface quite a bit, and also the roundcube webmail browser interface. Both are installed on my website. But heck, should we have to go that far? I mean really, squirrelmail works well, but it's not exactly robust.

Roundcube is pretty cool...


btw: Balsa seems to work well -- except that I can't figure out how to save sent messages to my imap Sent folder on the server. (And selecting Remove Duplicates causes balsa to crash.)

R.

---

### Post by x1a4 on 2007-11-06
> **rosslaird said:**
> I mean really, squirrelmail works well, but it's not exactly robust.

Have you tried Horde? 

> btw: Balsa seems to work well -- except that I can't figure out how to save sent messages to my imap Sent folder on the server.

Settings > Preferences > Mail Options > Outgoing

>  (And selecting Remove Duplicates causes balsa to crash.)

Really?  What version do you have?  I use 2.3.13 from the feisty repositories and it works flawlessly.

---

### Post by rosslaird on 2007-11-06
> **x1a4 said:**
> Settings > Preferences > Mail Options > Outgoing
.

The above only allows the saving of sent messages, not the location of the saving. 

I'm using 2.3.17.

R.

---

### Post by Ux64 on 2007-11-07
I would use Thunderbird. But there is only one annoying problem with it. It won't spool emails to be sent in background. I really hate that SENDING window. I know I can do other things. But when I process over 100 emails daily, and reply to most of those. I want it to close email being send immediately and I can continue my work without extra clicks.

Just my comments.

Right now I'm using Evolution. I'm not too happy with it. It misses a quite bunch of feature. But it sends emails perfectly.

---

### Post by andrew.46 on 2007-11-10
Hi,

 So why not just stick with mutt? I know you mentioned that you did not really want a console app for mail but mutt is an amazingly solid piece of software and is under constant development. New development version released November 1st btw.

                                 Andrew

---

### Post by viking777 on 2007-11-10
Have you tried this:

 [http://kshowmail.sourceforge.net/](http://kshowmail.sourceforge.net/)

I don't know how it works with Gnome because I only use KDE and I do know that if you have Beryl or Compiz as a window manager it works but behaves strangely, but on a plain kde desktop it is superb and has the benefit of getting rid of all the junk mail before you download it.

Of course when you want to download some mail you are still going to have to use Tbird or some such, so I have probably just wasted my time typing this!!

Hey ho!!

---

### Post by rosslaird on 2007-11-10
> **andrew.46 said:**
> Hi,

 So why not just stick with mutt?
                                 Andrew

Typically I do use mutt at various times. It's the most stable and feature-ful of all the mail applications. But you know, sometimes a GUI is nice. Copying and pasting is a little easier in the GUI, as is the opening of links and so on. And a GUI is integrated more with the desktop. Claws-mail is the closest thing on the desktop to mutt, in my experience. If only there was something called mutt-gtk!

Ross

---

