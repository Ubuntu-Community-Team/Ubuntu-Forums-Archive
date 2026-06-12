---
title: "Evolution and loading images"
date: 2007-06-14
forum: General Help
---

### Post by z_diver on 2007-06-14
Hello to all!

I've been running Dapper with Evolution 2.6.1 in imap mode since it came out.  In all honesty I've been very happy with it.  The exception being html messages with embeded images.  It's too sloooowwww there.  I have Evo set to only download images from senders in my address book although setting it to download all images doesn't seem to make it download images faster.

Does anyone know how to speed this process up and if not, does anyone know if newer versions of Evo are faster in this regard.  If so, it'd be great if I could simply build it on my Dapper box as I have no other reason to upgrade.

Hanks in advance.

---

### Post by foxmulder881 on 2007-06-14
I had this same problem when I was running Dapper. Since upgrading to Feisty, it's muchy better. I think it's an issue with the older versions, maybe.

---

### Post by z_diver on 2007-06-14
Thanks for responding.  I have run Evo on a few fiesty boxes and it seems faster.  Just wasn't sure if it would stay that way after it's loaded with all my mail like my current install.

If you don't mind my asking, how long have you been running it and are you using IMAP?

---

### Post by foxmulder881 on 2007-06-14
> **z_diver said:**
> Thanks for responding.  I have run Evo on a few fiesty boxes and it seems faster.  Just wasn't sure if it would stay that way after it's loaded with all my mail like my current install.

If you don't mind my asking, how long have you been running it and are you using IMAP?

I've been running it since I was first release.\

I'm using POP3.

---

### Post by z_diver on 2007-06-14
That's interesting that you also noticed the slowness of images loading with Pop3.  I guess it was a problem with Evo 2.6.1 rather than just their implementation of the imap4 protocol which is what I was thinking.

---

### Post by foxmulder881 on 2007-06-15
I think you're right. I think it was just older versions of Evo. I had times when images wouldn't even load at all. All the niggles seem to be ironed out in recent versions though.

---

### Post by Midahed on 2007-06-20
I'm running Evolution 2.10.1 on Ubuntu 7.04 Feisty 64-bit.  I'm quite happy with it apart from one silly problem.  I receive daily HTML mails from a number of sites.  These work fine except for two sites where the embedded images are never displayed - all I get is the usual blank space with a small box in the top-left corner with a red cross in it.  The status bar indicates that Evolution is 'retrieving' from the site, but it never progresses beyond 0% complete.  The plain text content of the mail is displayed normally.

I've seen posts elsewhere where Evolution users complain about similar problems.  Is this a common problem/known bug?

Any suggestions as to how I might cure it?

[Edit] ...Forgot to say that, yes, the option 'always receive images from the internet' in HTML preferences is ticked.

Thanks,

Mike

---

### Post by stchman on 2007-06-20
> **z_diver said:**
> Hello to all!

I've been running Dapper with Evolution 2.6.1 in imap mode since it came out.  In all honesty I've been very happy with it.  The exception being html messages with embeded images.  It's too sloooowwww there.  I have Evo set to only download images from senders in my address book although setting it to download all images doesn't seem to make it download images faster.

Does anyone know how to speed this process up and if not, does anyone know if newer versions of Evo are faster in this regard.  If so, it'd be great if I could simply build it on my Dapper box as I have no other reason to upgrade.

Hanks in advance.

I never load images, but when I do it is sometimes a little slow.  My big thing is that Evolution takes forever to empty the trash.

All in all for a free email client it is very good.  I give it an 8/10 for functionality and a 10/10 on value.  I like it because it behaves exactly like Outlook.

---

### Post by Ajc on 2007-11-04
Hi - I'm having the same problem re images loading at all in Evolution ?!

- all the options are ticked with regards to loading images + the "Ctrl + I" key functions to load images doesn't appear to be working.

any help really appreciated.

Ajc
:confused:

---

### Post by janbockaert on 2008-01-08
same problem here, all options set to load the images, but it is not happening. Evo + gmail IMAP.

---

### Post by dcstar on 2008-01-08
> **Midahed said:**
> I'm running Evolution 2.10.1 on Ubuntu 7.04 Feisty 64-bit.  I'm quite happy with it apart from one silly problem.  I receive daily HTML mails from a number of sites.  These work fine except for two sites where the embedded images are never displayed - all I get is the usual blank space with a small box in the top-left corner with a red cross in it.  The status bar indicates that Evolution is 'retrieving' from the site, but it never progresses beyond 0% complete.  The plain text content of the mail is displayed normally.

I've seen posts elsewhere where Evolution users complain about similar problems.  Is this a common problem/known bug?

Any suggestions as to how I might cure it?

[Edit] ...Forgot to say that, yes, the option 'always receive images from the internet' in HTML preferences is ticked.

Thanks,

Mike

Many "HTML" e-mails do not comply with standards, they are set to be used by Microsoft mail clients using special little tricks only available on those clients, so other e-mail clients like Evolution have trouble with them.

You can try and find another client more "Microsoft-centric", or you can complain to those sending them to you to change the format to meet the standards, not the convenience of Microsoft.

---

