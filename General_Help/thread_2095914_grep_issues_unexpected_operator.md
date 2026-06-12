---
title: "grep issues unexpected operator"
date: 2012-12-18
forum: General Help
---

### Post by cbillson on 2012-12-18
I'm wanting to use grep to extract a string from a log, however the string contains items that cause the command to fail.

Unfortunately using more specific words throws up false positives.

the full string is: "program started - My_Program"

after much googling i tried " and ' and -F without success. i also tried \-

any thoughts how i can get grep to pickup that as a full string?

thanks
Chris

---

### Post by steeldriver on 2012-12-18
Hmm that's odd - quotes should work (they do for me)

```
$ echo "program started - My_Program" | grep 'program started - My_Program'
program started - My_Program
$ echo "program started - My_Program" | grep -v 'program started - My_Program'

```Are you sure there's nothing else going on?

---

### Post by Lars Noodén on 2012-12-18
If it really is the whole line from start to end then you could include the start and end as part of the search with ^ and $.

```

 grep '^program started - My_Program$'

```

---

### Post by cbillson on 2012-12-18
> **steeldriver said:**
> Hmm that's odd - quotes should work (they do for me)

```
$ echo "program started - My_Program" | grep 'program started - My_Program'
program started - My_Program
$ echo "program started - My_Program" | grep -v 'program started - My_Program'

```Are you sure there's nothing else going on?

I get the following output:

./count.sh: 63: [: /var/countlogs/count/count.2012-12-16.001.log: unexpected operator

---

### Post by cbillson on 2012-12-18
> **Lars Noodén said:**
> If it really is the whole line from start to end then you could include the start and end as part of the search with ^ and $.

```

 grep '^program started - My_Program$'

```


Still returns the same error i'm afraid.

---

### Post by steeldriver on 2012-12-18
can we see that section of the count.sh script please? I think it's actually complaining about the [ operator not grep

```
 ./count.sh: 63: [COLOR=Red]**[**[/COLOR]: /var/countlogs/count/count.2012-12-16.001.log: unexpected operator
```

---

### Post by cbillson on 2012-12-18
Sorry.... was a different line giving the error, will teach me to assume the environment was the same as i left it yesterday - DOH!

---

