---
title: "Need fetchmail help"
date: 2007-07-02
forum: General Help
---

### Post by beniwtv on 2007-07-02
Hello,

I'm trying to configure fetchmail, to get e-mails from my server to my local box. Everything works fine, except that I don't want fetchmail to re-write my headers.


Here's my config (fake data):

poll mail.server.com protocol pop3 port 110 username "user@server" password "serverpass" keep no rewrite,
      is [email]root@server.com[/email] here and wants mda "/usr/local/bin/maildrop -V 5 /home/vmail/maildropcustembkp /home/vmail/xxxx/xxx/xxxxx/Maildir/"; 

All works, well, but it just ignores the no rewrite option. :(

Any clue?

Thanks.

---

### Post by andrew.46 on 2007-07-05
Hi,

 Read your post while searching the forums:

> **beniwtv said:**
> Hello,

I'm trying to configure fetchmail, to get e-mails from my server to my local box. Everything works fine, except that I don't want fetchmail to re-write my headers.


Here's my config (fake data):

poll mail.server.com protocol pop3 port 110 username "user@server" password "serverpass" keep no rewrite,
      is [email]root@server.com[/email] here and wants mda "/usr/local/bin/maildrop -V 5 /home/vmail/maildropcustembkp /home/vmail/xxxx/xxx/xxxxx/Maildir/"; 


I have a few suggestions, although I am not completely sure:[LIST=1]
[*]Put your options (such as "no rewrite") after the word "options". This is the syntax that I use.
[*]A long shot but try "norewrite" instead of "no rewrite".
[*]Possibly the most sensible option is to ask the experts who helped me with Fetchmail: The Fetchmail users group
[/LIST]

This mailing list can be accessed from:

[https://lists.berlios.de/mailman/listinfo/fetchmail-users](https://lists.berlios.de/mailman/listinfo/fetchmail-users)

    All the best,

         Andrew


PS My own setup is described here: [http://people.aapt.net.au/~adjlstrong/mutt.html#fetchmail](http://people.aapt.net.au/~adjlstrong/mutt.html#fetchmail)

---

