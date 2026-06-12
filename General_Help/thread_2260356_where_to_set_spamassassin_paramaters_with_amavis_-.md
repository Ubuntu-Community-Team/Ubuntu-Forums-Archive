---
title: "where to set spamassassin paramaters with amavis - postfix setup?"
date: 2015-01-11
forum: General Help
---

### Post by akos.maroy on 2015-01-11
I'm lost on where to set spamassassin parameters in a 'typical' postfix - amavis - spamassassin setup on Ubuntu 14.04?

I'm trying to set things like:

```
score BAYES_999 1.0
```

I'm trying to set this in /etc/spamassassin/local.cf, in /var/lib/amavis/.spamassassin/user_prefs, but it doesn't have an effect either. where should I put such settings so that they are taken into account?

---

### Post by TheFu on 2015-01-11
```
shortcircuit BAYES_99                spam

```is the setting I'm using. Did something change?

According to the file, **perldoc Mail::SpamAssassin::Conf** has the manpage, though I don't have perldoc installed on my email front-end box so I couldn't check it easily.

---

### Post by akos.maroy on 2015-01-11
> **TheFu said:**
> ```
shortcircuit BAYES_99                spam

```is the setting I'm using. Did something change?

According to the file, **perldoc Mail::SpamAssassin::Conf** has the manpage, though I don't have perldoc installed on my email front-end box so I couldn't check it easily.

yeah, but _where_ do you put this setting? what specific configuration file?

---

### Post by TheFu on 2015-01-11
/etc/spamassassin/local.cf
Putting settnigs that program doesn't understand into the correct file doesn't help.  I'm still on 12.04 here.

---

### Post by akos.maroy on 2015-01-13
> **TheFu said:**
> /etc/spamassassin/local.cf
Putting settnigs that program doesn't understand into the correct file doesn't help.  I'm still on 12.04 here.

that's my point, that putting settings into this file doesn't have any effect. neither of the following take effect:

```
required_score 4.9
score BAYES_999 1.0
```

with both of them being valid spamassassin confirugration settings according to the doc here: [https://spamassassin.apache.org/full/3.1.x/doc/Mail_SpamAssassin_Conf.html](https://spamassassin.apache.org/full/3.1.x/doc/Mail_SpamAssassin_Conf.html)

so the question still is, where should one put these settings?

---

### Post by TheFu on 2015-01-13
When the online document doesn't match what I'm seeing, it usually means my box is running a different version and I need to check the local documents .... or there is a bug that needs to be reported.

Did you try the ```

shortcircuit BAYES_99
```
version?

---

### Post by akos.maroy on 2015-01-20
> **TheFu said:**
> When the online document doesn't match what I'm seeing, it usually means my box is running a different version and I need to check the local documents .... or there is a bug that needs to be reported.

Did you try the ```

shortcircuit BAYES_99
```
version?


I set this as well, and nothing has changed :(

---

