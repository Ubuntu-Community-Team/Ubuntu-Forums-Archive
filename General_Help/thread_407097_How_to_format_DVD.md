---
title: "How to format DVD"
date: 2007-04-11
forum: General Help
---

### Post by Gumper on 2007-04-11
Simple question here, but for the life of me I can't figure out how to format / erase the contents of a DVD+RW. 


Can anyone explain to me how I would do this? 

I'm currently using Feisty.

Thanks,

Gumper

---

### Post by andrew.46 on 2007-04-12
Hi,

 I don't actually have a DVD Burner but I see that GnomeBaker has an option: Format DVD + / -r under Tools. Is this what you mean?

                  Andrew

---

### Post by Gumper on 2007-04-12
Hi Andrew,

Yes that is what i was talking about but it doesn't seem to work. 

Gumper

---

### Post by amaroKer on 2007-04-30
I can't seem to make it work either...

---

### Post by Acksys on 2007-05-11
In case anyone's still working on this problem..

Gnomebaker uses dvd+rw-format to format DVD+RWs, but doesn't use the -force option.

I ran it from the command line

```
dvd+rw-format -force /dev/cdrom
```

with no problems.

---

