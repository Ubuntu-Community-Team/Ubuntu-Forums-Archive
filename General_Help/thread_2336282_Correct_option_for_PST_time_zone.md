---
title: "Correct option for PST time zone?"
date: 2016-09-06
forum: General Help
---

### Post by Aphexlog on 2016-09-06
Hey fellas,

What is the correct option to select if I require a server to register on PST timezone?

I am executing the following command: sudo dpkg-reconfigure tzdata

P.S. I see no option for Oregon, Washington or CA

Thanks,
Aaron

---

### Post by ian-weisser on 2016-09-07
Choose 'Vancouver' or 'Los_Angeles'.

---

### Post by Aphexlog on 2016-09-07
Unfortunately, both of those options are PDT time which is a 1 hour difference to PST (which is what I need).

---

### Post by Habitual on 2016-09-07
Well, I don't know where it needs to be "set" but in bash, I'd be inclined to use
```
export TZ='PST8PDT' ; date
```

---

