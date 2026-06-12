---
title: "OpenOffice.org Writer: Headers and Footers"
date: 2007-05-09
forum: General Help
---

### Post by BrokeBody on 2007-05-09
I'm doing some research in Writer and I don't know how to set up not to have header and footer on the first and the second page. So, I need to have header and footer from the third page to the last one. I tried messing around with styles, but I it seems like I'm doing something wrong.

Anyone knows how to set up this?

---

### Post by rich.bradshaw on 2007-05-09
Can't you just delete what's in them on the first couple of pages? That's what I have done before...

---

### Post by BrokeBody on 2007-05-09
> **rich.bradshaw said:**
> Can't you just delete what's in them on the first couple of pages? That's what I have done before...

Well that's the problem. If I delete their content on the first couple of pages, it will be deleted on every page.

---

### Post by jketvirtis on 2007-05-09
I have always done it this way: You have to set up different page styles.  You need to create one page style for your first two pages, and then a different one for everything else.  Once that is done, you can go Insert->Header and you'll see your two different styles, and can choose which to apply the header/footer to.

---

### Post by BrokeBody on 2007-05-09
> **jketvirtis said:**
> You have to set up different page styles.  You need to create one page style for your first two pages, and then a different one for everything else.  Once that is done, you can go Insert->Header and you'll see your two different styles, and can choose which to apply the header/footer to.

I know that is has to be done that way, but I don't know how to set up styles for my first two pages. I tried messing around with styles, but I can't find my way through all this. :(

I need help with styles actually. Hot to set them up for my first two pages?

---

### Post by jketvirtis on 2007-05-09
It's been a while, so I'm a little rusty, but what I would do is open up the style organizer, go to Pages, select your default style, and then click the top right "New Style from Selection" button and go from there.  Rename it something like "First Two Pages."  Then just go to your first two pages and change both of their styles to what you just created, and now you can make the different headers and footers.

---

### Post by Hagar Delest on 2007-05-10
You can also see this thread for further details about page styles : [[Solved] Starting header on 3rd page of document]("http://http://www.oooforum.org/forum/viewtopic.phtml?t=54051"). There are plenty of other threads on that forum about this issue. Feel free to search it.

---

### Post by BrokeBody on 2007-05-10
> **Hagar de l'Est said:**
> You can also see this thread for further details about page styles : [[Solved] Starting header on 3rd page of document]("http://http://www.oooforum.org/forum/viewtopic.phtml?t=54051"). There are plenty of other threads on that forum about this issue. Feel free to search it.

That's it. I wasn't paying attention to some small detail.

Thank you!

---

### Post by Guru88 on 2008-01-16
What about no headers on first page, but headers on all remaining pages?  I want the footer to be on all pages.  It seems when I play around with page styles, the header keeps popping up on the first page again.

---

### Post by Hagar Delest on 2008-01-16
You need 2 page styles: one for first page (with footer, no header), the second for the other pages (manually copy the footer of first page and activate header).

---

