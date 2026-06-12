---
title: "cyrillic + icq + gaim = disaster"
date: 2007-01-18
forum: General Help
---

### Post by aa.ivanov on 2007-01-18
Gaim is annoying me. When someone tries to send me a message in cyrillic I get the following error:
> (There was an error receiving this message.  The buddy you are speaking to most likely has a buggy client.)
I've tried setting the codepage / encoding manually to cp1251, windows-1251 and utf-8 since these are the most common encodings in the neighborhood. No difference.

Has anyone had any such problems?

Ubuntu 6.10, gaim 2.0.0betta3.1

---

### Post by Stemp on 2007-01-18
If you read Russian, maybe [http://libc6.blogspot.com/2006/10/icq-russain-encoding-in-gaim.html](http://libc6.blogspot.com/2006/10/icq-russain-encoding-in-gaim.html)

---

### Post by aa.ivanov on 2007-01-18
wow this worked! Thanks a lot!

For anyone not reading russian the plot is:
1. activate support for bg_BG.CP1251 locale (ru_RU.CP1251 for Russian) by adding it to the appropriate file in cd /var/lib/locales/supported.d/
2. do "sudo dpkg-reconfigure locales" and you should see the new locale listed in the output of the command
3. edit the gaim starter so that the command is not 'gaim', but rather: sh -c "LC_ALL=bg_BG.CP1251 gaim"
4. In gaim edit the icq connection properties and set the codepage to CP1251 (it's on the 'advanced' page)
5. get a friend to test the cyrillic support

---

### Post by robertpolson on 2007-05-25
This looks simpler:

[https://answers.launchpad.net/ubuntu/+source/gaim/+question/60](https://answers.launchpad.net/ubuntu/+source/gaim/+question/60)

"It depends on the protocol / server you use, but usually you can do the following: Tools >> Accounts. Select the account you want to use cp1251 on and click "Modify". Click "Show more options" and enter "Windows-1251" in the "Encoding" field. Works on ICQ or IRC. Jabber doesn't have this field, but it just works (uses utf8 internally). I don't have other accounts."

---

