---
title: "sorting by IP address"
date: 2020-03-05
forum: General Help
---

### Post by Skaperen on 2020-03-05
the [COLOR=#0000cd][FONT=courier new]**sort**[/FONT][/COLOR] command appears to have features to sort dates more easily.  but i still do not see an easy way to sort by _IP address_ that comes in the [COLOR=#0000cd][FONT=courier new]**sort**[/FONT][/COLOR] command.

---

### Post by EuclideanCoffee on 2020-03-05
Does this help?

[https://www.cyberciti.biz/faq/unix-linux-shell-script-sorting-ip-addresses/](https://www.cyberciti.biz/faq/unix-linux-shell-script-sorting-ip-addresses/)

---

### Post by Doug S on 2020-03-05
I have always found sort -g to be good enough for my needs.

---

### Post by Skaperen on 2020-03-06
> **EuclideanCoffee said:**
> Does this help?

[https://www.cyberciti.biz/faq/unix-linux-shell-script-sorting-ip-addresses/](https://www.cyberciti.biz/faq/unix-linux-shell-script-sorting-ip-addresses/)

i'm not sure why they think that works.  it doesn't for me.  it's clearly wrong.  it only sorts based on the last 2 octets.  but i think it will work if i add key options for the first 2 octets sot sorts based on all 4 octets.  this worked:
```

sort  -t . -k 1,1b -k 2,2n -k 3,3n -k 4,4n

```

> **Doug S said:**
> I have always found sort -g to be good enough for my needs.

[COLOR=#0000cd][FONT=courier new]**sort -g**[/FONT][/COLOR] doesn't get IP addresses in order.  i end up with 66 after 202. which is not right.

---

### Post by The Cog on 2020-03-06
This is the shortest I could make it:
```
sort -nt. -k1,1 -k2,2 -k3,3 -k4,4
```

---

### Post by slickymaster on 2020-03-06
*Thread moved to **General Help**.*

---

### Post by Skaperen on 2020-03-06
i originally didn't try the key form like "3,3".  i just tried plain numbers without the comma.  i don't understand what the comma does.

---

### Post by The Cog on 2020-03-07
The number after the comma defines where the key ends and the default is to the end of the string. So that just -k 3 says sort using the 3rd segment to the end, -k 3,4 says use segments 3 and 4 as a single sort key, and -k 3,3 says use segment 3 alone as a sort key.
Using 111.222.333.444 as input:
-k 2 would try to sort using "222333444"
-k2,3 would use "222333"
and -k2,2 would use "222"

I *think* that's right.

---

### Post by Skaperen on 2020-03-07
then the real problem is that it is merging multiple keys together (when comma is not used or specifies a later key) is done by _concatenating strings_ to make a new key, rather than just comparing that many separate keys (compare key 3 to key 3 in another line and if equal, compare key 4 to key 4 in that other line).  now i have a big clue to why i've had so much trouble with the sort command.  thanks!!

---

### Post by The Cog on 2020-03-08
Just found this that explains nicely: [https://unix.stackexchange.com/questions/52762/trying-to-sort-on-two-fields-second-then-first](https://unix.stackexchange.com/questions/52762/trying-to-sort-on-two-fields-second-then-first)

---

### Post by Skaperen on 2020-03-08
IMHO, it was a bad CLUI design decision to have simple keys (without comma) operate as -kN,end.  it should have required something explicit like -kN, or -kN,end to get that behavior.  -kN should have been made to behave like -kN,N.  just MHO.  it's the way i would have done it.

---

