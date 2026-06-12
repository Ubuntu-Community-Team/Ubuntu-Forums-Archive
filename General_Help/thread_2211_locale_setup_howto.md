---
title: "locale setup howto"
date: 2004-10-26
forum: General Help
---

### Post by macsaint on 2004-10-26
I figured out how to change the locale for the input system keeping menu and others in english

First, write the .xsession file as

export LANG="en_US"
export LC_CTYPE="ko_KR.EUC-KR"
export XMODIFIERS="@im=nabi"
export GTK_IM_MODULE=nabi
exec gnome-session

and make it executable (chmod 744 .xsession).
In the session manager, add the input method as a startup program.

Now log out and choose the session as default.
(I don't know why .xsession is not read if I choose gnome session)

Although I explain for korean locale, but it will work for other locales too.
It should be noted that "nabi" is korean input method, so it is needed to change
to appropriate input system for other languages.

JW

---

### Post by byoon on 2004-12-10
Just a few questions.

I am setting up an Ubuntu system for my dad and am trying to set up the Korean locale.

1.  When you run "dpkg-reconfigure locale" do you set up "none", "en", or "kr" as your default locale?  I chose "none"

2.  When you say "In the session manager, add the input method as a startup program", what do you mean?  Where is the session manager and what is the input method program?

Thanks.

---

