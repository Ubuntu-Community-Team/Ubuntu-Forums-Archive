---
title: "Zend Studio 5.5 on edgy / feisty on AMD64"
date: 2006-12-18
forum: General Help
---

### Post by dm1024 on 2006-12-18
Hi ubuntu people!

Few days ago I've try to install ZendStudio 5.2 on ubuntu (x86_64). I had no success.
Than in mail I found, that there is a new version 5.5 available.
It installed without any troubles - just click-and-run.

But there was annoying bug with russian symbols. Here's the explanation.
Other java applications allows normal cyrillic input, but ZDE doesn't. So, the trouble is in java. And it looks like system's java (sun-java5-bin) runs fine. ZDE uses own JRE. And his JRE has no cyrillic fonts (I don't know, what was the bug - it could display russian easily, but couldn't input cyrillic in editor's area).
Well, what I did. I have installed ZendStudio to /usr/local/Zend/ZendStudio-5.5.0.
I've rename directory /usr/local/Zend/ZendStudio-5.5.0/jre to jre_, and made an symlink named jre to /usr/lib/jvm/java-1.5.0-sun.
And it works. Just run ZDE without any optional tricks!

---

