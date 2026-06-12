---
title: "apt-get help"
date: 2007-01-05
forum: General Help
---

### Post by artinla on 2007-01-05
I get this anytime that I run apt-get:

[I]The following packages were automatically installed and are no longer required:
  libpopt-dev liborbit2-dev libsm-dev gtk-doc-tools gtranslator libice-dev
  x11proto-xext-dev libtasn1-3-dev libatk1.0-dev docbook-to-man...**Use apt-get -autoremove to remove them**[/I]

The list is actually quite a bit longer.  

I don't particularly want to remove any packages.  They appear to be mostly libraries, why would I want to just remove them?  

How can I tell apt-get to ignore them and not force me to autoremove them in order to avoid this message?

---

### Post by moma on 2007-01-05
Interesting question.

A suggestion:
You could possibly edit "/etc/apt/apt.conf.d/01ubuntu" and add a new regular expression to the NeverAutoRemove section.  So you need to add regular expression [COLOR="Red"]".*"; [/COLOR] there.  
Expression ".*" means any package what so ever. So no packages will be AutoRemoved and it will stop nagging about it.

Does it cause any side effects?
-------------------------

Anyway, most of the packages in your list are "-dev" packages (source code and c/c++ header/include files). Removal of those will not harm your system unless you do some development and compilation work.

ps. 50% of businesses will run [COLOR="Yellow"]Ubuntu[/COLOR] Linux in 5 years
[http://www.computerworld.com/....]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9006990")

---

### Post by artinla on 2007-01-05
Thanks, I will try that now.


No, there are no adverse side effects other than it nagging me to remove them each time I apt-get something.

I am on dial-up internet, so I don't like to uninstall anything unless I have to.  

Art

---

