---
title: "[SOLVED] tar: Conflicting compression options"
date: 2008-01-03
forum: General Help
---

### Post by S3loth on 2008-01-03
I'm trying to get my Moto Razr to work with Ubuntu and am following [this]("http://veinhammer.wordpress.com/2006/05/18/motorola-razr-ubuntu-linux/") guide, however when I get to > $ tar zxvfj moto4lin-0.3.tar.bz2] terminal says > tar: Conflicting compression options

I don't know what the problem is and Google didn't help at all. Anybody know what's wrong?

---

### Post by cdenley on 2008-01-03
```

tar xvfj moto4lin-0.3.tar.bz2

```

z=gzip
j=bzip2

You can only use one type of compression.

---

### Post by p_quarles on 2008-01-03
I just skimmed the comments on that blog (looking for someone pointing out the poster's mistake with the tar options), and noticed the very last one, dated yesterday:
> worked great. thanks! Now moto4lin is in the Ubuntu package. So it&#8217;s a matter of apt-get. For readers of the blog, although p2k hasn&#8217;t been packaged I didn&#8217;t use it. My cell pone, RAZR V3, got switched to p2k by echo AT+MODE=8>/dev/ttyACM0
I just checked, and this is correct. All you need to do is install the moto4lin package from Synaptic.

---

### Post by S3loth on 2008-01-03
Ok, great. But if I needed to install it the old way, all I would have to do is take out the z or j, right?

---

### Post by taurus on 2008-01-03
> **S3loth said:**
> Ok, great. But if I needed to install it the old way, all I would have to do is take out the z or j, right?

In your case, take out the z.

```
tar xvjf moto4lin-0.3.tar.bz2
```

---

