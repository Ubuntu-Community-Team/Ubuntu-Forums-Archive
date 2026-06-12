---
title: "Undo command"
date: 2014-06-13
forum: General Help
---

### Post by betty3 on 2014-06-13
Can anyone help me undo these commands and explain me what they do: 

```
[COLOR=#333333][FONT=Courier New]wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -[/FONT][/COLOR]
```
```
[COLOR=#333333][FONT=Courier New]sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" >> /etc/apt/sources.list.d/postgresql.list'[/FONT][/COLOR]
```

---

### Post by steeldriver on 2014-06-13
AFAIK all that they do is **prepare** your system's package management system to install packages from [www.postgresql.org]("http://www.postgresql.org") - as long as you didn't go any further than that, you can undo them by editing the added line out of your /etc/apt/sources.list file and using 'apt-key del' to remove the added key.

---

### Post by betty3 on 2014-06-13
how do I use the apt-key del ? do I repeat the code like this? :

[COLOR=#333333][FONT=Courier New]wget --quiet -O - [https://www.postgresql.org/media/keys/ACCC4CF8.asc](https://www.postgresql.org/media/keys/ACCC4CF8.asc) | sudo apt-key **del** -[/FONT][/COLOR]

---

### Post by steeldriver on 2014-06-13
No, afaik you will need to run 

```

apt-key list

```

and look for the lines like

```

pub   4096R/[COLOR=#ff0000]**ACCC4CF8**[/COLOR] 2011-10-13 [expires: 2019-07-02]
uid                  PostgreSQL Debian Repository

```

then you can do 

```

sudo apt-key del ACCC4CF8

```

You can check it's really gone by running 'apt-key list' a second time. 

[In this case you could have got the key-id from the ACCC4CF8.asc filename but I don't think that will always necessarily be the case.]

---

### Post by betty3 on 2014-06-13
thanks although I had nothing on the list that was related to PostgreSQL. I had already erased the line in the sources.list file and then I listed the trusted keys but found nothing, so maybe is not there anymore, and maybe it was never there. Did you try it yourself?

---

### Post by steeldriver on 2014-06-13
yes I added and then removed it just to make sure I posted the right syntax

---

### Post by betty3 on 2014-06-13
thanks :)

---

