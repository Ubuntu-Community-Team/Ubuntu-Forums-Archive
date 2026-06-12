---
title: "Cyrus-imap with Hoary"
date: 2005-04-19
forum: General Help
---

### Post by Klunk on 2005-04-19
I have been trying to get cyrus-imap working with my ubuntu. I ended up doing the upgrade from warty to hoary as a result (not that I am disapointed). However, I still cannot get imtest to work :(.

I have run saslpasswd with the cyrus account, entered my desired password and done an sasldblistusers and can see the account. However when I run ```
imtest -m login -p imap localhost
``` as cyrus and specify my password I get a user does not exist error message.

I have the default config for cyrus. Is there a cyrus howto for ubuntu because I have followed the 'official' howto and googled for the error message and cannot find a resulution.

Any help would be appreciated.

---

