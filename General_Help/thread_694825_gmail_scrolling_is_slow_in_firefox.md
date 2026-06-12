---
title: "gmail scrolling is slow in firefox"
date: 2008-02-12
forum: General Help
---

### Post by themoebius on 2008-02-12
So far every other site is nice and snappy and smooth, but gmail is really choppy when I try to scroll around. It was kind bad in FF2. Now I upgraded to FF3 and although the app as a whole runs more quickly, gmail is much slower.

Whats the deal?

---

### Post by Pekkalainen on 2008-02-12
I have noticed that when I type replies to people in gmail the cursor tends to lag most of the times, otherwise its working fine for me in stock firefox 2 in ubuntu 7.10.

---

### Post by fuhrysteve on 2008-02-18
Gmail scrolls extremely slowly for me too, and sometimes other sites that are heavy on javascript and stuff, but other than those, I have no problems. I can have 20 tabs open, and all of them scroll normally except Gmail, regardless of how many tabs are open.

I use swiftfox.

---

### Post by Yellow Pasque on 2008-02-18
Click the link in the upper-right corner that says 'Older version'. This will turn off the Javascript  chat. See if that helps

---

### Post by themoebius on 2008-02-19
crippling gmail isn't really a solution, though. This is a problem with firefox on linux. Firefox on my mac and windows handle gmail just fine.

I guess I'm looking for confirmation that it isn't just me and maybe wondering if someone has already filed a bug report?

But for the record, using the older version does fix the problem.

---

### Post by Yellow Pasque on 2008-02-19
> crippling gmail isn't really a solution, though. This is a problem with firefox on linux.
True, it's more of a workaround, but I think it's a damn good one. :)
Also, I believe the issue is with javascript.

---

### Post by Abiezer on 2008-02-20
> **themoebius said:**
> I guess I'm looking for confirmation that it isn't just me.

I've been having similar problem in both FF and Swiftweasel. It starts off snappy enough after a recent reboot, but then gets progressively slower. I wonder if it's a caching thing? I'd love a better solution; I already have chat turned off but the problem still gets worse over time.

---

### Post by Peepsalot on 2008-02-23
Hey folks, was just searching for a solution to this problem and read this thread.  Using "older version" did not really help in my case.  I was able to come up with my own solution though which really helped.

When you are viewing a long conversation, do you see a little box at the bottom right corner that displays the name of the person who's reply is below?  I noticed that on my computer, scrolling was slowest only when this box is visible.  Scrolling speeds up a lot at the last portion of the page, where you are  viewing the last reply(and that name box is not in the bottom corner).

I don't know why displaying this small box makes firefox so slow, but I do know that disabling the display of this really helped my scrolling.

Here's how I disabled this box(html div element) from displaying:
I found a firefox plugin called [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108") that allows customized css to be applied to pages.  
I installed this plugin, went into it's preferences and added this rule:
```

@-moz-document domain(mail.google.com) {
#ind { display : none !important }
}

```
After this, it scrolls so much better for me.

Hope this helps you guys.

---

### Post by Peepsalot on 2008-02-23
Hmm, I guess it still slows down a lot when an active chat pane is being displayed.  But I guess you can just close this when not in use. 

Something about these displays that do do not scroll along with the rest of the page.  Whenever firefox must show them, it seems to slow down considerably.

---

### Post by psyke83 on 2008-02-26
Although I'm using Hardy, my post here should equally apply to Gutsy (and indeed, Firefox 2): [http://ubuntuforums.org/showthread.php?p=4412617](http://ubuntuforums.org/showthread.php?p=4412617)

---

### Post by Peepsalot on 2008-02-28
> **psyke83 said:**
> Although I'm using Hardy, my post here should equally apply to Gutsy (and indeed, Firefox 2): [http://ubuntuforums.org/showthread.php?p=4412617](http://ubuntuforums.org/showthread.php?p=4412617)
This one did not make a noticeable difference for me, though the theme does look slicker, so I think I'll keep it.  :)


Also, in case anyone cares, the fix I wrote previously needs an update.
It looks like the name box no longer uses id="ind", it appears to have class="sss8ob" for now, so I added another rule
```

@-moz-document domain(mail.google.com) {
#ind { display : none !important }
.sss8ob { display : none !important }
}

```
I have no idea how often these things are changed though, so maybe this will not work again tomorrow if they keep changing the html classes, ids, etc.

---

### Post by Endolith on 2008-05-02
"Experience the fastest Firefox ever — twice to three times as fast on today's complex web applications like Google Mail or Zoho Office."

lolz.  This is super slow for me, too.  I'm surprised it hasn't been fixed yet.

---

### Post by vdawg on 2008-05-03
Ya it was slow for me too, I just installed pidgin for googletalk and I use the html version :)

