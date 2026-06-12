---
title: "Bulk rename files based on contents"
date: 2012-10-23
forum: General Help
---

### Post by creativelies on 2012-10-23
Hi guys;

I've searched for the above and have found a few threads with similar questions but I don't have a strong enough understanding of sed to make them work for me.

I need to bulk rename a directory of .txt files based on a single line within that file - the catch is that that line is somewhere random within that file. The line is always:

Customer No.: 012345677

I'd like to rename each file to that customer's unique number.txt.  I'm reading up on sed as that seems to be the most commonly suggested way of doing this but it's making my head spin at the moment and my crude adaptations of other solutions are doing amusingly awful things to my files.

Any help is vastly appreciated.

---

### Post by Vaphell on 2012-10-23
try
```
for f in *.txt; do id=$( awk '/Customer No/{ print $NF }' "$f" ); **echo** mv "$f" "$id.txt"; done
```

obviously echo is to be removed once it's clear that the results are right.

---

### Post by creativelies on 2012-10-23
EDIT: User error!

That works beautifully!

Thankyou very much for the time you took to help - it's appreciated. :) Message me your Paypal and I'll send you beer money!


Edit: I let it loose on a directory of files and a few of them turned up oddly;

```


 4578455?.txt  4593101?.txt  4594405?.txt  4595030?.txt  4598772?.txt  4599832??4599832?.txt


```Seems to work for most of them. Any idea why there's ? marks in some of the results?

Edit edit: They also sometimes appear as:

```

4578455^M.txt  4593101^M.txt  4594405^M.txt  4595030^M.txt  4598772^M.txt  4599832^M      4599832^M.txt

```They get turned into nonsense characters if I look at them from Windows over a samba share. The contents are A-OK though.

---

### Post by Vaphell on 2012-10-23
These ^M come from the fact that in windows end-of-line is marked with \r\n while linux uses only \n and that \r gets into the content itself (^M=\r=CR=carriage return)

try to add this:
```
id=$( awk '/Customer No/{ print $NF }' "$f"** | tr -d '\r'** )
```

this one is especially interesting, looks like 4599832\r\t4599832\r ?
**4599832??4599832?.txt**

to find out what exactly is there, do this with that specific file:
```
awk '/Customer No/{ print $NF }' 4599832*.txt | od -c
```
or maybe Customer No line appeared twice and there are 2 id's mashed together?

---

