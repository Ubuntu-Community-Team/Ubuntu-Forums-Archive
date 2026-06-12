---
title: "Dell D600 Can't Enable Desktop Effects in 8.04"
date: 2008-05-24
forum: General Help
---

### Post by Vuddha on 2008-05-24
Hi all,

I've got a Dell D600 and I can't enable Desktop Effects. I am using Ubuntu 8.04.

I was able to very successfully use Desktop Effects in Ubuntu 7.04 and 7.10.

I've tried searching the forums, and no luck.

Thanks for the help.

---

### Post by Kevbert on 2008-05-24
Have a look at this: [http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")
If I guess correctly your machine has a Radeon 9000 with 32Mb memory.  Are you using a restricted driver or the built in one for your card ?  What error messages do you get ?

---

### Post by Forlong on 2008-05-24
Sounds like you got blacklisted in Hardy. Compiz-Check should fix this for you. :)

---

### Post by Vuddha on 2008-05-24
Thanks for replying so promptly. I have used compiz-check (that was great) and it turns out I have been blacklisted. The output from compiz-check is as follows:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze, this particular combination had to be
 blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

Do you want to skip blacklist checks by Compiz? (y/N) 



I have a follow-up question. According to this result, does this mean that the set-up will cause x-server to crash? Actually, I had X crash periodically while using 7.04 and 7.10. Could it be because of the ATI card? By enabling desktop effects in 8.04, would this increase the chance of X crashing?

Thanks again for the help. And the Forlong pages are excellent.

---

### Post by Forlong on 2008-05-24
> **Vuddha said:**
> According to this result, does this mean that the set-up will cause x-server to crash? Actually, I had X crash periodically while using 7.04 and 7.10. Could it be because of the ATI card? By enabling desktop effects in 8.04, would this increase the chance of X crashing
That depends...
What do you mean by 'crash' and what is 'periodically' to you?

---

### Post by Vuddha on 2008-05-24
> **Forlong said:**
> That depends...
What do you mean by 'crash' and what is 'periodically' to you?

When I say "crash", I mean it would automatically "log off" my session and take me back into the log-in screen. Previously, other users have suggested that this indicates the X server is crashing, but I couldn't relate it to a possible cause. I don't have much time to learn the fine details of Ubuntu, so I'm not very good at diagnosing/fixing problems.

"Periodically" means once a week? Once every couple of weeks? I use my computer for hours every day (mainly Lyx, Firefox, Jabref, and occasionally k9copy).

I can't recall having X server issues in Ubuntu 6.04 or 6.10, only in 7.04, 7.10.

If enabling desktop effects would cause this problem to re-occur, maybe I would think twice.

Thanks.

---

### Post by Neo4 on 2008-05-25
I have the same problem with ati x700 + 8.05 drivers + hardy

I've skiped blacklist and enable compiz that messed up all my desktop.

now I'm with composite disabled

what can I do to run compiz? should I downgrade my ati driver?

---

### Post by Forlong on 2008-05-25
> **Vuddha said:**
> When I say "crash", I mean it would automatically "log off" my session and take me back into the log-in screen. Previously, other users have suggested that this indicates the X server is crashing, but I couldn't relate it to a possible cause. I don't have much time to learn the fine details of Ubuntu, so I'm not very good at diagnosing/fixing problems.

"Periodically" means once a week? Once every couple of weeks? I use my computer for hours every day (mainly Lyx, Firefox, Jabref, and occasionally k9copy).
Those are definitely not the symptoms of that bug.
(In fact, the X server won't crash but freeze. Maybe I should overhaul that explanation.)

So I think you should be fine skipping the blacklist.


@Neo4: What do you mean by "messed up all my desktop" and how did you install the fglrx driver?

---

### Post by Neo4 on 2008-05-25
I mean that my desktop when I put my mouse over some folder or other file it change to a square full of fragmented colors! it happens in any button, right mouse button gives me the same, gnome menu button too.

I guess this happens because my graphic card is blacklisted on compiz!

i've installed my 8.5 ati drive manually

---

### Post by Forlong on 2008-05-25
> **Neo4 said:**
> I mean that my desktop when I put my mouse over some folder or other file it change to a square full of fragmented colors! it happens in any button, right mouse button gives me the same, gnome menu button too.
That is a bug in the fglrx driver, it's well known, especially on dual head setups.

Try searching in the forums for this problem.
> **Neo4 said:**
> I guess this happens because my graphic card is blacklisted on compiz!
No, that's definitely not the reason.
> **Neo4 said:**
> i've installed my 8.5 ati drive manually
May I ask why you did that? Are there any benefits over the one from the Ubuntu repos for you?
The issue mentioned above may very well be because of an installation failure.

---

### Post by Neo4 on 2008-05-25
I've installed manually because it is a newer  version than the one on the repos.

the installation works like a charm, I've installed all my ati drivers this way...

If this isn't a problem with compiz why the card is blacklisted?
in this forum you have a sticky post about that.

can you give me a theread talking about that fglrx problem?
on ubuntu 7.10 I had no problems :S

thanks a lot

---

### Post by Forlong on 2008-05-25
> **Neo4 said:**
> I've installed manually because it is a newer  version than the one on the repos.
So what? If it doesn't add (to you) important functionality then why bother?
Never change a running system ;)
> **Neo4 said:**
> the installation works like a charm, I've installed all my ati drivers this way...
Just because there were no big bold error messages, doesn't mean everything is set up correctly.
> **Neo4 said:**
> If this isn't a problem with compiz why the card is blacklisted?
Your graphics card is not blacklisted at all on Hardy.
> **Neo4 said:**
> in this forum you have a sticky post about that.
Just to avoid confusion: I'm just a regular user here, just as you are.
> **Neo4 said:**
> can you give me a theread talking about that fglrx problem?
on ubuntu 7.10 I had no problems :S
I would have to do a search in the forums for such a thread just as you.
My main recommendation would be un-installing the driver you manually installed and try the optimized one from Ubuntu.

