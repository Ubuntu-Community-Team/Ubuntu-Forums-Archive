---
title: "[SOLVED] checkgmail turns strange"
date: 2008-07-09
forum: General Help
---

### Post by imjscn on 2008-07-09
I've been using checkgmail for a while, it works fine till today.
When I tried to start it from Applications/Network/checkgmail, no response. so I go to Terminal, sudo checkgmail, and I got this:

[B]Warning: Crypt::Simple not found ...

CheckGmail requires the above packages for password encryption
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) if you want to use this feature ...

Warning: Gtk2::Sexy not found ...

CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) if you want to use this feature ...

Creating translations file at /root/.checkgmail/lang.xml ...
Updating translations file ...
Wide character in print at /usr/bin/checkgmail line 4801.
 ... done![/B]

After this, checkgmail starts. Then, if I close checkgmail and start it from Applications/Network/checkgmail, it still not working. I am confused, what are those messages about? Anything wrong?

---

### Post by imjscn on 2008-07-10
anybody, please?

---

### Post by danielph on 2008-07-20
See post #9 from [this thread]("http://ubuntuforums.org/showthread.php?t=639377") for Warning: Crypt::Simple not found ...problem[B].

[/B]You need a later version of checkgmail

---

### Post by imjscn on 2008-07-20
Thanks, danielph! I'll follow that thread

---

### Post by robert114 on 2008-07-20
```
checkgmail -no_cookies
```

will do the trick as well!

Robert

---

