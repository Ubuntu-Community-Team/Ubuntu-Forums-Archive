---
title: "sed / grep / awk / whatever...help?"
date: 2008-06-22
forum: General Help
---

### Post by calman on 2008-06-22
I have this line: 

```
 <input type="hidden" name="video_id" value="q48JEl45xlg" />
```

and I want to use sed or another program to get the output in a bash script:

```
q48JEl45xlg
```

I've googled this to death and can't figure it out....can anyone help?

---

### Post by unutbu on 2008-06-22
If the text is in a file called test
```
 <input type="hidden" name="video_id" value="q48JEl45xlg" />
```

then 
```
sed -e 's/.*value="\(.*\)".*/\1/' < test
```

should work.

---

### Post by calman on 2008-06-22
It works perfectly, thanks for the quick response.  I don't know why I had trouble with it.

---

