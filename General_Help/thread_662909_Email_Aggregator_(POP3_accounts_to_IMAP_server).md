---
title: "Email Aggregator (POP3 accounts to IMAP server)"
date: 2008-01-09
forum: General Help
---

### Post by deejross on 2008-01-09
Hello everyone,

I've seen this question asked before with few results or with convoluted answers. What I want to do is set up an IMAP server that gathers mail from other POP3 servers. This would be for multiple users, so I would need one IMAP server to collect mail for about 50 POP3 accounts, the only problem is that I don't want to create a linux user account for every person. A list of users and their pop3 account info in a text file would be perfect, though I would settle for a SQL-based solution.

It needs to be easy to setup, and easy to add/remove accounts. So a detailed how-to would be awesome. Thank you in advance for help.

Ross

---

### Post by jeffus_il on 2008-01-09
Opening fifty GMail accounts would do it for you, imap, and fetch pop, no overhead, no maintenace, 4Gb for each account, and ZERO $

---

### Post by deejross on 2008-01-09
I thought about that, but it would kill our bandwidth having everyone constantly connected to gmail. That's why the internal IMAP server approach sounded so good. Plus the fact that we need to backup all of our emails. Regardless of how well Google backs up gmail, we are required to have our own backups. Right now, everyone uses Outlook and we force them to backup their PST files every night.

So long story short, we need an in-house solution. But that was thinking out of the box and I appreciate your quick response :)

---

### Post by deejross on 2008-01-10
I did see something once where someone used getmail and dovecot, but it was based on linux user accounts. Anyone have any ideas?

---

### Post by jeffus_il on 2008-01-10
This may be what you're looking for:
[http://gentoo-wiki.com/HOWTO_Fetch_mails_from_multiple_POP/IMAP-mailboxes_and_export_them_via_IMAP_to_Thunderbird/SquirrelMail_etc](http://gentoo-wiki.com/HOWTO_Fetch_mails_from_multiple_POP/IMAP-mailboxes_and_export_them_via_IMAP_to_Thunderbird/SquirrelMail_etc)

It's for gentoo, but the logic is there, replace emerge with apt-get ...

---

### Post by deejross on 2008-01-10
Yea, that's the howto that tries to use getmail and dovecot, but requires linux user accounts.

---

### Post by jeffus_il on 2008-01-10
Do you want to access the imap account from one user only?

---

### Post by jeffus_il on 2008-01-10
Dovecot supports real or virtual users, have you looked into virtual users (i.e. users not in /etc/passwd) as a solution?

---

### Post by deejross on 2008-01-10
I'm actually reading up on it now: [http://wiki.dovecot.org/HowTo/SimpleVirtualInstall](http://wiki.dovecot.org/HowTo/SimpleVirtualInstall) Looks promising. But now how do i get fetchmail or getmail to deliver the mail? Oh, and on a side note, the server I'm trying this on doesn't have getmail in the repositories, so I may not be able to use that one.

---

### Post by jeffus_il on 2008-01-10
I am not an expert on this, I am researching like you,
Could you implement the getmail as the gentoo tutorial advises and have users access the imap server as virtual users, that is the imap server authenticates them, not  /etc/passwd, should be a small change to the tutorial.

---

### Post by deejross on 2008-01-10
Ok, I think it's working now. This is what I did

[http://www.odrakir.com/blog/2006/08/26/your-own-personal-mail-server/](http://www.odrakir.com/blog/2006/08/26/your-own-personal-mail-server/)

However, I had to make ALOT of changes to get it to work properly:
[LIST]
[*]While editing dovecot.conf, uncomment the line "disable_plaintext_auth = no". This allows clients like Outlook to log in.
[*]Also set "first_valid_uid" and "last_valid_uid" to the UID of the "mail" user. You can find this number user the Users and Groups window under System -> Administration in Gnome. Since we are using virtual users, only the "mail" linux user is actually being used, so you have to allow its UID.
[*]There is no "mail_location" property and setting it will give you an error, so instead, you have to set the "default_mail_env" property like so: "default_mail_env = maildir:/var/mail/%u/Maildir". This way, when a user logs in, the maildir directories get created automatically by dovecot.
[*]You will also need to chown the /var/mail directory. Dovecot creates the "mail" user when installed, and sets the user's home directory to "/var/mail".
[*]To allow users to create subfolders in the Inbox folder, I had to add this to dovecot.conf:
```

namespace private {
     separator = /
     prefix = Inbox/
     inbox = yes
}

```
[*]The slash at the end of Inbox/ is important
[*]Under "protocol imap {", uncomment "imap_client_workarounds = outlook-idle". To workaround an Outlook bug involving being idle for too long and getting disconnected.
[*]Under "auth default {", make sure "mechanisms = plain" is uncommented
[*]Uncomment the line "passdb passwd-file {" along with the closing "}" just below it
[*]Then set the "args" property: "args = /etc/dovecot/passwd".
[*]Do the same thing with "userdb static {".
[*]But set the args for this one to: "args = uid=mail gid=mail home=/var/mail/%u"
[*]Now create the file "/etc/dovecot/passwd", and make the user "dovecot" the owner, and set group to "dovecot". This is the file that will store the virtual users.
[*] To setup the virtual users, just follow this: [http://wiki.dovecot.org/HowTo/SimpleVirtualInstall](http://wiki.dovecot.org/HowTo/SimpleVirtualInstall)
[*]When installing getmail, the package name is "getmail4", not "getmail".
[*]Make sure that the user "mail" owns EVERYTHING under "/var/mail".
[*]While writing the rc file for getmail, under [destination], set the path property: "path = /var/mail/USERNAME/Maildir/". Replace USERNAME with the username from the /etc/dovecot/passwd file you created. And notice the slash at the end of Maildir/ because it is important.
[*]While writing the rc file for getmail, under the [options] section, set "delete = false" while testing. And while testing, you will need to add the option "read_all = false" or you will get duplicate messages in your inbox every time getmail runs
[/LIST]

At this point, if you're not totally lost, it should be working. In fact, I'm pretty sure no one, including myself, would be able to get this working by following this post :p and for that, I apologize. Maybe if I get some time today, I'll make a proper how-to for the wiki. But for now, I hope this helps someone out there.

---

### Post by jeffus_il on 2008-01-10
Nice work DJ! I may implement it myself in a few days.

---

### Post by deejross on 2008-01-10
I started a wiki page for it at [https://wiki.ubuntu.com/Pop3Aggregator](https://wiki.ubuntu.com/Pop3Aggregator) which should be MUCH easier to follow.

---

### Post by eldragon on 2008-03-28
i followed the wiki and now i got a personal local imap server.

just pointing out it works great under hardy beta.

there are a couple of differences in the config file, but nothing important to point out (some variables have already something....just follow the wiki blindfolded and it should work.

thanks a lot. great wiki

---

### Post by deejross on 2008-03-28
Glad to hear it works in Hardy. I was beginning to wonder about that the closer we get to the official release date. For anyone else thinking about doing the same thing, I have had this running for the last 3 months flawlessly. I couldn't have hoped for a better result. The only thing I noticed is that even though Outlook 2003 can connect to the IMAP server, it doesn't work very nicely. Not the server's fault, but Outlook's crappy implementation of the imap protocol. I ended up using Thunderbird on my Windows machine at work (as well as on my Ubuntu machine at home). After adding the Lightning + GCAL add-ons to Thunderbird, I now have a complete Outlook replacement that uses Google Calendar, so now everything is shared between my work and home machines.

---

