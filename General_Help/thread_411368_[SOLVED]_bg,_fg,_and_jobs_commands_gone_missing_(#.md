---
title: "[SOLVED] bg, fg, and jobs commands gone missing? (#1 PREEMPT?)"
date: 2007-04-16
forum: General Help
---

### Post by Phrawm48 on 2007-04-16
I feel like I've lost my mind.  I could've sworn I had built-in *bash* commands for listing running jobs (j*obs*), or putting jobs into the background (*bg*) or foreground (*fg*).  Today, running Ubuntu 6.06 (Dapper) and *bash*, I seem to no longer have any vestiges of them(?)

A few days ago I used Synaptic to auto-update my kernel.  So I get the following response to a *uname* command:

> ric@ric-desktop:~$ uname -a
Linux rbv-desktop 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux
(And Holy Cow, what does that big PREEMPT mean?  Eek!)

Anyhow, now for *bg*, *fg*, or *jobs*:[LIST]
[*]If I type them at the *bash* prompt, all I get is a new prompt -- no other activity or action
[*]If I use *apropos* or *man*, I receive no "hits" for them
[*]If I use *locate*, I can't find them as command type listings[/LIST]Third-party documentation (books) indicates that *bg*, *fg*, and *jobs* are in fact *bash* commands.  So can anyone please suggest what might have happened to them?  Or have I indeed lost my little mind?

Cheers & thanks,
Ric
SFO

---

### Post by rmemm on 2007-04-16
fg, bg, etc are bash builtins -- if your using bash you should have them.

use "help" or "help fg" to see these builtins.  Or use "man bash" as they will be documented with the bash documentation.

Also make certian your running bash.  At what you think is the bash prompt just type "bash" to explicity launch bash as a sub process shell and then see if you have the commands.  If this fixed the problem -- then your running some other shell maybe.  At work I often have to say "bash" becauce they use tcsh as the default for some reason.

Just a thought.

Rob

---

### Post by Phrawm48 on 2007-04-16
Yeah, OK, thanks -- the "help [command]" approach showed that they're there alright.

I guess I'm mangling the syntax or usage in some way.  Well, that's more easily correctable than if the commands had truly gone missing...

Cheers & thanks 'gain,
Ric
SFO

---

