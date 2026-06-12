---
title: "Renaming a large amount of files while retaining the order?"
date: 2013-03-26
forum: General Help
---

### Post by Panderz on 2013-03-26
Hi all, I've got a possibly nooby question, I'm not sure. This is my firt forum post btw ^_^ .I've downloaded about 100 videos off of youtube, but alot of them are named something different even though they're from the same playlist. What I want to do is just rename the file to Mpt(order number here).mp4. I know what I want to do, but am not sure about the syntax.

So what I have in mind is something like this...

mv Mass(*number in series here, ideally I would like it to read the number as a variable*).mp4 Mpt(*the var number here*).mp4

Can anyone help me??

---

### Post by Vaphell on 2013-03-26
more details about naming convention would be nice, some examples?

---

### Post by Panderz on 2013-03-26
The majority of the files I dl'd are named "Mass Effect 3 PC Sentinel INSANITY pt.(insert number here).mp4. I want to name as Mpt(insert number here).mp4

---

### Post by Panderz on 2013-03-26
Is there no help for a computer-illiterate's son? :(

---

### Post by Vaphell on 2013-03-26
```
for f in "Mass Effect 3"*[0-9].mp4; do n=${f%.*}; n=${n##*[^0-9]}; **echo** mv "$f" "Mpt${n}.mp4"; done
```

```
rename -**n**v 's/.*[^0-9]([0-9]+[.]mp4$)/Mpt$1/' "Mass Effect 3"*[0-9].mp4
```

both of these won't actually rename files but print out what would happen if echo/n (bolded) were not present.

---

### Post by Panderz on 2013-03-26
Thank you very much

---

### Post by Panderz on 2013-03-26
How do I close /:

---

