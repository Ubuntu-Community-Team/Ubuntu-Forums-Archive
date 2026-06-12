---
title: "Mutt No matching mailcap entry found.  Viewing as text."
date: 2018-04-17
forum: General Help
---

### Post by GrouchyGaijin on 2018-04-17
Hi Folks,

I recently started using Mutt again and overall it is working well.
The main problem I am having is viewing images.

For example attached is a scrot of the attachment view of a recent message I received: 

When I click on one of the jpg files in the attachment list I get this error:
```
No matching mailcap entry found.  Viewing as text.
```

Inside my ~/.mutt folder I have a file called mailcap.mutt (I have also renamed it to mailcap_mutt to see if that made a difference).
In the mailcap.mutt file I have many listings.
for jpg files I have:
```
image/jpeg; /user/bin/viewer display 'jpeg:%s'; test=test -n "$DISPLAY"
image/jpg; /user/bin/viewer 'jpeg:%s'; test=test -n "$DISPLAY"
```

I also have graphicsmagick installed and had these entries set to:
```
image/jpeg; gm display 'jpeg:%s'; test=test -n "$DISPLAY"
image/jpg; gm 'jpeg:%s'; test=test -n "$DISPLAY"
```

Does anyone see what I am doing wrong?
I really like mutt more than any other client and would have to have to use something else just to view images without saving them first.

Thank you,

GG

---

### Post by GrouchyGaijin on 2018-04-17
Never mind - the path in my .muttrc file was pointing to the wrong place

---

