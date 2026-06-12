---
title: "Cannot make a cd in ubuntu"
date: 2017-09-29
forum: General Help
---

### Post by jsjpandey on 2017-09-29
I am trying to make an audio cd in in ubuntu,  but it is failing again and again which is wasting my cd and money.  Please help.

---

### Post by ian-weisser on 2017-09-29
Please explain the steps you are following that results in failed CDs, so we can duplicate the failure.

---

### Post by jsjpandey on 2017-09-29
Tried it with brasero but failing after 40% each time

---

### Post by lisati on 2017-09-29
Are you burning the CD at the slowest possible speed? This sometimes works better than letting the software automatically choose a write speed for you.

---

### Post by ajgreeny on 2017-09-29
I have not used brasero for a long time now, mainly because I use Xubuntu, but I do remember brasero being very flaky last time I did use it.

Several Ubuntu users make xfburn their default CD/DVD burner nowadays as it seems to work more reliably than brasero; it uses gtk libraries so you will probably already have many if its dependencies, but it uses a diferent backend.

Definitely worth a try!

---

### Post by Autodave on 2017-09-29
xfburn and do it at no faster than middle speed. Start there.

---

### Post by jsjpandey on 2017-09-30
Now that's interesting, with xfburn first I burned a small amount of file round about 100 MB and after ejection I reinserted the disk and it shows the content, then I burned all 600 MB of data and after ejection it doesn't show anything not even mounting. Now the first one is not even mounting.

---

### Post by speartip on 2017-09-30
I have never had a problem with Brasero. I take it you're trying to make a bog standard audio CD thats playable on anything. Or are you trying to make an mp3 CD?
Also what format are the files in that you are trying to burn? (mp3, m4a, flac etc..)
And do you have the ubuntu-restricted-extras package installed?

---

### Post by jsjpandey on 2017-09-30
Brasero is seriously having some problem as it cannot complete the but it is relief that xfburn is completing the burn.

---

