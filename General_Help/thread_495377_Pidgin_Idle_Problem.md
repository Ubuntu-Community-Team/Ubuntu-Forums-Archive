---
title: "Pidgin Idle Problem"
date: 2007-07-08
forum: General Help
---

### Post by ZERO_SHIFT on 2007-07-08
I recently installed pidgin but it keeps idle-ing me even when I am using my PC any ideas?

Thanks in Advance

LongLiveTheCommuntiy---LLTC

---

### Post by shasan on 2007-07-08
what are your idle settings under preferences?

---

### Post by ZERO_SHIFT on 2007-07-08
> **shasan said:**
> what are your idle settings under preferences?
Change Status when idle for 5 minuets to Away

---

### Post by hikaricore on 2007-07-08
There should be an option that says:

**Report idle time**

Options are:

[U]Never
From last message sent
Based on keyboard or mouse input[/U]

You may want to check the setting of this option.

---

### Post by ZERO_SHIFT on 2007-07-08
> **hikaricore said:**
> There should be an option that says:

**Report idle time**

Options are:

[U]Never
From last message sent
Based on keyboard or mouse input[/U]

You may want to check the setting of this option.

I found the first two but not _ Based on keyboard or mouse input:(:confused::(_

---

### Post by jmazzarelli on 2007-07-09
I compiled pidgin from source and had this problem too. This has the solution:
[http://developer.pidgin.im/ticket/467](http://developer.pidgin.im/ticket/467)
```
sudo apt-get install libxss-dev
./configure && make
sudo make install
```

---

### Post by ZERO_SHIFT on 2007-07-09
> **jmazzarelli said:**
> I compiled pidgin from source and had this problem too. This has the solution:
[http://developer.pidgin.im/ticket/467](http://developer.pidgin.im/ticket/467)
```
sudo apt-get install libxss-dev
./configure && make
sudo make install
```

I am sorry but in what directory do I execute these commands?


Thanks

---

### Post by jmazzarelli on 2007-07-10
> **ZERO_SHIFT said:**
> I am sorry but in what directory do I execute these commands?


Thanks

How did you install it to begin with?
I downloaded the source code and compiled it. If you want to do it that way, you can do this from your home directory:
```
sudo apt-get install libxss-dev
wget http://superb-west.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.2.tar.bz2
tar xf pidgin-2.0.2.tar.bz2
cd pidgin-2.0.2/
./configure && make
sudo make install

```

---

### Post by ZERO_SHIFT on 2007-07-11
> **jmazzarelli said:**
> How did you install it to begin with?
I downloaded the source code and compiled it. If you want to do it that way, you can do this from your home directory:
```
sudo apt-get install libxss-dev
wget http://superb-west.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.2.tar.bz2
tar xf pidgin-2.0.2.tar.bz2
cd pidgin-2.0.2/
./configure && make
sudo make install

```

Thanks! :lolflag:that solved the problem but I still cant get the sounds in pidgin working...

Any ideas?

---

### Post by midtown on 2007-07-17
Yeah, this fixes the idle problem but seems to break sound. I don't personally care as I normally disable the sounds anyway, though. Thanks!

---

### Post by lawrence1992 on 2007-07-19
> **ZERO_SHIFT said:**
> Thanks! :lolflag:that solved the problem but I still cant get the sounds in pidgin working...

Any ideas?

```


sudo apt-get install libgtk2.0-dev libxml2-dev gettext libnss-dev libnspr-dev



```
if you desire spell checking, include ```
 libgtkspell-dev in that list .
```

---

### Post by chungaroo on 2007-10-22
Is there any way to set pidgin so that it never reports me as idle?  Right now it's set to not report my idle-time, but I'm still showing as idle on other people's computers.  Thanks!

---

### Post by 65 mustang on 2007-11-01
I had to do
```
apt-get build-dep pidgin
```
and then remake and install pidgin from source to fix my problem of never coming back from away.

---

