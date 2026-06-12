---
title: "SMTP server for localhost only"
date: 2007-06-26
forum: General Help
---

### Post by Jamie Jackson on 2007-06-26
I've got Ubunty Feisty desktop.

What's the quickest way for me to be able to send mail from localhost-only?

Use case: Send an email to external recipients (gmail, hotmail, etc.) from my machine (the same machine that hosts the SMTP service). However, disallow any other external relaying.

I was preparing to install sendmail (as it's the only Linux mailer I've heard of); however, when I went into Synaptic, it says:

[INDENT]Sendmail is an alternative Mail Transport Agent (MTA) for Debian.[/INDENT]

...which leads me to believe that sendmail is not the standard Ubuntu SMTP app. If it's not, what is?

Thanks,
Jamie

---

### Post by reclusivemonkey on 2007-06-27
I'm not quite sure what you mean here. The easiest way to send mail via SMTP would be to use your current ISP's SMTP server; do they not provide you with one?

---

### Post by Jamie Jackson on 2007-06-27
I do programming at work. The work SMTP doesn't allow me to relay from it, as my IP changes when VPNed in, etc, and IP# is how they're doing allowed relayers.

I'd prefer not to rely on their SMTP server or my ISPs SMTP, as I'd always have to switch back and forth depending on where I was. Or, say I were hacking at the local coffee shop, I wouldn't be able to do email-related development from there....

That sort of thing.

Does that make sense?

Thanks,
Jamie

---

### Post by reclusivemonkey on 2007-06-27
> **Jamie Jackson said:**
> 

That sort of thing.

Does that make sense?

Thanks,
Jamie

Ah, yes certainly. I see where you are coming from now. I believe exim is the default MTA used by Ubuntu, and should be installed by default (you should notice local mail delivery working). If you look in Synaptic, there is quite a bit of information which should point you where you need to look into getting this working how you want to. I'm afraid we're rapidly leaving my comfort zone, but if you don't find what you need, please post back =]

---

### Post by dcstar on 2007-06-28
Install the **postfix** package.

---

### Post by scxtt on 2007-06-28
yes, install **postfix** and **mailx** - then you can do:

mailx -s "subject" [email]user@email.com[/email] < input_file.txt

or

mailx -s "subject" [email]user@email.com[/email] [hit enter]
this is the text of the email [enter]
CTRL-D
Cc: [enter]
[ mail sent! ]

---

