---
title: "Inserting Date TO Second Line of Text File"
date: 2013-10-31
forum: General Help
---

### Post by chiques on 2013-10-31
Hello Community,
I'm trying to insert the date to the second line of my output.txt file in a script. I've tried sed without any success. Any hints on what I might doing wrong?

```

#!/bin/bash
echo "hello world">output.txt

sleep 1

sed '2 i\ My date goes here' output.txt

sleep 1

```

---

### Post by btindie on 2013-10-31
with
```
echo "hello world">output.txt
```
there is no second line so it can't Insert it. If there were more lines in output.txt it would work.

You'd need to Append it
```
sed -e '1 a\My date goes here' output.txt
```

though you could just do
```
 echo "$(date)" >> output.txt
```

it depends what you're trying to achieve though...?

---

### Post by steeldriver on 2013-10-31
How about

```
sed '1r/dev/stdin' *yourfile* < <(date)
```

---