---

### Post by Neo4 on 2008-05-25
I've istalled the newer because it could over with some bugs that the 8.4 had..

the card isn't blacklisted on hardy, it is baclkisted on compiz, this is what the compiz-check said...

without compiz the sistem works good.

btw, i'm not using dual-head :)

I will search :)

---

### Post by Forlong on 2008-05-25
> **Neo4 said:**
> the card isn't blacklisted on hardy, it is baclkisted on compiz, this is what the compiz-check said...
Please post that output here (and make sure you have the latest version 0.4.1).

---

### Post by Neo4 on 2008-05-25
this was what compiz check said:

Blacklisted PCIID '8086:2972' found

if i press know more information is said that my card is blacklisted due to a driver problem with compiz...

(I don't have the text because I've choose to ignore and run compiz..)

---

### Post by Forlong on 2008-05-25
*This* is probably what the script told you:
```
Error: PCI ID $PCIID detected.

Your particular graphics chip may be blacklisted on certain distributions.
However that does not necessarily mean you won't be able to run Compiz.

You can skip this blacklist -- but keep in mind that you did so.
Do not complain if you encounter any problems with Compiz afterwards.
```
I know that your card is not blacklisted on Hardy.

And there is no such thing as a blacklist in Compiz itself.

---

### Post by Neo4 on 2008-05-25
yes that was what was told me.

well i've enabled composit and compiz and now it works like a charm :| lool

I haven't changed anything! very strange!

now I can't choose emerald themes! they are still the gnome... maybe this is a new option on compiz i will check that!

thanks a lot forlong!

---

### Post by Forlong on 2008-05-25
> **Neo4 said:**
> now I can't choose emerald themes! they are still the gnome... maybe this is a new option on compiz i will check that!
Try ```
emerald --replace
```

---

### Post by Neo4 on 2008-05-25
worked :D

how can I put this to run without the console open?

should I add this to the start up programs?

---

### Post by Forlong on 2008-05-25
> **Neo4 said:**
> how can I put this to run without the console open?
Run it via [Alt]+[F2]
> **Neo4 said:**
> should I add this to the start up programs?
If you want to use Emerald by default, try this:
```
echo USE_EMERALD=yes >> $HOME/.config/compiz/compiz-manager

```
This *should* take of it, because Hardy has a separate script to run the decorator.

Restart Compiz afterwards and see if it worked, if not, I'm confident we'll find another way ;)

---

### Post by Neo4 on 2008-05-25
It worked! thanks a lot forlong!

---

### Post by Vuddha on 2008-05-26
> **Forlong said:**
> Those are definitely not the symptoms of that bug.
(In fact, the X server won't crash but freeze. Maybe I should overhaul that explanation.)

Hi Forlong, thanks for your help. Actually, now that you mention it, my X Server did freeze. When this occurred, I had to do a hard shutdown of the computer. This will be my last question relating to this problem.

Should I be concerned about this in 8.04, then?

---

### Post by Forlong on 2008-05-26
OK... here goes:
The bug did not come up until the driver version included in Gutsy, thus if you had no problems at all on **Feisty** but freezes on Gutsy, you are most probably one of the affected users.

(another indicator is Debian Lenny btw. -- that has the same driver version as Feisty used to have)

A pretty safe way to find out if you are affected on Gutsy/Hardy is installing a 3D tuxracer game:
```
sudo apt-get install extremetuxracer
```
**Afterwards, close all running applications!**

Then run
```
etracer
```
If you are able to run it without the X server freezing (music continues, everything else just stopped working), then you are _not_ affected.

Note that the game *will* run painfully slow for you. That's (unfortunately) normal.

If you do get the freeze, you have to restart your computer like this:
[list][*][Alt]+[Print] (hold those pressed the whole time!)
[list=1][*][R]
[*][E]
[*][I****]
[*][S]
[*][U****]
[*][B****][/list][/list]

---

### Post by Vuddha on 2008-05-27
Thanks Forlong. I'll try this and let you know.

---

### Post by kanaqsasak on 2010-04-24
It works for me, upgrading from Gutsy to Hardy. I'm quit using Karmic. Thanks for the advice.. :)

---

