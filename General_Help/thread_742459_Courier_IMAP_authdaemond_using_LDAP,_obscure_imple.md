---
title: "Courier IMAP authdaemond using LDAP, obscure implementation detail"
date: 2008-04-01
forum: General Help
---

### Post by eode on 2008-04-01
I know this is only one small detail, but I wanted it to be here so that it's more available on the interwebs, because I searched the google and I had much lack of dice.

For the problem where:
authdaemond is not connecting to the LDAP server, even though:

[LIST]
[*]It *is* listed as a module in authdaemonrc
[*]Using 'authtest <username>' works, correctly returning user info
[*]Running slapd in debug mode shows that authdaemond is not even *trying* to connect to to the ldap server
[/LIST]

The solution to your problem may be this:
in authdaemonrc, add the following line (I did so above the 'authmodulelist' line):

```
version="authdaemond.ldap"
```

..obscure.  Not in the comments in the config file.  Hard to find on the intertubes.  ..at least, it was, until you found this.  you know who you are.  :-)

---

