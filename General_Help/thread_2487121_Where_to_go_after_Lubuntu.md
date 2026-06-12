---
title: "Where to go after Lubuntu?"
date: 2023-05-23
forum: General Help
---

### Post by ne29914 on 2023-05-23
I've now worked with Lubuntu for several years and been extremely happy with it, but I think it's time to part ways.
Too many bugs in newer versions, no real interest from the community, very limited support etc., but I'd like to stay in the Ubuntu world.

My demands are still the same: lightweight (I use older laptops) with a classical desktop.
From my own research, Mate and Xubuntu seem to fit best, though I tend towards Mate as it seems to have a larger user base.
What do you think?

(Sorry, I didn't find a suitable forum for this, I thought about the "OS Chat", but... moderator feel free to move this to where it's appropriate).

---

### Post by ian-weisser on 2023-05-23
> **ne29914 said:**
> Too many bugs in newer versions, no real interest from the community, very limited support etc.

I think the Lubuntu volunteers (who are very nice people) may be rather hurt that you seem to take their many years of volunteer labor for granted and disparage it as buggy and "limited support." Perhaps that's not what you meant.

Please recall that you and I are not Lubuntu *customers*. We are a *participants*. Any flavor is only as good as the participants make it.

If it has "too many bugs", then help triage those bugs.
If there is is "no real interest from the community", then help by showing interest.
If there is "very limited support", then help provide support.

Since all flavors of Ubuntu are free to try...try several.

---

### Post by Rex Bouwense on 2023-05-24
+ 1 @ ian-weisser.
I have used Lubuntu with the LXDE desktop and still have Lubuntu 22.04.2 with the  LXQT desktop environment on one of my computers.  While it is not as fast as the old Lubuntu and is not really suited for the really older computers it is very modern, robust,  and responsive.  I have found the volunteers responsive to problems and provide answers and solutions to problems and questions asked.  If you are unhappy and not satisfied you can do what has been suggested and try other flavors.  All seem to have a very dedicated group of volunteers who are seriously dedicated to maintaining their respective flavor.

---

### Post by ne29914 on 2023-05-24
@ian-weisser:
Rereading my post, I understand your response and accept that I come over as a "Karen" which was unintended. Perhaps my disillusion shines through.

But I'm certainly active, not as a programmer (that's outside my skills), but at least as a contributor/user trying to help where I can. You're welcome to scroll through my posts.

I was member of the discourse.lubuntu.me forum until a couple of other "superusers" found it appropriate to troll me, abuse me and call me names. I deleted my account.
I've reported bugs on Launchpad (a nightmare, took several days to figure it out with friendly help from users here). Result: nothing.
I've asked questions here without results (perhaps my headlines aren't sexy enough). Admittedly, my questions go beyond what can be read in the user manual for Lubuntu.

I've had great responses from one or two users with knowledge of Lubuntu.
However, disillusion, discouragement and frustration grows when every problem hits a brick wall.

So my question still stands: which lightweight distri with classical desktop has a user base large enough to command attention and receive resources?

---

### Post by guiverc on 2023-05-24
> **ne29914 said:**
> 
My demands are still the same: lightweight (I use older laptops) with a classical desktop.
From my own research, Mate and Xubuntu seem to fit best, though I tend towards Mate as it seems to have a larger user base.
What do you think?


I'll *skip* the Lubuntu stuff; except to say we (*Lubuntu*) do what we can with the *time* & *resources* & *skills* we have available to us; we're a small team.

My oldest box I use in QA is a 2005 HP, and I test other *flavors* too and not just Lubuntu.  I recently changed video card in that old 2005 HP because Lubuntu/LXQt started showing graphic glitches that had been experienced with GNOME/KDE for many (*six monthly*) cycles and as *nouveau* issues aren't the focus of my testing, the video card was starting to cost me time. Lubuntu was the second last *flavor* to be impacted (GNOME/KDE first, Budgie/MATE pretty soon after) & the only *flavor* unimpacted thus far is still Xfce/Xubuntu.

In my QA *testing*, and even my use, I've found Xubuntu/XFCE *lighter* than Ubuntu-MATE/MATE. On newer (*or better resourced really*) hardware the difference is *moot* (*I'd never pick it if I wasn't looking for what shows on older/slower systems*), but on older or limited devices its noticeable.  I've found Xfce lighter & believe it's the lighter of the two (*assuming you're using GTK apps**; at least those I use*).

- LXQt is a Qt5 system.
- MATE & Xfce are GTK3, thus will be better if using GTK3 apps, but neither will be as efficient if using Qt5 apps.
- KDE is also a Qt5 system, whilst it needs KF5 (KDE Frameworks 5) meaning it'll use more resources than LXQt, it'll be lighter than MATE or Xfce if using Qt5 apps in my experience. Kubuntu offers KDE Plasma.

Myself - I see all of Ubuntu, Lubuntu, Kubuntu, Xubuntu Ubuntu-MATE & other *flavors* as Ubuntu systems anyway; and most problems one has also exist with the others (*on the rare instance where this doesn't occur - you've got a HUGE clue as to what the problem is & what needs to be resolved, given how common they all are**; alas I still don't know why Xfce doesn't trigger the nouveau issues as readily*).

---

### Post by guiverc on 2023-05-24
> **ne29914 said:**
> 
But I'm certainly active, not as a programmer (that's outside my skills), but at least as a contributor/user trying to help where I can. You're welcome to scroll through my posts.

I was member of the discourse.lubuntu.me forum until a couple of other "superusers" found it appropriate to troll me, abuse me and call me names. I deleted my account.
I've reported bugs on Launchpad (a nightmare, took several days to figure it out with friendly help from users here). Result: nothing.
I've asked questions here without results (perhaps my headlines aren't sexy enough). Admittedly, my questions go beyond what can be read in the user manual for Lubuntu.

