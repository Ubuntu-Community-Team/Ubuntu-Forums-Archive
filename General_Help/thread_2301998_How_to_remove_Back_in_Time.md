---
title: "How to remove Back in Time"
date: 2015-11-06
forum: General Help
---

### Post by windwalker2 on 2015-11-06
Not sure how I did it, but it may have been from the command line I installed Back In Time. In the Applications list in Wily Werewolf 15.10 I am showing two icons for back in time.
One is back in time and the other back in time (root). Both function when clicked on.

I went to the software section and they both show not installed. So I installed them thinking it would help uninstall them. I clicked "remove" on both and it says it removed them and they are showing the option to "install" now.

I'm not planning on using back in time and was wondering if there was a safe way to remove the two that are showing and functional. 

Thanks,

---

### Post by Germar on 2015-11-09
Please open a Terminal and type
```

sudo apt-get remove backintime-common

```

Regards,
Germar, BIT Dev-Team

---

### Post by windwalker2 on 2015-11-09
That was simple. Thank you so much for that help I appreciate it. It removed it perfectly.

---

### Post by Bucky Ball on 2015-11-09
You might also want to:

```
sudo apt-get autoremove
```

... to eradicate any cruft it may have left hanging about.

When you're happy, see the first link in my signature. Thanks and enjoy.

---

### Post by windwalker2 on 2015-11-10
Would that be 

sudo apt-get autoremove backintime
and should I run that after I have already used the first instructions or will it cause a problem.
Thanks

---

