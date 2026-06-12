---
title: "How to use man2html with 13.10?"
date: 2014-01-11
forum: General Help
---

### Post by stinkeye on 2014-01-11
Used this in previous releases and just required installation of man2html and bookmarking of
[http://localhost/cgi-bin/man/man2html](http://localhost/cgi-bin/man/man2html) in my web browser.

Browser gives error...
```
The requested URL /cgi-bin/man/man2html was not found on this server.
```

I understand that man2html uses some sort of server but what has changed so it no longer works.
I'm also aware of other ways to view man pages like [**_[COLOR="#B22222"]online[/COLOR]_**]("http://manpages.ubuntu.com") or  "**yelp man:[COLOR="#696969"]<insert manpage>[/COLOR]**"
but prefer the man2html method.

---

### Post by steeldriver on 2014-01-12
You may need to enable the apache2 cgi module

```

sudo a2enmod cgid

sudo service apache2 restart

```

---

### Post by stinkeye on 2014-01-12
> **steeldriver said:**
> You may need to enable the apache2 cgi module

```

sudo a2enmod cgid

sudo service apache2 restart

```
You da man. ):P
Up and running. Thanks.

---

### Post by steeldriver on 2014-01-12
I guess it might be worth reporting it as a bug - I assume an installation script is supposed to enable the module

---

### Post by stinkeye on 2014-01-12
> **steeldriver said:**
> I guess it might be worth reporting it as a bug - I assume an installation script is supposed to enable the module

I posted a question as to whether it was a bug or a change.
[https://answers.launchpad.net/ubuntu/+source/man2html/+question/242116](https://answers.launchpad.net/ubuntu/+source/man2html/+question/242116)
The man page seems to have changed but most of that stuff takes the scenic route through my brain.

---

### Post by mc4man on 2014-01-12
There's a bug here somewhere. At least here on 14.04 it appears some of the apache2 packaging was changed around, maybe that's the cause.
Otherwise man2html needs some fix or at the very least an altered Description, if need be it should add the command above to the - 
"Point your web browser at [http://localhost/cgi-bin/man/man2html](http://localhost/cgi-bin/man/man2html) to read and
search your man pages in the browser."

---

