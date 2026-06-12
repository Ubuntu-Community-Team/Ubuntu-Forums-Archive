---
title: "Giving Ubuntu laptop to a friend - how to clear out all of my personal info"
date: 2014-12-19
forum: General Help
---

### Post by serbriang on 2014-12-19
My neighbor's computer died on him, and as I have an extra laptop I can spare, I offered to give it to him.

I have Ubuntu 14.04 installed on it, and I would like to know if there is a way of simply creating a new admin account for him on the machine, and then deleting my own so that none of my Chrome / Firefox settings remain and that I have no personal information left.

I would prefer to not have to do a clean reinstall, with all the extra tweaking.

Is this possible, and if so, how?

Thanks in advance!

---

### Post by deadflowr on 2014-12-19
You can create new user(and also remove old users) with the gui app: User Accounts. It's in system settings, or do dash search for it.
Simply remember to make the new user admin and not standard.
I think it will auto remove the user's home folder, but if not you can do a quick manual delete/removal of said folder.

I think from a command line you can use usermod, or adduser to make a new user, and use deluser to remove an old one.
So it is possible, and depending on how you feel, quite easy.

Edit:: Personally though, I would just give the neighbor the machine and an install disk so they can set it up how they would want it for themselves.
One of the funner parts is installing everything yourself. Makes it so you can't push your own faults on others...

---

### Post by serbriang on 2014-12-19
Thanks for the reply! That seems much easier than I thought that it would be.

The reason I'm doing everything for him is that he's quite helpless when it comes to computers of any kind. I know that anything involving the terminal may shorten his life!

---

### Post by agillator on 2014-12-19
I agree with DeadFlowr except I would go one step further. I would totally wipe the HD with Darik's Boot and Nuke, then reload Ubuntu or whatever. This is the only real way to be sure all your sensitive info is removed from everywhere. It may not all be in your user directory. For example, SSL certificates could inadvertantly give access to other information elsewhere that you would rather not share, and who knows what you saved or installed where month's (or years) ago. You can also wipe a HD with dd, but Boot & Nuke does a fine job also.

---

### Post by QIII on 2014-12-19
+1 to DBAN.  Friends are only friends until they have your bank information...  :)

---

### Post by mörgæs on 2014-12-19
Have you shown him the various Buntus? It's not a given fact that everyone prefers Ubuntu. 

If he wants another a reinstall is getting closer.

---

### Post by deadflowr on 2014-12-19
> **QIII said:**
> +1 to DBAN.  Friends are only friends until they have your bank information...  :)

Yep, a good wipe is a nice idea.
People give me their old machines all the time, and I'm totally amazed that not once, have they wiped the machine, leaving all their old cruft wide-open for me to see, and use(if i wanted). Fortunately for them I'm nicer than that, but not everybody is.

---

### Post by serbriang on 2014-12-20
> **mörgæs said:**
> Have you shown him the various Buntus? It's not a given fact that everyone prefers Ubuntu. 

If he wants another a reinstall is getting closer.

He was still (to my shock) using XP. He'll be fine with what I give him. ;) If that isn't a good fit, we'll look at something else.

As for the rest of the advice on wiping - I agree. The laptop he's getting is just a test machine that has never had so much as a forum password put on it, so it really isn't necessary in this case.

Thanks all!

---

### Post by mörgæs on 2014-12-20
If it were me I would begin showing him Ubuntu and Lubuntu which is closer to XP in look and feel in Youtube and see what appeals most to him. Just a five minutes test but it could save a lot of disappointment (and support calls to you).

---

