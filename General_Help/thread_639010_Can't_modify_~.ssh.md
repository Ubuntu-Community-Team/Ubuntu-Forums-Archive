---
title: "Can't modify ~/.ssh"
date: 2007-12-12
forum: General Help
---

### Post by swalsh76 on 2007-12-12
Hey peeps,

I'm sure this is an easy answer, probably due to the fact I'm more familiar with how other dists do things.

When I ssh to a host for the first time, ssh of course asks me if I want to add the key to my list of known hosts.  So I type out 'yes' and then it promptly tells me:

*Failed to add the host to the list of known hosts *

So, after I do it again (figuring I just imagined I typed yes) and it failing again, I try to go over to ~/.ssh/known_hosts to see what's up, and it won't let me.  I see that .ssh is set up as such: 

drwx------  2 root  root  4096 2007-12-11 15:54 .ssh

Now, I could go in as root and chown it over to my main user account, but is that the "Ubuntu way", or am I asking for a headache when I go do that?

Thanks!

---

### Post by p_quarles on 2007-12-12
Well, my ~/.ssh folder is owned by my user, with permissions set at 755. The known_hosts file is also owned by me, with permissions set at 600. Those are the default, so I'm not sure how you got this set up with root ownership.

---

### Post by swalsh76 on 2007-12-12
>  Well, my ~/.ssh folder is owned by my user, with permissions set at 755. The known_hosts file is also owned by me, with permissions set at 600. Those are the default, so I'm not sure how you got this set up with root ownership.

Yeah, I did a pretty standard install, (and haven't see than it other dists) so I'm not sure how it ended up that way, either.

---

### Post by p_quarles on 2007-12-12
Yeah, I would just go ahead and change it to the correct settings.

---

### Post by swalsh76 on 2007-12-12
Already done.  Thanks.

---

