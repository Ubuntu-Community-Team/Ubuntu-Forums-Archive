---
title: "problem with bookmarks dolphin gutsy"
date: 2007-10-26
forum: General Help
---

### Post by roy92 on 2007-10-26
I just installed the new kubuntu, and I just edited the dolphing bookmarks (delete and change icons) but when i open dolphin the bookmarks are the same likethe beginning and the icons are not the ones i put, and plus i get an error that says: 

Unable to save bookmarks in /home/roger/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive. 

and like it says "This error message will only be shown once" everytime I open dolphin that error appears.

---

### Post by por100pre1 on 2007-10-27
```
sudo chown -R roger:roger /home/roger/.kde
```

Let us know if this works. :-k

---

### Post by BWF89 on 2007-10-28
@por100pre1: Thanks for that. I was having the same problem.

---

### Post by mistergq on 2007-10-30
thanks, that command worked for me too!

---

### Post by raydar on 2007-10-31
And me--thanks!

---

### Post by por100pre1 on 2007-10-31
> **BWF89 said:**
> @por100pre1: Thanks for that. I was having the same problem.
> **mistergq said:**
> thanks, that command worked for me too!
> **raydar said:**
> And me--thanks!

Glad to help! :) BTW, this is clearly a bug, I'm asking myself what causes it. :-k

---

### Post by bmorency on 2007-11-03
> **por100pre1 said:**
> Glad to help! :) BTW, this is clearly a bug, I'm asking myself what causes it. :-k

what caused it for me was when I opened dolphin and at some point  you click "open as root" on the right. it will change thethe ownership of /home/user/.kde/share/apps/d3lphin/bookmarks.xml  and other files in that directory. I think it should be changing that folder in root's home folder instead of the users home folder. a bug has been filed for this already. a lot of other people have confirmed this bug also. apparently it is a bug in kdesu.

---

### Post by por100pre1 on 2007-11-04
> **bmorency said:**
> what caused it for me was when I opened dolphin and at some point  you click "open as root" on the right. it will change thethe ownership of /home/user/.kde/share/apps/d3lphin/bookmarks.xml  and other files in that directory. I think it should be changing that folder in root's home folder instead of the users home folder. a bug has been filed for this already. a lot of other people have confirmed this bug also. apparently it is a bug in kdesu.

Thanks for clarifying this out. :)

---

### Post by rabspd on 2007-11-07
This method also worked for me.

---

### Post by BWF89 on 2007-11-08
It's doing the same thing for me again. Hopefully they'll release a patch for it or fix it in the next release.

---

### Post by Weyoun on 2007-11-11
Works!
Thanks a lot!!!

---

### Post by Benitlu on 2007-11-13
Thank you, you did fix my problem [http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by kooldino on 2007-11-17
Frankly I'm appaled that

a) it was released with such an obvious flaw

and

b) that a patch hasn't been released yet.

Either way, the command worked.  Kudos to you, sir.

Seems like you're just changing the ownership of the folder to yourself?  Huh?

---

### Post by John Bennett on 2008-01-20
Worked for me to.

Thank you por100pre1

---

