---
title: "Request for Folding@Home in the Repositories"
date: 2007-03-04
forum: General Help
---

### Post by altonbr on 2007-03-04
I'm just wondering how I can put in a request to have the Folding@Home project supported in the Ubuntu repositories? I THINK it's supported under Gentoo or a similar distribution but I'm not positive.

I see that some one on here already has a script to install Folding@Home but it is only updated as often as he feels like it. They have new beta releases that could be stabilized if someone where to look around at the code... such as 5.04 or 5.91... currently only 5.02 is available thanks to this man's efforts.

Can anyone help me on this dilemma? I believe it would be MUCH easier to install on my friends and family's PCs if I had this support. :KS


EDIT: Sorry, "some guy" refers to 'ndhskp' and his HOWTO's URL is: [http://www.ubuntuforums.org/showthread.php?t=101817](http://www.ubuntuforums.org/showthread.php?t=101817)

---

### Post by altonbr on 2007-03-05
Bump.

---

### Post by altonbr on 2007-03-06
Also, Folding@Home is well supported in the Ubuntu Wiki as seen here: [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

How come it's not in the repositories?

---

### Post by D!mon on 2007-03-07
yeah, it would be really cool if F@H will be included into repositories.. maybe there is possibility for 7.04?

---

### Post by drezha on 2007-03-10
It's against the End User Lience Agreement to get the Folding at Home client from anywhere but the Folding at home website.

Thus it will never be in the repositories.

BUT
using finstall (here [http://www.vendomar.ee/~ivo/finstall](http://www.vendomar.ee/~ivo/finstall)) works just as well to grab the client, set it up and start it as a service. :)

---

### Post by altonbr on 2007-03-10
WOW, why is that installer SO BIG!???

I've been referred to this as well from the Folding-community.org forum: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=261257](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=261257), but it looks unpromising.

---

### Post by drezha on 2007-03-11
I'd hardly call 150kb big...

What do you want? Downloading that set it up as a serivce and everything.

Possibly if that finstaller was packaged into the repo with a script that as soon as it downloaded it ran and offered you the choices etc to install it would that be what you wanted?

---

### Post by altonbr on 2007-03-11
No no no, it sounds perfect. I was just surprised at the length of coding.

I'll look forward to this *trick*, because it's not actually a "package" correct, it's just an installer that will be hosted in the repos?

---

### Post by D!mon on 2007-03-12
I believe that there some packages that are 'just installers' in the repos, flashplayer for example

---

### Post by altonbr on 2007-04-22
> **D!mon said:**
> I believe that there some packages that are 'just installers' in the repos, flashplayer for example

Ok, well any news on when this will be implemented? I hope that it's backported back to at least Dapper..

---

### Post by Megatog615 on 2007-04-27
> **drezha said:**
> It's against the End User Lience Agreement to get the Folding at Home client from anywhere but the Folding at home website.

Thus it will never be in the repositories.

BUT
using finstall (here [http://www.vendomar.ee/~ivo/finstall](http://www.vendomar.ee/~ivo/finstall)) works just as well to grab the client, set it up and start it as a service. :)
You could make a package that downloads it from their website and installs it, just like flashplugin-nonfree.

---

### Post by altonbr on 2007-09-16
> **Megatog615 said:**
> You could make a package that downloads it from their website and installs it, just like flashplugin-nonfree.

Yes, that would make the most sense.

Anyone know of progress done on this?

---

