---
title: "firefox, on edgy, keeps closing"
date: 2006-10-28
forum: General Help
---

### Post by fuscia on 2006-10-28
is it just me? it closes for seemingly no reason and then i get an error message saying "firefox has closed unexpectedly". no! really?

---

### Post by Raoul Duke on 2006-10-28
Not just you, my edgy FF was going down constantly...solution: download firefox 2.0

---

### Post by Lord Illidan on 2006-10-28
Same here.

---

### Post by mostwanted on 2006-10-28
Pretty much very time I open Fx on Edgy it gives me that message.

---

### Post by fuscia on 2006-10-28
> **Raoul Duke said:**
> Not just you, my edgy FF was going down constantly...solution: download firefox 2.0

isn't that what it is?

---

### Post by Lord Illidan on 2006-10-28
> **fuscia said:**
> isn't that what it is?

yes and no.. the version of firefox provided with edgy is a bit unstable.

---

### Post by .t. on 2006-10-28
As I wrote elsewhere, it's "Edgy"!

---

### Post by fuscia on 2006-10-28
> **Lord Illidan said:**
> yes and no.. the version of firefox provided with edgy is a bit unstable.

so, how would i replace it?

---

### Post by Jad on 2006-10-28
I tried to install FF myself and got same result, seems to be missing/confused/conflict in  some dependency libraries

---

### Post by tedrogers on 2006-10-28
I have this problem as well....but at least it loads up the last session when you restart!

Is FF2 (the stable version) somewhere in the repositories?

I have noticed there is a tarball version available on the mozilla website though....is this the one to use?

---

### Post by ~LoKe on 2006-10-28
I've been using Edgy for a while now; I upgraded to 2.0 once it was released, via the update manager.  No problems thus far.

---

### Post by Virogenesis on 2006-10-28
I'm having problems with firefox 2 on another linux distro.
Was hoping wasn't just me and as its not hopefully be fixed shortly.

---

### Post by fuscia on 2006-10-28
hey, epiphany's not bad (just couldn't bring myself to use opera).

---

### Post by user1397 on 2006-10-28
i upgraded from dapper, and my firefox 2 works perfectly.  maybe one crash one time, but that's it.

---

### Post by Jad on 2006-10-29
Just want to confirm that after I changed the depth from 16 into 24 i got things under control and no more crashes.

---

### Post by gvgerman on 2006-10-29
I became fed-up w/ Epiphany and the poor handling of favicons and the bookmarks, in general. I use Bloglines and Epiphany is incapable of finding the favicon for the toolbar. 

You can import bookmarks into Epiphany easily, but exporting them from Epiphany and then importing into anything else is a mess.  Plus, if you empty the cache, I discovered the bookmark favicons become mixed-up.  

Lastly, Epiphany's approach to Adblock is not as good as Adblock Plus in FF. The Epiphany wiki describes an "old" way to handled blacklists, but that method either was never used or has been abandoned.

Speaking of exporting Epiphany's bookmarks and having a mess, I also abandoned Evolution for similar reasons.  There is no easy way I could find to back-up the data or to import Evolution data into, say, Thunderbird, for instance.  I now use Tbird on XP and on Ubuntu and can easily keep the two in-sync.

---

### Post by fuscia on 2006-10-29
> **Jad said:**
> Just want to confirm that after I changed the depth from 16 into 24 i got things under control and no more crashes.

you did what?:???:

---

### Post by shining on 2006-10-29
That's a very well known problem, flash crash (these 2 go well together) when using 16 bit.
You need to edit /etc/X11/xorg.conf, look for DefaultDepth 16 (in Section "Screen"), and switch to 24.

---

### Post by APNelson.L on 2006-10-29
I have this problem and I think firefox crashes when it tries to prevent pop ups for me at least

---

### Post by cjnkns on 2006-10-29
I was just wondering if someone has found a solution to this?

Just installed Edgy and FF keeps closing on me also!!

](*,)

---

### Post by crthomas on 2006-10-30
The problem is with flash, not firefox.  I had the same problem too.  Change the default depth from 16 to 24, like was suggested above (in /etc/X11/xorg.conf).  Restart X (control alt backspace, or reboot) and you should be good to go.

---

### Post by Lord Illidan on 2006-10-30
My default depth was 24 and it crashed like hell. What I did was got the firefox 2.0 from Mozilla, and set the icons on the desktop to the location of the unzipped binary from Mozilla. Now it's faster and smoother.

---

### Post by fuscia on 2006-10-30
i'm loving epiphany and no longer care. it still seems luxurious to someone who used to use dillo all the time.

---

### Post by shining on 2006-10-30
> **fuscia said:**
> i'm loving epiphany and no longer care. it still seems luxurious to someone who used to use dillo all the time.

Well epiphany looks pretty much like firefox, only the interface is different.
I don't know how you could use dillo at the time :)
The rendering of most web page isn't very nice, and the interface in gtk1 is also ugly and not very useful.
Though, its speed is really amazing, and it's fine for viewing basic html site.

---

### Post by Brunellus on 2006-10-30
I am moving this to an appropriate, substantive forum.

---

### Post by fuscia on 2006-10-30
> **Brunellus said:**
> I am moving this to an appropriate, substantive forum.

you'll ruin my reputation.

---

