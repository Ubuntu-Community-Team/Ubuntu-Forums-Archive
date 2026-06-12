---
title: "Problem with &quot;help.ubuntu.com&quot; default language."
date: 2014-04-05
forum: General Help
---

### Post by kobold2 on 2014-04-05
Hello guys!

I am working through russian ISP so i am getting russian version of "help.ubuntu.com".
But i want the default english version of it.
What should i do to get it back?

Thanks in advance.

---

### Post by bapoumba on 2014-04-05
I have a French ISP and [https://help.ubuntu.com/](https://help.ubuntu.com/) is an English page. What browser are you using and have you setup translation of pages that are not in your preferred language ?

---

### Post by kobold2 on 2014-04-07
> **bapoumba said:**
> I have a French ISP and [https://help.ubuntu.com/](https://help.ubuntu.com/) is an English page. What browser are you using and have you setup translation of pages that are not in your preferred language ?

I am on Ubuntu 12.04 LTS and Firefox 28.0 with no addons.

The thing is the head page itself ( help.ubuntu.com ) is showing in english.
But when i am trying to go deeper ( for example: help.ubuntu.com/12.04/ubuntu-help/index.html ) it switchs to the russian.

So it turns out that i can't read original documentation.
 It sucks, really.

---

### Post by bapoumba on 2014-04-07
> **kobold2 said:**
> I am on Ubuntu 12.04 LTS and Firefox 28.0 with no addons.

The thing is the head page itself ( help.ubuntu.com ) is showing in english.
But when i am trying to go deeper ( for example: help.ubuntu.com/12.04/ubuntu-help/index.html ) it switchs to the russian.

So it turns out that i can't read original documentation.
 It sucks, really.

Had a look at Firefox (using Chrome here).

Please have a look at Content > Language item > Choose and see what you have set up there, thanks.

---

### Post by kobold2 on 2014-04-07
> **bapoumba said:**
> Had a look at Firefox (using Chrome here).

Please have a look at Content > Language item > Choose and see what you have set up there, thanks.

It works!
First i rearranged languages to desired order but that didn't worked. Then i removed all languages except english and bingo! It works!

You just made my day, sir!
Thank you!

---

### Post by bapoumba on 2014-04-07
Glad to see you got it to work :)
Please mark your thread as solved (under Thread Tools menu), thanks!

---

### Post by Doug S on 2014-04-07
help.ubuntu.com contains over 60 languages. As you have discovered, the server returns pages based on your language settings. There are a few handwritten "glue" pages, in English only, that hold it all together. If you want to force a particular page language without changes to your language settings you can manually add the language extension to the address. For example, say I wanted the dutch version of [https://help.ubuntu.com/13.10/ubuntu-help/unity-dash-intro.html](https://help.ubuntu.com/13.10/ubuntu-help/unity-dash-intro.html) then I just ask for [https://help.ubuntu.com/13.10/ubuntu-help/unity-dash-intro.html.nl](https://help.ubuntu.com/13.10/ubuntu-help/unity-dash-intro.html.nl)

---

