---
title: "konqueror not loading web pages"
date: 2008-05-30
forum: General Help
---

### Post by gdkeene on 2008-05-30
Every time I try to open a web page with konqueror, I get the following error message:

An error occurred while loading [http://www.whatever.com:](http://www.whatever.com:)
Unexpected end of data, some information may be lost.

If I then refresh the page, it loads.  This happens for every web page.  As a file browser it works fine.

Any ideas?

---

### Post by p_quarles on 2008-05-30
What version of Konqueror? What is the cache size?

Also, if you can run the application from a terminal, you may get more information about the problem:
```
konqueror --profile webbrowsing
```
Try to get it to replicate the problem you're describing, and look for any error messages in the terminal that might correspond to the problem.

---

### Post by gdkeene on 2008-05-30
I'm using Konqueror 3.5.9.  The cache size is 5120 kB.

I've run it from the terminal, but when the error ocurrs in the web browser, there is no error message in the terminal.

---

