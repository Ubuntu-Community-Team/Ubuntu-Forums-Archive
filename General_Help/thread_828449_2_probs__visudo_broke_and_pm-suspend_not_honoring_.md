---
title: "2 probs:  visudo broke and pm-suspend not honoring sudoers priveleges"
date: 2008-06-13
forum: General Help
---

### Post by usnmustanger on 2008-06-13
[COLOR="Silver"]I actually have two problems:  First, I successfully edited the sudoers file (not using visudo--more on that in a minute) as suggested [here]("http://wiki.archlinux.org/index.php/Pm-utils#Execute_suspend.2Fhibernate_without_root_password") by adding the following lines (with my user name substituted for "username"):
```
username  ALL = (ALL) NOPASSWD: /usr/sbin/pm-hibernate
username  ALL = (ALL) NOPASSWD: /usr/sbin/pm-suspend

```However, typing pm-suspend in terminal still gives me the following error:
> This utility may only be run by the root user.With the change to sudoers, why can't I invoke pm-suspend without the root password?[/COLOR]

**EDIT:**  Nevermind--I'm a bonehead.  I still have to put the *sudo* before pm-suspend, I'm just not asked for a password now.  So the first problem is a problem no more (actually never was).

Okay, second problem, encountered when trying to do the above:  visudo isn't working quite right--that is, I can't type in visudo--typing "i" to enter "insert mode" (a la vi or vim) does nothing--except enter the letter i.  Also, using arrow keys to try to scroll around actually enters the letters A, B, C, and D, rather than actually scrolling.  The escape key does nothing.  As soon as I execute visudo, I can type text--but not delete it, nor change cursor position (b/c of the arrow key problem mentioned above).  Trying to copy text in is also a futile effort.  About the only thing that does work right is entering :q! to quit visudo.  So visudo is completely unusable.  Any ideas why?
Is visudo broke?

Here's my system info:
Panasonic CF-48 Toughbook laptop
Ubuntu Hardy Heron 8.04
Latest updates as of 13 June 08.
Using any terminal emulator under Openbox in standalone mode.

TIA!

---

