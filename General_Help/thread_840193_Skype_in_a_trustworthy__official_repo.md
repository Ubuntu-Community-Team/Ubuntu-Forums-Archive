---
title: "Skype in a trustworthy / official repo?"
date: 2008-06-25
forum: General Help
---

### Post by georgia_tech_swagger on 2008-06-25
Hello.  I'm reviewing Ubuntu 8.04 as the first episode of a podcast I'm doing, in the ilk of the now defunct System Trash podcast if any of you saw that one.   It's called SourceCast ( [www.sourcecast.org](www.sourcecast.org) ).

Anyway, I was trying to get Skype installed, and noticed it was not any of the repos including 3rd party.   Are there plans to include it there?   Is there any particularly good reason why it isn't?  I don't want to go around manually installing packages from their source websites like I do in windows, or use (insert name of shadowy dev figure here) repo, because I'm a security paranoid kinda guy.

Thanks for any assistance you can provide!

---

### Post by wormser on 2008-06-25
Skype is closed source so it is not in the official repositories.  It is in the trusted Medibuntu repository.  Directions on setting it up [here]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f"): I do not think it is the latest version which has web cam features.

---

### Post by georgia_tech_swagger on 2008-06-25
Ah -- is Medibuntu officially affiliated with Canonical/Ubuntu in some form?   Or is it a group of devs doing their own thing?

---

### Post by Marshal0505 on 2008-06-25
It's the 2.0.0.** version in the Medibuntu repo.If i'm not mistaken this means webcam functionality.So it should work fine. :)

---

### Post by georgia_tech_swagger on 2008-06-29
Thanks for the help guys.   The review is here ( sourcecast.org ) if you're interested.

Particularly shocking to me was how Ubuntu stacked up to Gentoo in performance.

---

### Post by Vivaldi Gloria on 2008-06-29
> **georgia_tech_swagger said:**
> The review is here ( sourcecast.org ) 

ibex is not a bird:

[http://en.wikipedia.org/wiki/Ibex](http://en.wikipedia.org/wiki/Ibex)

---

### Post by kostkon on 2008-06-29
> **georgia_tech_swagger said:**
> Hello.  I'm reviewing Ubuntu 8.04 as the first episode of a podcast I'm doing, in the ilk of the now defunct System Trash podcast if any of you saw that one.   It's called SourceCast ( [www.sourcecast.org](www.sourcecast.org) ).

Anyway, I was trying to get Skype installed, and noticed it was not any of the repos including 3rd party.   Are there plans to include it there?   Is there any particularly good reason why it isn't?  I don't want to go around manually installing packages from their source websites like I do in windows, or use (insert name of shadowy dev figure here) repo, because I'm a security paranoid kinda guy.

Thanks for any assistance you can provide!
What is better than the official *Debian*/*Ubuntu* repository (as referenced here in the [*Ubuntu* documentation for *Skype*]("https://help.ubuntu.com/community/Skype")). It works like a charm and is safe to use it in *Ubuntu*.

Just go to *System -> Administration -> Software Sources* and add the following repository to your software sources list
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

---

