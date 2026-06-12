---
title: "Disabling sudo..."
date: 2008-06-21
forum: General Help
---

### Post by dpastern on 2008-06-21
I'm an old hand and prefer su, rather than sudo.  I have disabled sudo.  The problem now is that I cannot go to System > administration > software sources (or update manager for that matter), not without me getting an error message (see attached screendump)...frustrating!

[IMG]http://www.macro-images.com/error.jpg[/IMG]

Does getting rid of sudo break the admin stuff in Ubuntu, if so that's pretty lame imho...

Is there a way to fix this, if so how?  I did some searching in the forums but couldn't really find an answer...

synaptic works from the command line, as does apt-get etc.

Any help appreciated.

Cheers,

Dave

edit: bodhi.zazen : Information deleted.

---

### Post by Barriehie on 2008-06-21
<edit> Never mind! </edit>

Don't know about reenabling sudo but perhaps next time alias sudo to something like 'Command not found...' or whatever.  That way when you need it it's not far away.

Barrie

---

### Post by bodhi.zazen on 2008-06-21
> **dpastern said:**
> I'm an old hand and prefer su, rather than sudo.  I have disabled sudo.  The problem now is that I cannot go to System > administration > software sources (or update manager for that matter), not without me getting an error message (see attached screendump)...frustrating!

Does getting rid of sudo break the admin stuff in Ubuntu, if so that's pretty lame imho...

Is there a way to fix this, if so how?  I did some searching in the forums but couldn't really find an answer...

synaptic works from the command line, as does apt-get etc.

Any help appreciated.

Cheers,

Dave

We understand how you feel (I myself came from a rpm system and sudo was annoying at first).

However, most of us, including myself, have learned to prefer sudo. sudo is quite secure and quite powerful and, IMO, you should give it a try before you blindly disable it.

[uwiki]RootSudo[/uwiki]

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

At any rate, posting the kind of information re: disabling the root account is against forums policy.

[New forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201") 

As you indicated there are many off site tutorials on how to do this and if yo wish to publish this kind of information please do it off site as well.

FYI the "proper" way to access root is with sudo -i or gksu

sudo -i is akin to su -

Yes, there are times when enabling the root account or logging in a root is required, but that is rare.

---

