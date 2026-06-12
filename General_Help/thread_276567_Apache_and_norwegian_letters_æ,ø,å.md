---
title: "Apache and norwegian letters æ,ø,å"
date: 2006-10-13
forum: General Help
---

### Post by cullam on 2006-10-13
Hi I have just installed Apache and got it up and running, but when I post a simple test page, I see that it does not take the letters æåø if you dont understand what I mean, you can allways take a loot at [http://vannredning.mine.nu](http://vannredning.mine.nu) Any of you have any suggestions how to fix this?

Cullam
:p

---

### Post by whopazz on 2006-10-13
Have you tried setting the charset in your html document to

<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />

?

You might also try <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />

If that don't work, you'll probably have to edit apache.conf, and add norwegian charset, iso-8859-1 .

---

