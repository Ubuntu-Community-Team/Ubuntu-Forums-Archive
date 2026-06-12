---
title: "C Header Files Missing i"
date: 2006-11-07
forum: General Help
---

### Post by mandar_dj on 2006-11-07
hey 

i have ubuntu linux 6.06 version 

and could not find any gcc header files.
Can u tell me how do i get it .

I did installed gcc4.0 base thru synaptec manager .


mandar

---

### Post by boban on 2006-11-07
try from terminal:

```

sudo aptitude install build-essential 

```

---

### Post by po0f on 2006-11-07
mandar_dj,

Type the following command from a terminal:
```
sudo aptitude install build-essential
```

The package you were missing is libc6-dev, but build-essential pulls in gcc, g++, libc6-dev, make, and a couple of other things needed to build stuff from source.

---

### Post by jnet3000 on 2007-02-23
I had the same problem with Ubuntu 6.10.  But I found it, not sure how I lost it, because my last install of Edgy didn't have that problem:

apt-get install libc6-dev

 dpkg-query -L libc6-dev | grep stdio.h
/usr/include/bits/stdio.h
/usr/include/stdio.h

---

