---
title: "Quick tar extract question"
date: 2007-05-09
forum: General Help
---

### Post by wormeyman on 2007-05-09
How do i "extract here" with a tar file the examle is that i'm installing word press using the shell on dream host and right now what i currently do is

```
wget http://wordpress.org/latest.tar.gz
```
```
tar -xzvf latest.tar.gz
```
```
cd wordpress/
```
```
cp * ..
```

I know that the last 2 have to be unnecessary but i don't now how to just extract the files in the folder wordpress in to the current directory.

---

### Post by ikonia on 2007-05-09
you can't do that as the tar extract was created within the wordpress folder so every time you extract it will always extract into ./wordpress this is because the person creating the tar did tar cvf wordpress.tar ./wordpress rather than cd wordpress; tar cvf ../wordpress.tar .

---

