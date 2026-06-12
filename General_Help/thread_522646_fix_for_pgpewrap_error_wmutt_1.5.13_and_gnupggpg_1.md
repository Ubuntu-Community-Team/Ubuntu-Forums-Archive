---
title: "fix for pgpewrap error w/mutt 1.5.13 and gnupg/gpg 1.4.3"
date: 2007-08-10
forum: General Help
---

### Post by srf21c on 2007-08-10
If you're trying to get gnupg working with mutt 1.5.13 and experiencing a "pgpewrap" error, you need to fix a path.  Make the following changes to the stock gpg.rc file (available at /usr/share/doc/mutt/examples/gpg.rc") then copy into your home directory, and source from your muttrc config file.

BEFORE:

set pgp_encrypt_only_command="[COLOR="Red"]**pgpewrap**[/COLOR] /usr/bin/gpg --batch --quiet --no-verbose --output - --encrypt --textmode --armor --always-trust -- -r %r -- %f"
set pgp_encrypt_sign_command="[COLOR="#ff0000"]**pgpewrap**[/COLOR] /usr/bin/gpg %?p?--passphrase-fd 0? --batch --quiet --no-verbose --textmode --output - --encrypt --sign %?a?-u %a? --armor --always-trust -- -r %r -- %f"

AFTER:

set pgp_encrypt_only_command="[COLOR="#ff0000"]**/usr/lib/mutt/pgpewrap**[/COLOR] /usr/bin/gpg --batch --quiet --no-verbose --output - --encrypt --textmode --armor --always-trust -- -r %r -- %f"
set pgp_encrypt_sign_command="[COLOR="#ff0000"]**/usr/lib/mutt/pgpewrap**[/COLOR] /usr/bin/gpg %?p?--passphrase-fd 0? --batch --quiet --no-verbose --textmode --output - --encrypt --sign %?a?-u %a? --armor --always-trust -- -r %r -- %f"

---

### Post by chiselwright on 2007-08-23
Because I (automatically) open mutt as part of a screen session, I just altered my .screenrc to open mutt like this:
> PATH=$PATH:/usr/lib/mutt/ mutt

I guess you could also (permanently) add it to your path in your .bashrc

---

### Post by andrew.46 on 2008-01-06
Hi,

 I suspect that this is a modification made by Ubuntu, I believe the original gpg.rc file from mutt comes with no hardcoded path. Might be a good case for a bug-report?

My only doubts are:[LIST=1]
[*]I am not running Ubuntu at the moment
[*]The version of mutt I am using is 1.5.17 not the version you are speaking of.[/LIST]However this version, which I compiled from source, comes as:

```
set pgp_encrypt_only_command="pgpewrap gpg --batch --quiet --no-verbose etc etc
```                         

I guess the solution for the Ubuntu devs would be either to write full hardcoded paths within the gpg.rc file or to ensure a change to the path statement is made with the installation or to change the installation path of mutt to fall within the existing, default, path statement.



Andrew

---

### Post by go_beep_yourself on 2008-06-20
Quick question: once I have a configured gpg.rc, what do I need to do inorder to use gpg with mutt emails such as choosing whether to encrypt + sign or just clearsign, etc.?

---

