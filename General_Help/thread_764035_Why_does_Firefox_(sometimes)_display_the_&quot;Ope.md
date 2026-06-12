---
title: "Why does Firefox (sometimes) display the &quot;Opening...&quot; dialog?"
date: 2008-04-23
forum: General Help
---

### Post by DasCrushinator on 2008-04-23
Sometimes when doing a Google Image Search, I will try to click on an image to see only it (not see the Google frame on top and the original page from which the image came frame on bottom).

Sometimes when doing this, I get the "Opening..." dialog.  Normally it's not that big of a deal to me; however now I seem to get it for some PHP files as well.  I was about to post something on Autopia.org, and upon hitting the "Post New Thread" button, I get this:

---

### Post by gsmanners on 2008-04-23
That is pretty weird, but not quite this level:

---

### Post by twright on 2008-04-23
i think it's a server side error

---

### Post by KOld Iron on 2008-04-23
> **DasCrushinator said:**
> Sometimes when doing a Google Image Search, I will try to click on an image to see only it (not see the Google frame on top and the original page from which the image came frame on bottom).

Sometimes when doing this, I get the "Opening..." dialog.  Normally it's not that big of a deal to me; however now I seem to get it for some PHP files as well.  I was about to post something on Autopia.org, and upon hitting the "Post New Thread" button, I get this:

I usually get this behavior, because I use Noscript to disable Javascript (particularly the download for .php files). Allowing Javascript for the page normally fixes that.

---

### Post by DasCrushinator on 2008-04-24
Hmm, how would I go about fixing it?

---

### Post by twright on 2008-04-24
i would try telling the servers owner, i thinks they just need to change a value in their php.ini file

i think it wouldn't load at all for internet explorer users

---

### Post by kpkeerthi on 2008-04-24
> **DasCrushinator said:**
> Hmm, how would I go about fixing it?

There is nothing wrong with your firefox. The server at the website   is delivering the PHP to browser "as is" without interpreting it. Contact the site admins.

---

### Post by DasCrushinator on 2008-04-24
Thanks!

---

