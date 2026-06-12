---
title: "[SOLVED] dvd size detect"
date: 2008-06-12
forum: General Help
---

### Post by KaliVoid on 2008-06-12
Hi

im trying to burn a data dvd total size of 4.6G.
the burning media is 4.7G (new empty) Brasero only detect (allow to burn) 4.3G ,after searching the forum i try K3B it only detect 4.4G.
i made an iso image and same problem 4.6G dont fit
on 4.7G with both software (with overburn).

my burner is [LG GSA-H55L]("http://ca.lge.com/en/products/model/detail/dvdwriter_gsah55l.jhtml#")

ty

---

### Post by KaliVoid on 2008-06-16
bumpy bump
(i have to present the data in one week)

---

### Post by Vivaldi Gloria on 2008-06-16
A DVD-5 format disc has a storage capacity of 4.71 GB but this equals only 4.39 GiB because media makers use different units. See

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

So no way you can fit your files on dvd.

---

### Post by geirha on 2008-06-16
This sounds like the usual problem between representing sizes in [Gigabytes](http://en.wikipedia.org/wiki/Gigabyte) (GB) vs. [Gibibytes](http://en.wikipedia.org/wiki/Gibibyte) (GiB).

4.7 GB is approximately 4.4 GiB. 
```
$ bc <<< "scale=3; 4.7 * 10^9 / 2^30"
4.377

```

Read [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix) to understand more about this problem.

---

### Post by KaliVoid on 2008-06-16
this is my first dvd in ubuntu , so every time i burned a dvd in windows they lie to me! saying 4.7g when its actually 4.3g .

thanks for the links.

---

