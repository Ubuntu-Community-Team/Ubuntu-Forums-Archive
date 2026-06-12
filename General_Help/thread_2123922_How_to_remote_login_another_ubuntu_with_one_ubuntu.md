---
title: "How to remote login another ubuntu with one ubuntu"
date: 2013-03-09
forum: General Help
---

### Post by iPhilip on 2013-03-09
I have searched some website and I know three ways.
1.telnet
2.ssh
3.vnc

Is there other easier method?

Thank u!

---

### Post by agillator on 2013-03-09
It depends upon what you want to do to some extent. If you are wanting a remote X-Window session, vnc is probably the way to go although it can be done with ssh. If you are wanting a shell session, ssh is probably the way to go. If any part of your link is unsecure or not trusted to ANY degree, I would not use telnet. If you are trying to mirror directories or disks, use rsync which is in effect using ssh. To simply transfer individual files use scp which is again using ssh. To run a single XWindow program I find ssh works well. For a real remote session, some form of vnc would probably be best. You will find a number of programs/methods to do various things though all that I know of end up coming back to some form of vnc or ssh. That's the long answer. The short answer is there may be but I can't think of any, partially because vnc or ssh in some form or other have served all my needs.

---

### Post by SeanBlader on 2013-03-10
I have to agree with what Gill said, but more specifically. VNC is the "simple" solution you're looking for. 

Ironically though I've never bothered to figure it out, SSH gets it done when usually the only thing I want to run remotely is a code editor and that's just because I don't want to contaminate my personal desktop with a bunch of work garbage. Once you've used the terminal a few times it's usefulness with SSH is much more palatable.
ssh -X [email]user@host.domain.com[/email]

That will let you run your applications if they are on your system path which most automatically are. And if you want to run more than one at a time, append it with an ampersand.

firefox &
evolution &

Then you get both applications and back to a command line in case there are more you want.

---

### Post by iPhilip on 2013-03-11
Thank u  agillator! Thank u seanblader!

---