---

### Post by JaspSoft on 2008-05-17
Does anyone know when this is going to be fixed? It is driving me NUTS!

---

### Post by themoebius on 2008-05-17
Its still not fixed in FF3 beta 5. I switched to Opera, which doesn't have an scrolling issues, but it does have some compatability issues with ajax sites.

---

### Post by Endolith on 2008-05-19
> **JaspSoft said:**
> Does anyone know when this is going to be fixed? It is driving me NUTS!

Never. :)

Does this workaround work for Gmail?

1. Install the Stylish Add-on ([https://addons.mozilla.org/en-US/firefox/addon/2108](https://addons.mozilla.org/en-US/firefox/addon/2108))
2. Right click the icon --> Write style --> For google.com
3. Add "*{border-style: none !important;}"

---

### Post by dunnerz on 2008-05-19
Hi,

Problem for me too at home - (ubuntu Hardy).
However, my work PC, Kubuntu Hardy (through upgrade, not fresh install) - gmail works 100% okay.

Makes me think it is Ubuntu related, rather than Firefox? 
The RC for firefox is out today - so once that gets to the repos, I'll see if the problem is still there.

I'll try this [http://ubuntuforums.org/showthread.php?p=4412617](http://ubuntuforums.org/showthread.php?p=4412617)  later at home and see what happens - but my guess is also to try to go to add-ons->(in firefox) and disable the ubuntu firefox modifications pack.

I'll post my results !

---

### Post by Endolith on 2008-05-19
> **dunnerz said:**
> I'll try this [http://ubuntuforums.org/showthread.php?p=4412617](http://ubuntuforums.org/showthread.php?p=4412617)  later at home and see what happens - but my guess is also to try to go to add-ons->(in firefox) and disable the ubuntu firefox modifications pack.

I tried both of those, and neither worked.  The only thing that worked is turning off borders in Gmail, since part of this is apparently caused by border rendering.  Other sites are still slow for other reasons, though.

---

### Post by crisnoh on 2008-05-19
For the record, this problem isn't restricted to Ubuntu.  I'm experiencing the same thing under Arch.

---

### Post by dunnerz on 2008-05-19
> **Endolith said:**
> I tried both of those, and neither worked.  The only thing that worked is turning off borders in Gmail, since part of this is apparently caused by border rendering.  Other sites are still slow for other reasons, though.


Hi,

Agreed - those didn't fix it - doing the "stylish" / no borders fix **did work. **Thanks for the tip

It is an annoying bug though !

---

### Post by svaens on 2008-07-08
Just for the record ( i know this is an old thread), 
Using firefox 3, ubuntu Hardy, 

switching to 'old version' makes scrolling perfect. 

This is not a 'crippling' solution (although annoying enough) as javascript is still used (and obviously used better). 
What have gmail done with the new ui!!! geez!

---

### Post by Endolith on 2008-07-08
Is it just me, or did this get better for a few weeks and then get worse again?

---

### Post by stek79 on 2008-07-11
I have the same suspect!!!

Must be an updated package...

---

### Post by dunnerz on 2008-07-12
yes, it is going slow for me again too !
I wonder if this was an update to firefox or ubuntu?

---

### Post by Endolith on 2008-07-12
I checked with a brand new user account, with or without Compiz enabled, and it's still super slow, while other pages scroll quickly.  I swear this got better for a while.  What changes have been made lately?

---

### Post by stek79 on 2008-07-13
Hi,
  I don't remember any FF3 update lately, other than the beta->3.0 package.

I remembere a recent update to libcairo, which is the graphic library used by FF3.

I have to check if I can find the previous version and install that one.

BTW if you check the changelog, it seems that a performance related patch has been removed:

cairo (1.6.0-0ubuntu2) hardy-proposed; urgency=low

  * debian/patches/03-turn_on_buggy-repeat_handling.dpatch:
    - don't use this workaround, it's not required and create slowness issues
      (lp: #219587)

 -- Sebastien Bacher <seb128@canonical.com>  Tue, 03 Jun 2008 18:30:35 +0200

---

### Post by Endolith on 2008-07-20
And today it's much better, for instance.  I don't know what's changing.

---

