---
title: "E-Mail client for VIM user?"
date: 2007-11-11
forum: General Help
---

### Post by mivo on 2007-11-11
I've recently gotten back into using Vim, and I'm facing my old problem again: My email client, Evolution these days, does not seem to allow the use of an external editor. There was a project aimed at using Vim in Evolution, but it apparently died two years ago. I know that KMail would work, but I try to stay away from KDE applications in Gnome (plus KMail was not the most stable program for me when I used it for some time, and its IMAP support is weak).

What I'm looking for is an email client that supports both POP3 and IMAP, is reasonably fast, can handle a mail base of about 2 GB, has good filters (does not need to filter spam, that's done by the server, but should be able to filter based on custom header lines as well), has a GUI and allows custom fonts (can be simple, but I don't want to do mail in the terminal), and of course supports Vim or an external editor in general. 

I'm not a programmer (well, some Ruby here and there, but that's all), but I work a lot with plain text like mail, documentation, etc., and Vim is quite good for that as well.

Thanks for any pointers!

---

### Post by hugmenot on 2007-11-12
I hate to break it to you, but the best match for Vim as a mail editor is mutt. I just set it up to ue Gmail&#8217;s new IMAP support, and it&#8217;s a joy to use. The integration is smooth and the paradigms are similar (e.g. keystrokes, colors).

---

### Post by kellemes on 2007-11-12
> **hugmenot said:**
> I hate to break it to you, but the best match for Vim as a mail editor is mutt. I just set it up to ue Gmail’s new IMAP support, and it’s a joy to use. The integration is smooth and the paradigms are similar (e.g. keystrokes, colors).

True.. and you can set vim as the editor.

---

### Post by mivo on 2007-11-12
*grin* I did look at Mutt, and I might even get used to it. :) I also found Claws Mail, which has a pretty GUI interface and allows the use of an external editor. Haven't really played much with it yet, though. (They have a repo for Ubuntu at their site.)

---

### Post by avel on 2007-11-12
I use claws-mail myself. It does have some shortcomings and it might look a bit ugly, but it has decent IMAP support, configurable shortcuts, interesting plugins etc.

As mutt's website states, "All mail clients suck". Mutt in the console _does_ suck less, and I might dare to say that Claws-mail is one GUI-client that also sucks less than its equivalents.

Note that you can get updated deb's directly from their website. I think gutsy has a bit older ones.

```
# Claws-Mail
deb http://www.claws-mail.org/ubuntu/gutsy/ ./
```

---

