---
title: "Can't fetch storage information"
date: 2012-10-25
forum: General Help
---

### Post by leopoldbirkholm on 2012-10-25
_Hello dear members_

I have an issue with my Ubuntu 12.10 Unity 32-bit installation. It comes when I try to use the update function via the cog wheal up to the left. See this image:

[http://ubuntuone.com/7SJtfQdxAf9gq7xheonXsN](http://ubuntuone.com/7SJtfQdxAf9gq7xheonXsN)

I can override the problem via the Terminal but I like to know I cannot longer update my system via the update manager?

I have tried to search the forum with the tags:
update, error, fetch, information, gui, 12.10

I have mixed the tags in the hope of finding something.

What am I missing here?

//Leopold

**Edit:**
Forgot my computer spec.
Homebuild desktop.
OS: Ubuntu 12.10 Unity
Mothereboard: Intel
CPU: Intel® Core&#8482;2 CPU 6300 @ 1.86GHz × 2 
Anything more, ask and I will find out the hardware.

---

### Post by drmrgd on 2012-10-25
The issue is that this PPA is not available for Quantal according to the launchpad website.  The latest version looks to be Precise, and so you're getting a not found error since it doesn't exist.  You can just remove this repository from your sources list in the Update Manager, and then this error should go away.

---

### Post by leopoldbirkholm on 2012-10-27
> **drmrgd said:**
> The issue is that this PPA is not available for Quantal according to the launchpad website.  The latest version looks to be Precise, and so you're getting a not found error since it doesn't exist.  You can just remove this repository from your sources list in the Update Manager, and then this error should go away.

Thank you drmrgd.

Refining search with "remove repository update manager ubuntu".

I will post my success. :KS

---

### Post by leopoldbirkholm on 2012-10-27
Thanks to drmrgd I was able to refine my search perimeters and found a solution - see [Snippet: How to Remove Repositories In Ubuntu ]("http://maketecheasier.com/remove-repositories-in-ubuntu/2010/05/27").

I went to "Settings" (or the cog wheel with the wrench on it at the launch bar :-)), 
on the line at the bottom clicked onto "Program Source" (I don't know what it's called in English, I translate directly from Swedish),
went on to the second column "other software",
scrolled down to the two lines that cause me problem (see the image earlier in this post) and clicked "remove".

Closed the windows down, went to the Terminal, wrote
```

sudo apt-get update
Password: *Hysh, it's my secreet! :P*

```
and it worked without any problem now.

Thanks for all the help!

//Leopold

---

### Post by drmrgd on 2012-10-27
No problem, glad I could help.  Sorry I didn't give you more details about how to remove repository sources previously!

---

