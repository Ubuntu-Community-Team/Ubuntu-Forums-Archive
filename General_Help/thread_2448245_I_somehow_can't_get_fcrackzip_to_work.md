---
title: "I somehow can't get fcrackzip to work"
date: 2020-08-04
forum: General Help
---

### Post by raphaell2 on 2020-08-04
For reasons I won't get into, I want to at least try to crack some encrypted zip files on my computer. No problem, I thought, I'll simply install fcrackzip (through synaptic). So I did. I tried it on one of the files, in brute-force mode. Of course, for any chance of success, I'd need patience. 

But after a while, I decided to test it, simply to see how it would look like if it found a password. So I made a little nonsensical test file and encrypted it as a zip archive with the worst password I could think of at the moment - the word "fish" (without the quotation marks). I tried a brute force of passwords with up to for letters:

```
snip
```

It found the text file inside testfile.zip, and told me it was testing all kinds of passwords, but the entire run didn't result in finding the password. But it *must* have tried "fish" during that run, so why didn't it crack the file?

Then, for a dictionary attack, I made a little text file consisting *only *of the word "fish", and used that: 

```
snip 
```

Again, *no result*. Apparently, I am doing *something *wrong, but I have no idea what it could be. Any ideas?

---

### Post by QIII on 2020-08-04
Please refer to the [Ubuntu Forums Rules]("https://ubuntuforums.org/misc.php?do=showrules"), specifically:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.
Thread closed.

---

