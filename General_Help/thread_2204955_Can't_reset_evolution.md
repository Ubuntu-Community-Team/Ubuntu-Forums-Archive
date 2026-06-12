---
title: "Can't reset evolution"
date: 2014-02-11
forum: General Help
---

### Post by mune on 2014-02-11
Hi all

I've been able to save my mails in many mbox files, if evolution won't work I'll use firebird but I don't like this solution.

As I had a couple of google calendars not working and two existing google mail account that, without any reason (I tried gnome3, but INMHO it doesn't matter), become type imapx, I decided to start evolution from scratch.

I did a lot of google search and I end up with the commands

```
gconftool-2 --shutdown
rm -rf ~/.local/share/evolution
rm -rf ~/.gconf/apps/evolution
rm -rf ~/.cache/evolution
dconf reset -f /org/gnome/evolution/
gconftool-2 --recursive-unset /apps/evolution
```

and to check with
```
dconf reset -f /org/gnome/evolution/
```

The output should be null instead I get a long XML.

Any help will be appreciated. Thanks.

Obviously when I launch evolution again I found that something is still there (those accounts of type imapx).

---

### Post by Kirboosy on 2014-02-11
It looks like these commands worked for someone else who used a fairly recent version of Evolution. Hopefully your experience will be the same.

```
$ rm -rf ~/.local/share/evolution
$ rm -rf ~/.gconf/apps/evolution
$ rm -rf ~/.cache/evolution 
$ evolution --force-shutdown
```

Find the process id for &#8216;gconfd&#8217; and kill it
```

$ ps -ef|grep gconfd
*yourusername 12345** 1 0 13:24 ? 00:00:00 /usr/libexec/gconfd-2*

$ kill 12345

```

```
gconftool-2 --recursive-unset /apps/evolution
```

Hope that helps!
~Caboose

---

### Post by mune on 2014-02-11
@ Caboose
Thank for your help: I tried the way you suggested but the result was like this morning, last night, yesterday afternoon and yesterday morning.

As I already pulled the mbox files out of the evolution maildir files I give up and I'm going to use Firebird.

---

### Post by mune on 2014-02-11
I'm back.

I don't like thunderbird: I want back my evolution.

---

### Post by Kirboosy on 2014-02-14
So if you go Under Evolution Preferences it won't let you delete the accounts that are there manually? (Edit -->Preferences-->Mail Accounts)

---

### Post by mune on 2014-02-14
I confirm I couldn't undelete the two remainig accounts.

I tried to "apt-get purge evolution" and later "apt-get install evolution": but nothing.

Finally I take the moment to move to 13.10 (with gnome3). It looks as I changed for a different PC :-)

Thanks for the help

---

