---
title: "How to make Emblems size bigger?"
date: 2007-10-19
forum: General Help
---

### Post by UK-Wobbie on 2007-10-19
Hello all I have instilled Ubuntu 7.10 and everything is well... But only when i add any Emblems to a file! The Emblem size is like a dot.

Do any one no how to make it bigger?

Thanks :)

---

### Post by fragos on 2007-10-19
Increasing the size of icons in Nautius will increase emblem size at the same rate.  You might try another icon set, some have larger emblems.

---

### Post by kolinab on 2007-10-19
I came here looking for the answer to this question as well. My emblems show up extremely small now that I'm running Gutsy. 

I'm using the default icon set which had nice big emblems in Feisty.

[EDIT]

Here's the bug report:

[https://bugs.launchpad.net/ubuntu/+source/human-icon-theme/+bug/126104/](https://bugs.launchpad.net/ubuntu/+source/human-icon-theme/+bug/126104/)

There is a workaround suggested but I've yet to try it.

[edit again]

Works like a charm. yay!

---

### Post by exchequer598 on 2007-10-20
> Nicolò Chieffo wrote on 2007-09-03: Re: [Bug 126104] Re: emblems are too small (permalink) 

a way to fix the tiny emblems is to edit **/usr/share/icons/Human/index.theme**
and find

[scalable/emblems]
Size=128
Context=Emblems
Type=Scalable
MinSize=32
MaxSize=256

then [COLOR="Red"]change Size=128 to Size=24[/COLOR]

worked for me too!:D

---

### Post by Jim Danner on 2007-10-25
Yes, it has worked for me. As it says in the bug report: this workaround works only if your default icon size is set above 50%. Does anyone know of a way to get it right for smaller zoom levels too?

---

### Post by erginemr on 2007-10-26
Thanks a million. I shall give it a try. That also bothered me from the beginning.

---

### Post by shane_orlando on 2007-12-01
Worked Perfectly :)

---

### Post by Hopsakee on 2007-12-13
It's a bummer. It didn't work for me. I'm not allowed to edit the index.theme.

If I do:

sudo edit /usr//usr/share/icons/Human/index.theme

I get:

Warning: unknown mime-type for "index.theme" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"


Can someone solve this problem. I encoutered this also trying some other workarounds. Furthermore I got another post ([http://ubuntuforums.org/showthread.php?t=614009](http://ubuntuforums.org/showthread.php?t=614009)) which I think has got something to do with this issue. I think I messed up my mime-library somewhere.

---

### Post by Hopsakee on 2007-12-13
I figured out a sort of fix for this problem

sudo gedit

instead of

sudo edit.

---

### Post by OmegaBLK on 2007-12-13
> **Hopsakee said:**
> It's a bummer. It didn't work for me. I'm not allowed to edit the index.theme.

If I do:

sudo edit /usr//usr/share/icons/Human/index.theme

I get:

Warning: unknown mime-type for "index.theme" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"


Can someone solve this problem. I encoutered this also trying some other workarounds. Furthermore I got another post ([http://ubuntuforums.org/showthread.php?t=614009](http://ubuntuforums.org/showthread.php?t=614009)) which I think has got something to do with this issue. I think I messed up my mime-library somewhere.

Try using **ViM**, **gedit**, or **Nano** to edit the file.

---

### Post by days_of_ruin on 2007-12-27
> **exchequer598 said:**
> worked for me too!:D
:)Same here.

---

### Post by UK-Wobbie on 2007-12-30
> **Hopsakee said:**
> It's a bummer. It didn't work for me. I'm not allowed to edit the index.theme.

If I do:

sudo edit /usr//usr/share/icons/Human/index.theme

I get:

Warning: unknown mime-type for "index.theme" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"


Can someone solve this problem. I encoutered this also trying some other workarounds. Furthermore I got another post ([http://ubuntuforums.org/showthread.php?t=614009](http://ubuntuforums.org/showthread.php?t=614009)) which I think has got something to do with this issue. I think I messed up my mime-library somewhere.

I am getting the same thing!
I can not open the file when i edit..Or using ViM, gedit, or Nano to edit the file.


It keep saying like what Hopsakee put down :(

Can some one upload the index.theme file with the size thing init?
As i can not edit the file it self :(

Thanks

---

### Post by UK-Wobbie on 2007-12-30
Got it to work :lolflag: All things to playing about with it with OpenOffice :)

---

