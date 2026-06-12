---
title: "Bash &quot;variable sandwich&quot;?"
date: 2012-11-10
forum: General Help
---

### Post by ntzrmtthihu777 on 2012-11-10
Probably using all the wrong words, but here is my question:

```
#!/bin/bash

curl -s http://www.wizards.com/default.asp?x=dnd/arch/ag |
    cut -d\" -f10 | grep "dnd/ag" | sort -u |
while
    read ag;
do
    curl -s "www.wizards.com$ag" | grep "asp?url=/dnd/images/" |
    cut -d\= -f2 | cut -d\& -f1 | sort -u;
done    |

while
    read img;
do
    wget "www.wizards.com$img";
done

```In this script I get the source of a site, sift out the links, and then get the source for those links in turn, and then sifts out the image links and downloads them.

Because the source uses javascript I have to add "www.wizards.com/" on to $ag, is there a way to add another line of text onto $ag making a sort of sandwich, like ```
"www.wizards.com$ag$&page=1"
```?

I know it may seem redundant to tag &page=1 on the end, but some of these have multiple pages and I will be repeating this script with &page=2, 3, etc to be able to scoop them all.

[EDIT]
Just found what I think is the answer,
```
 "www.wizards.com/$ag"&page=1
```would this do the trick? I am somewhat worried about the '&' though.

[EDIT]
No, that did not do it. I think the '&' threw it off because without it does right, but I need the '&'. The correct method in this case would be
```
"www.wizards.com/$ag""&page=1"
```Marking as solved for the benefit of others.

---

### Post by HiImTye on 2012-11-10
"www.wizards.com/$ag&page=1"
or
www.wizards.com/"$ag"\&page=1
or
www.wizards.com/$ag\&page=1

---

