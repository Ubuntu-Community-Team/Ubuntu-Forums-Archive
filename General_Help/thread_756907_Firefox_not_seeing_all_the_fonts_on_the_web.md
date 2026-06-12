---
title: "Firefox not seeing all the fonts on the web"
date: 2008-04-16
forum: General Help
---

### Post by 1richard on 2008-04-16
I downloaded all the fonts and restricted extras, and Firefox, and all the other browsers will not see old english fonts on the web, yet they are there on windows. What do I have to do to correct this?  I think the problem is with ubuntu.

---

### Post by wdaniels on 2008-04-18
As usual, there are different ways to embed fonts in web pages and different browsers support different methods. And that's assuming the website(s) concerned are even embedding the relevant font(s) at all. I believe the Opera browser supports some form of TTF embedding, but as far as I know, no linux browser supports the EOT format used by Microsoft's WEFT (Web Embedding Fonts Tool) and thus Internet Explorer.

There is, however, a [plugin]("http://pakdata.com/products/pdms-weft-plugin") available for Firefox which adds this support, but I've never tried it myself.  I'd try that first and see if it solves your problem.

---

