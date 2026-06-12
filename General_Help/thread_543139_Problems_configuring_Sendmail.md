---
title: "Problems configuring Sendmail"
date: 2007-09-04
forum: General Help
---

### Post by jmeissen on 2007-09-04
I'm trying to migrate from a different distro to Ubuntu. I'm running into permissions problems when I try to configure various parts of Sendmail. Switching to something else, like Postfix, isn't an option. I've got custom spam/AV milters, virtual domains, secondary MX support and highly tweaked access files.

I'm running 6.06LTS, and I un-installed Postfix and installed Sendmail. I was able to generate my sendmail.cf file. But when I try to update the various .db files I get permission errors:
 Updating access_db ... 
 makemap: error opening type hash map /etc/mail/access.new.db: Permission denied

I'm running as root. I can create the file manually:
 touch access.new.db
and then re-run make, and that part then works. I can't figure out why I only have permission problems when I'm using the Makefile to update the file(s).

And when I try to rebuild the aliases.db file I get

# newaliases
 hash map "Alias0": unsafe map file /etc/mail/aliases.db: Permission denied
 WARNING: cannot open alias database /etc/mail/aliases
 Cannot create database for alias file /etc/mail/aliases
# ls -l aliases*
 lrwxrwxrwx 1 root  smmsp    10 2007-08-04 12:54 aliases -> ../aliases
 -rw-r----- 1 smmta smmsp 12288 2007-08-04 12:54 aliases.db
# ls -ld /etc/mail
drwxr-sr-x 7 smmta smmsp 4096 2007-09-04 16:26 /etc/mail/

Suggestions? Pointers?

---

### Post by dcstar on 2007-09-05
> **jmeissen said:**
> 
...........
And when I try to rebuild the aliases.db file I get

# newaliases
 hash map "Alias0": unsafe map file /etc/mail/aliases.db: Permission denied
 WARNING: cannot open alias database /etc/mail/aliases
 Cannot create database for alias file /etc/mail/aliases
# ls -l aliases*
 lrwxrwxrwx 1 root  smmsp    10 2007-08-04 12:54 aliases -> ../aliases
 -rw-r----- 1 smmta smmsp 12288 2007-08-04 12:54 aliases.db
# ls -ld /etc/mail
drwxr-sr-x 7 smmta smmsp 4096 2007-09-04 16:26 /etc/mail/

Suggestions? Pointers?

I can only assume that the actual file permissions aren't correct for the user accounts associated with them, how did you copy them from the other system?

As an example, my (Postfix) /etc/aliases & aliases.db files are owner root, group root.

---

### Post by jmeissen on 2007-09-11
> I can only assume that the actual file permissions aren't correct for the user accounts associated with them, how did you copy them from the other system?

They're the original files, as installed by the package. I simply edited them, but the ownership and permissions are untouched. I'm trying to rebuild them as root, since I obviously don't have write permissions as myself.

---

### Post by posterboy on 2007-09-11
Man, I feel your pain. This exact same thing happened when I tried to get sendmail running on ubuntu. I came here from FC6, and, like you, had a highly tweaked sendmail. NEVER got it running. 
I also hit permissions issues in the queue runner, didn't solve that either.
Wound up migrating to postfix, buying a book for it, and spending 2 weeks trimming and tuning.I don't like postfix nearly as well as I liked sendmail, so, if you get solutions, please SHARE, here. 
Thanks, Ray

---

### Post by rodneyr on 2007-10-30
In order to make this work, I discovered that:

(a) the target file must already exist and be world writable
(b) the source file's timestamp must be more recent than the target's timestamp 

For the make to work correctly, I had to make the following changes to Makefile:

%.db: %
        touch $@
        chmod 666 $@
        touch $<
        /usr/sbin/makemap hash $@ < $<
        /bin/chown smmta.smmsp $@

Or, to make a specific hash by hand, you can:
touch target.db
chmod 666 target.db
touch source
makemap hash target.db < source

---

### Post by HermanAB on 2007-10-30
Fortunately, postfix is designed to be a drop-in replacement for sendmail.  So it is an option for you to look into.

---

