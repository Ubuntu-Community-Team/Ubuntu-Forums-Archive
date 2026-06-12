---
title: "Bash help?"
date: 2006-10-31
forum: General Help
---

### Post by highneko on 2006-10-31
Hello. May I ask a bash question here? Please don't flame. If you think I should ask in another forum, please tell me where. However, I would still like this question answered here. Thank you!

I want to use something like: [COLOR="Red"]echo "$1" >> "$url"[/COLOR] but it doesn't save quotes when input is $1. Is it possible to keep quotes using $1 without the read command? Someone told me more quotes but refused to give an example. I figured, use it like [COLOR="Red"]Script.sh 'string'[/COLOR], but then I tried [COLOR="Red"]Script.sh 'string'''[/COLOR] and it didn't save the single quotes. Using escapes would be too tedious. An example would be nice. Thank you for taking the time to read this far!

#!/bin/bash
url="/data/documents/quicknotes.txt"
if [[ -n "$1" && -f "$url" ]]; then
echo "~~~~~~~" >> "$url"
echo "$1" >> "$url"
else
echo "error: insert error message here"
fi

I'm gonna press the post button now, I hope that's a good explanation!

---

### Post by bsussman on 2006-10-31
If you do not excape special characters, how shall you tell the interpreter to use them as not special characters?

---

### Post by highneko on 2006-10-31
> **bsussman said:**
> If you do not excape special characters, how shall you tell the interpreter to use them as not special characters?
I think read worked. but That's two presses of the enter key. One press too many for me! But, perhaps there's another way1! :-k

---

### Post by Arndt on 2006-10-31
> **highneko said:**
> Hello. May I ask a bash question here? Please don't flame. If you think I should ask in another forum, please tell me where. However, I would still like this question answered here. Thank you!

I want to use something like: [COLOR="Red"]echo "$1" >> "$url"[/COLOR] but it doesn't save quotes when input is $1. Is it possible to keep quotes using $1 without the read command? Someone told me more quotes but refused to give an example. I figured, use it like [COLOR="Red"]Script.sh 'string'[/COLOR], but then I tried [COLOR="Red"]Script.sh 'string'''[/COLOR] and it didn't save the single quotes. Using escapes would be too tedious. An example would be nice. Thank you for taking the time to read this far!

#!/bin/bash
url="/data/documents/quicknotes.txt"
if [[ -n "$1" && -f "$url" ]]; then
echo "~~~~~~~" >> "$url"
echo "$1" >> "$url"
else
echo "error: insert error message here"
fi

I'm gonna press the post button now, I hope that's a good explanation!

```
$ VAR=hi
$ echo $VAR
hi
$ echo "$VAR"
hi
$ echo \"$VAR\"
"hi"

```

---

### Post by highneko on 2006-10-31
> **Arndt said:**
> ```
$ VAR=hi
$ echo $VAR
hi
$ echo "$VAR"
hi
$ echo \"$VAR\"
"hi"

```
Thank you for trying, and for the nice example. I know how to use escapes, and like I said;
> **highneko said:**
> Using escapes would be too tedious.

---

### Post by Arndt on 2006-11-01
> **highneko said:**
> Thank you for trying, and for the nice example. I know how to use escapes, and like I said;

If you consider the addition of two characters to your script too tedious, I fail to see what would not be tedious. Please explain why you don't want to use escape characters.

There are other languages which perhaps make the use/mention distinction more palatable.

---

