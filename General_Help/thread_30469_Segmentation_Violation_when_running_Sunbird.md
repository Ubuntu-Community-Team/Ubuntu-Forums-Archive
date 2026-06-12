---
title: "Segmentation Violation when running Sunbird"
date: 2005-04-28
forum: General Help
---

### Post by jdiz on 2005-04-28
First of all, I want to note that I just installed Ubuntu one week ago, and upgraded to Hoary yesterday, so I'm quite a newbie in Linux.

I downloaded Sunbird from mozilla.org, untared it and tried to run it. In Nautilus I got no answer at all, but when at the console it throwed an error message: "Segmentation Violation etc" (sp?).

The Calendar extension works fine, and It's what I'm using at the moment, but I wanted to know if the error is Ubuntu's fault or myself's.

PS. Sorry for my english!

---

### Post by Psquared on 2005-04-28
[QUOTE=jdiz]First of all, I want to note that I just installed Ubuntu one week ago, and upgraded to Hoary yesterday, so I'm quite a newbie in Linux.

I downloaded Sunbird from mozilla.org, untared it and tried to run it. In Nautilus I got no answer at all, but when at the console it throwed an error message: "Segmentation Violation etc" (sp?).

The Calendar extension works fine, and It's what I'm using at the moment, but I wanted to know if the error is Ubuntu's fault or myself's.

PS. Sorry for my english![/QUOTE]

I'm not much further along than you are, but I know what it's like to post a question and not get an answer. I have not installed Sunbird but here' a couple of questions. First, did you look to see if there was a *.deb package so you could use "dpkg"? You may have some unresolved dependencies by installing it from the tar.gz file.

[Note: I just checked and while there are a variety of builds I did not see one specifically for debian. In that case, it is my understanding that you are pretty much on your own as to whether it will work.]

Maybe someone else has gotten it to work on Hoary and will suggest what you need to do.

---

### Post by pemcg on 2005-05-03
It' a known "feature" of this version of sunbird. Try running it with the -calendar switch, i.e.:

/usr/local/mozilla/sunbird/sunbird -calendar

Peter

---

