---
title: "Usenet reader suggestions please"
date: 2007-05-12
forum: General Help
---

### Post by Subban on 2007-05-12
Could anyone please suggest a usenet reader that will allow the saving of articles using the subject title as the filename. I would like to be able to select a large number of articles and just dump them to disk in bulk.

I have tried Pan as I recalled using that feature, but apparently it was dropped unfortunatly :S

I tried using Thunderbird, but couldn't see a way to do it, same with Sylpheed. I also tried Gravity and Agent under wine/virtualbox.

I rather suspect Sylpheed could be made to do it with the Actions, but after trying to achieve it I drew a blank.

NB. Some of the mentioned readers can save a mass selection, but does so using a useless naming convention or the msgid of the article, not using the subject name (makes reading later a real 'lucky dip affair).

---

### Post by Subban on 2007-05-14
Gave up on the search and scripted a workaround. Saved all the articles with their names as just the msgidss, then ran the following in a bash script over them:

```
for a in *; do mv "$a" `grep -m1 -i ^subject: $a|cut -b 10-|tr "/ ?" "___"`; done
```

It just greps through, finds the Subject: header and uses it as the new name. Then used a nautilus script I had already done to remove the headers:

```
#!/bin/sh
for arg; do

	sed '1,/^$/d' "$arg" > aasedtmp.txt
	mv aasedtmp.txt "$arg"
done
```

Job done; once I gave up on finding a news reader to actually save the articles in a decent manner ;)

---

