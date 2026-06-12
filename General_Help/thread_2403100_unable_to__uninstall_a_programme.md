---
title: "unable to  uninstall a programme"
date: 2018-10-07
forum: General Help
---

### Post by kmob on 2018-10-07
I have been with Ubuntu for about 4 weeks now and using 18.04. I dowloaded a prog 'TVtime'  which appears on my desktop but it is stopping Ubuntu updates. I dont seem able to uninstall it. Can anyone help plse?

---

### Post by howefield on 2018-10-07
Thread moved to the *General Help* forum.

---

### Post by #&amp;thj^% on 2018-10-07
Thanks howefield :)
@kmob what dose this show from the terminal:
```
apt policy tvtime
```

---

### Post by kmob on 2018-10-17
sorry I have been in hospital ..... apt policy tv time   ,......show[I]s
tvtime:
installed: 1.o.11.1
candidate: 1.0 . 11-1
*** 1.0.11 - 1 500
500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe amd64 packages
100 /var/lib/dpkg/status
[/I]

---

### Post by kmob on 2018-10-30
Can anyone help me please? - I am a newbie and finding my way around difficult. The app TVTIME is causing updates to fail.

---

### Post by deadflowr on 2018-10-30
So we get an understanding, what happens when you run
```
sudo apt purge tvtime
```
Post back the output (use code tags)

---

### Post by kmob on 2018-11-05
Thanks everyone, I have managed to uninstall tvtime using   .... sudo apt purge tvtime .................. thanks for the help

---

