---
title: "[SOLVED] Bibus with Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by squaregoldfish on 2007-10-20
I've just upgraded to Gutsy, and Bibus has unfortunately stopped working with a locale issue. Whenever I run it, I get the following output:


Traceback (most recent call last):
  File "/usr/bin/bibus", line 67, in <module>
    locale.setlocale(locale.LC_ALL,'en_US')                             # use english if any problem
  File "/usr/lib/python2.5/locale.py", line 478, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


The package was already installed in Feisty when I upgraded, but a complete removal and reinstall results in the same error.

Since my knowledge of Python is approximately nil, can anyone give me any pointers towards getting Bibus up and running again?

Thanks,
Steve.

---

### Post by AKoine on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077](https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi there,

Well, I don't really know how its works, but this bug as been reported in launchpad (bug #139077 [https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077](https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077)).

The workaround :

```
sudo ldconfig -v /usr/lib/openoffice/program
```

It worked for me ...

Hope this'll help.

---

### Post by squaregoldfish on 2007-10-22
You, sir, are a gentleman and a scholar. Your solution is flawless.

Thanks,
Steve.

---

### Post by Spoker on 2007-11-02
Thank you! It solved my problem too...

But, what does this command actually do?

---

### Post by aliennet on 2007-11-12
Great man!

---

### Post by rGb1707rGb on 2007-11-28
> **AKoine said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077](https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi there,

Well, I don't really know how its works, but this bug as been reported in launchpad (bug #139077 [https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077](https://bugs.launchpad.net/ubuntu/+source/openoffice.org2/+bug/139077)).

The workaround :

```
sudo ldconfig -v /usr/lib/openoffice/program
```

It worked for me ...

Hope this'll help.

It works fine. Thanks.

---