I've had great responses from one or two users with knowledge of Lubuntu.
However, disillusion, discouragement and frustration grows when every problem hits a brick wall.


I re-read this, and now consider I have to respond.

I too am not a programmer.  You can contribute to Ubuntu (*and this includes flavors too*) without being a programmer.

Almost all Ubuntu (*and flavor*) systems use launchpad; so reporting issues will almost exclusively require it. Yes some (eg. Ubuntu-MATE) do prefer it on GitHub, but as Ubuntu uses launchpad for QA; you'll end up reporting the issue twice (GitHub + Launchpad) & linking reports rather often.. ie. you'll still often need to use launchpad for tracking bugs in much of Ubuntu (*and flavors*).

You've mentioned the Lubuntu discourse issue before, I recall it vaguely, but do not have clear memory of *events* sorry (*nor recall when which would probably helped to allow me to find something & refresh memories*). I don't recall anyone being called 'names' or 'troll' like behavior though.  If you'd like me to look, you can PM me some details (*or should the issue involve me, I'll find another solution/person*[I]).

[/I]Disagreements between people will always occur, esp. given cultural & language differences, and on this form of *written or electronic* communication where we can't see the *body language* of the person to whom we're speaking, thus can't in real time *adjust our wording* so our intention is better understood. This form of communication is missing most of how humans usually communicate (*ie. our body language*).

---

### Post by TheFu on 2023-05-24
Why use any DE at all?  They aren't necessary for a nice, system interface.  Check out some of the different Window Managers. I suspect you might be surprised at how full featured they are.  Additionally, many WMs provide full customization to the detailed level that DEs don't support.

As a reminder, 
[IMG]https://upload.wikimedia.org/wikipedia/commons/9/95/Schema_of_the_layers_of_the_graphical_user_interface.svg[/IMG]
There's no mandate to use any DE.  They are optional.

For example, I use fvwm. There's a prettier theme with fvwm-crystal - see these screenshots. [https://fvwm-crystal.sourceforge.io/screenshots.html](https://fvwm-crystal.sourceforge.io/screenshots.html)  fvwm is in the repos, so you can install it on your current system and pick it on the login screen.  Because it isn't GTK+ or Qt based, it won't conflict with other DEs you may already have loaded.

---

### Post by wyattwhiteeagle on 2023-05-28
I've tried other 'buntu flavors.
Each time I tried one, I posted here that it's awesome.
Only after then did I begin to run into problems with that particular flavour.
Those problems are those which you describe, problems that seems to not have a solution anywhere.

I didn't know specific terminology to ask "the right questions" and get "the right answers".
There are still questions I've asked when I first came to Ubuntu that have yet to be responded to.
Yes, it becomes frustrating and maybe even irritating.

There are lots of people here who has a phenomenal knowledge of 'buntu who seems to speak in terms way above and beyond my technical knowledge.

Lubuntu is the flavour that I've stuck with the longest.
I've left Lubuntu...then came back...then left again...then came back...
The reason I kept coming back is because it's "easiest for me to learn".
That doesn't mean it is easy to learn, it's "easiest for me" to learn.
And there are a lot of things about Lubuntu that I still don't know.

There's only a few things I've encountered which I haven't asked here yet.
Only a couple things I've gotten help on that I'm having a rough time grasping...you know..."if I can just get it through my thick head".

Don't be hard on yourself.
We're all human.

As for you...don't be discouraged.
Try the different things suggested here on the forums.
Learn at your own pace.
Learn what is "most simple for you" to learn.
Do that which is "most simple for you".
If you feel you're being ignored here on the forums, take a break from the forums and think of how your question sounds to others here on the forums, then come back and re-phrase the question, or add more details to the question.

There are lots of people here who are willing to offer knowledge when you ask.
Some of those people may reply with questions to try and understand what your trying to ask.

Some of the best help I've received came from these forums.
Those who have helped me, I guarantee, there was one time or another they felt it was useless trying to help me.

Be strong, and of a good courage, for the learning curve of 'buntu is possible to overcome.

---

### Post by ian-weisser on 2023-05-28
Great advice. Well-written, well-organized.

> **wyattwhiteeagle said:**
> ... "the right questions" and get "the right answers"

I have begun discerning between the terms "right answer" (which suggests policy) and "useful answer" (which suggests helpfulness).

That's not a quibble about the use of "right." Use "right" all you like! It's a great word.
It's merely an encouragement to all readers that broader vocabulary, used wisely, can help clarity.

---

### Post by wyattwhiteeagle on 2023-05-28
> **ian-weisser said:**
> Great advice. Well-written, well-organized.



I have begun discerning between the terms "right answer" (which suggests policy) and "useful answer" (which suggests helpfulness).

That's not a quibble about the use of "right." Use "right" all you like! It's a great word.
It's merely an encouragement to all readers that broader vocabulary, used wisely, can help clarity.

Thank you

Absolutely YES.
Everywhere I look, I notice "policy" being utilized.
The kernel, DE, apps or packages, even the very system it is being used on, whichever...that each of us use...I notice "policy" being used.
We need useful advice to be able to use policy properly.

Notice I used quotation marks around right questions and around right answers.
To one person, "right answers" may be easily understood, when that same exact answer is above the level of technological understanding of the next reader.

I chose "right answers" to denote that the answer is only as useful as the reader understands it.
As the reader learns the "in's and out's" of the 'buntu world, the reader begins to rely on the most useful advice given to the reader.

---

