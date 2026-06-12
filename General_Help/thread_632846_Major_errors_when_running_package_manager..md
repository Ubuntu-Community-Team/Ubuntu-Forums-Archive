---
title: "Major errors when running package manager."
date: 2007-12-05
forum: General Help
---

### Post by kuantum_fizax on 2007-12-05
Okay, I had some issues mentioned on this post. It has some background info:
[http://ubuntuforums.org/showthread.php?t=620568](http://ubuntuforums.org/showthread.php?t=620568)

Long story short, updates started failing, first for cups-sys, followed by other programs, and finally certain packages wouldn't install. I never got any solutions. I think people just stopped posting in that threat thinking I must have had a solution if I had as many replies as I did. Anyways, since I posted that, my package manager stuff has grown to be much worse.The list of updates that couldn't be applied grew. Now, finally, I cannot run an  update or package installation (using synaptic package manager) without it giving the error:

E: tzdata: subprocess post-installation script returned error exit status 1

Which seems to completely stop the update or install process I'm running.

Related to this might be the fact that I recently tried reinstalling Firefox. Specifically, I was having crashing problems, which I saw somewhere could be fixed by taking the tar file directly from mozilla and replacing everything in your firefox directory with that. ( It didn't work, and I still have the crashing, but I digress) Tthis new error with the updating seems to have coincided with a new firefox update, so I may have confused the whole system  by my hack of a reinstall.  

Anyways, any suggestions? Any help would be greatly appreciated. I'm seriously considering reinstalling linux, but it doesn't seem like that should be necessary... I'm running on a thinkpad T60 if it matters at all...

Thanks!

---

### Post by barney_1 on 2007-12-07
I had a tzdata update problem myself.  What worked for me was to change the timezone to London, run your updates, then change it back to the proper time zone.

It worked for me. If that doesn't do it, take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=583024](http://ubuntuforums.org/showthread.php?t=583024)

---

### Post by kuantum_fizax on 2007-12-09
No luck... I think my problem might be wider than what they are saying, because this problem started with updating cups. tzdata is kind of new, although it seems to have taken center stage.

None of the solutions I could find on that thread worked...

---

