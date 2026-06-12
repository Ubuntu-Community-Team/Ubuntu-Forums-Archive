---
title: "Problem that may be related to character encoding"
date: 2006-11-08
forum: General Help
---

### Post by abelthorne on 2006-11-08
I have a big problem that seems to have originated since I upgraded from Dapper to Edgy. I'll try to describe it in the most accurate way (english not being my native language, I hope it won't be too confusing).

A part of my job is to work on websites (design and code). I use Bluefish in Ubuntu to code HTML and PHP pages. I happen to use different hosts (servers ?) for the websites I manage and I have recent problems with one of them.

A few days ago, I updated a PHP file on a site. I created the whole website when I was using Dapper and it worked fine. When I uploaded the new version of the PHP file, it became inaccessible ("unexcpected error" message from the server). I first thought ther was a ponctual problem but it turned out that the problem came in fact from my file (as other PHP files not made by me work and HTML files work too). The same PHP file that can't be used work flawlessly in my local server (using LAMPP) and with other web hosts.

The strange thing is that I tried to boot in Windows, download the problematic file from the problematic host, copy-pasted its content in a new file (encoding it in ISO), reuploaded it and it then worked without problem.

I think my problems may come from character encoding, but I don't understand how.

To sum it up :
- PHP files made with Dapper (UTF-8) work
- PHP files made with Windows (ISO) work
- PHP files made with Edgy (UTF-8 or ISO) don't work
this happens with one particular web host and only with PHP files. PHP files I recently made (with Edgy) work when hosted on other servers.

Has anybody the slightest idea of what is happening ?

---

