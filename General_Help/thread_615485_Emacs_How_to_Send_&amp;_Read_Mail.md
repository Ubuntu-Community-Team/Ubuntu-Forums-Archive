---
title: "Emacs: How to Send &amp; Read Mail?"
date: 2007-11-17
forum: General Help
---

### Post by Arhuma on 2007-11-17
[SIZE="2"]Hello,

I've installed Emacs 22.1.1 (i486-pc-linux-gnu, GTK+ Version 2.10.11) on my Xubuntu 7.04 system. In all manuals and How To's out there it is said that it can be used to send and read mail so I want to use this feature,  I'm not interested in programming. So I go to Tools>Send Mail and I get a new buffer with mail headers, while in the lower bar it says: "Customize regexp:"  What do I have to write here?

I guess I have to tell Emacs what my POP and SMPT servers are, but can't figure out how to do it, 
which is the file I have to modify, create or whatever I have to do? Can someone please help? 

Arhuma[/SIZE]

---

### Post by Embedded Linux Guy on 2007-11-17
There are several choices of client for reading your mail in Emacs.  The one I use is Wanderlust; the Ubuntu package is called "wl-beta".  Configuring Wanderlust will require you to edit Emacs Lisp files.  These are the values to customize in ~/.wl to set your mail server:

(setq wl-smtp-posting-server "mail.your-server.com")
(setq elmo-pop3-default-server "mail.your-server.com")

You probably want to start by copying the default ~/.wl to your home directory:

cp /usr/share/doc/wl-beta/examples/en/dot.wl.gz /tmp
gzip -d /tmp/dot.wl.gz
mv /tmp/dot.wl ~/.wl

If you are interested to try Wanderlust, I would start with this Wiki link, then install it and read the manual entry inside Emacs (as in, "C-h i g(wl)").
[http://www.emacswiki.org/cgi-bin/wiki/WanderLust](http://www.emacswiki.org/cgi-bin/wiki/WanderLust)

VM and Gnus are other Emacs mail readers.  If you are only interested in sending mail, you can use these examples to configure smtpmail:

[http://emacswiki.org/cgi-bin/wiki/SendingMail](http://emacswiki.org/cgi-bin/wiki/SendingMail)

---

### Post by Arhuma on 2007-11-22
> **Embedded Linux Guy said:**
> There are several choices of client for reading your mail in Emacs.  The one I use is Wanderlust; the Ubuntu package is called "wl-beta".  Configuring Wanderlust will require you to edit Emacs Lisp files.  These are the values to customize in ~/.wl to set your mail server:

(setq wl-smtp-posting-server "mail.your-server.com")
(setq elmo-pop3-default-server "mail.your-server.com")

You probably want to start by copying the default ~/.wl to your home directory:

cp /usr/share/doc/wl-beta/examples/en/dot.wl.gz /tmp
gzip -d /tmp/dot.wl.gz
mv /tmp/dot.wl ~/.wl

If you are interested to try Wanderlust, I would start with this Wiki link, then install it and read the manual entry inside Emacs (as in, "C-h i g(wl)").
[http://www.emacswiki.org/cgi-bin/wiki/WanderLust](http://www.emacswiki.org/cgi-bin/wiki/WanderLust)

VM and Gnus are other Emacs mail readers.  If you are only interested in sending mail, you can use these examples to configure smtpmail:

[http://emacswiki.org/cgi-bin/wiki/SendingMail](http://emacswiki.org/cgi-bin/wiki/SendingMail)

I'm interested in sending and also reading mail. Some tools  are already included in Emacs22, so I would rather use those just to make my life easier.  From the menu:

Tools > Read Net News (Gnus)
Tools > Read Mail (with RMAIL)
Tools > Send Mail (with sendmail) (C-x m)

What would be the advantage of using WanderLust intead?

---

### Post by Embedded Linux Guy on 2007-11-26
> **Arhuma said:**
> 
Tools > Read Net News (Gnus)
Tools > Read Mail (with RMAIL)
Tools > Send Mail (with sendmail) (C-x m)

What would be the advantage of using WanderLust intead?

I have not used Gnus or RMAIL so I can't comment on these.  However I like Wanderlust because it has a nice 3-pane view (folders on the left, subjects on top, message on bottom) as in Thunderbird.  It also has excellent support for IMAP folders, which is why I switched to Wanderlust from VM.

---

### Post by Arhuma on 2007-11-30
> **Embedded Linux Guy said:**
> I have not used Gnus or RMAIL so I can't comment on these.  However I like Wanderlust because it has a nice 3-pane view (folders on the left, subjects on top, message on bottom) as in Thunderbird.  It also has excellent support for IMAP folders, which is why I switched to Wanderlust from VM.

That sounds interesting. In fact, Gnus and RMAIL have ugly interfaces. I was able to configure them to read and send mail, but as they are so ugly, I don't use them! I just thought of using them as they  are already included  in Emacs, so  as to save disk space (I have a small disc). 

Thank you for your answers.

Arhuma

---

