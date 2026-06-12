---
title: "(login) failed to add entry to user"
date: 2008-06-20
forum: General Help
---

### Post by squiddy on 2008-06-20
pls anybody help me on this

i'm new to ubuntu
i got this error "faile to add entry to user" everytime i type username on the login screen.. i able to login to desktop, but this warning is annoying.

also, everytime ubuntu asking for user authentification (while using synaptic manager, update manager etc), there goes another warning says "failed to authenticate" ???

anyone ? really need help here

---

### Post by kerryhall on 2008-06-24
bump

---

### Post by george97477 on 2009-04-09
I know this post is old but it might help someone Googling for an answer.

I'm not an expert but it seems that it's related to the pam authentication modules.
If you are only planing to use Linux local authentication then edit the /etc/pam.d/common* scripts and comment optional authentication lines not needed.

It will help to check your /var/log/auth.log for clues as to which module is causing the issue.

Be careful in modifying authentication as it can cause you not to be able to log in at all.  Leave the Unix authentication modules alone.

Hope this helps.

---

### Post by Captain_Glen on 2009-12-13
I had the same problem.  But the solution is easy.

Just open up System -> Administration -> Users and Groups.

Then click unlock and enter your password.

Then Find the group that is your username and click on it.  Mine was "glen".

Then click properties.  Then make sure you put a tick in the box next to your username.

---

### Post by Captain_Glen on 2009-12-18
Ok my bad.  That didn't fix it.

But this really does (well it did for me anyway):

Open up Synaptic.

search for samba
select completely remove samba and system-config-samba
Hit apply

Log out
Log in.  It should say user added for your username.

Now install samba for the ubuntu software centre.

Your good to go.  

I should point out that I encountered this problem when I removed myself for the list of samba users (I was listed twice so I thought I'd "clean up" by removing one - bad idea!).  If you didn't encounter this problem by messing up samba this fix may not work for you.

---

