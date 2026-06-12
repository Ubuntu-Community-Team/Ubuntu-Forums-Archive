---
title: "Search and replace text with variables?"
date: 2013-01-29
forum: General Help
---

### Post by CrewDK on 2013-01-29
Is it possible somehow in bash script to organize a search and replace text using variables?

Now I do it like this:


```

grep-rl "what_replace" where_replace | xargs perl -p -i -e 's /what_replace/on_what_replace/g'
```
Here instead "on_what_replace" I want to substitute a variable. But nor $name, nor \$name does not help. Is this posible at all?

---

### Post by papibe on 2013-01-29
Hi CrewDK. Welcome to the forums ):P

The syntax $var works generally, but it is best to quote your variables in case they have special characters:
```
#!/bin/bash
old="what_replace"
new="new_value"

sed "s/"$old"/"$new"/g" input_file.txt
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by CrewDK on 2013-01-29
> **papibe said:**
> Hi CrewDK. Welcome to the forums ):P
Thank you. I decided to ask here, after i'm discovered a bunch of trolls in my native Russian forum. Not the best way to attract new users. :( 

> **papibe said:**
> 
The syntax $var works generally, but it is best to quote your variables in case they have special characters:
```
#!/bin/bash
old="what_replace"
new="new_value"

sed "s/"$old"/"$new"/g" input_file.txt
```Hope it helps. Let us know how it goes.
Regards.

Thanx again. I'll try this tomorrow on my work.

---

### Post by CrewDK on 2013-01-29
Could not resist. Even in spite of the fact that now 2 AM on my side. :) 

Well, am i correct, that in my case correct code will be next: 

```

test1="crew"

sed "s/"test"/"$test1"/g" ./test.txt > ./test2.txt
mv ./test2.txt ./test.txt

```


   SED does not change the file on the fly, but only displays the result on the screen. So I had to redirect the output to a second file and then rename it. Or is there a short way?

---

### Post by papibe on 2013-01-29
> **CrewDK said:**
> SED does not change the file on the fly, but only displays the result on the screen. So I had to redirect the output to a second file and then rename it. Or is there a short way?
Yes ;)

You can make the changes in place by using the -i option:
```
sed -i "s/"test"/"$test1"/g" ./test.txt
```
Come here often and have fun.
Regards.

---

### Post by steeldriver on 2013-01-29
*n/m too slow*

---

### Post by Vaphell on 2013-01-29
is that jumping out of the string to embed variables necessary?
In case there is a space in variables, the expression will be malformed because of unshielded spaces breaking it to pieces, eg

```
old='abc def'
new='ghi jkl'
*sed "s/"$old"/"$new"/"* = *sed "s/abc" "def/ghi" "jkl/"* # 3 strings instead of 1.
```

simple *sed "s/$old/$new/"* will work just fine

---

### Post by CrewDK on 2013-01-30
You mean it's better use single quote for variables but not double quote?

---

### Post by Vaphell on 2013-01-30
no, single quotes are used for fixed strings. '$var' is '$'+'v'+'a'+'r' and that's it.
double quotes are required because they allow for expansion of $var to its value.

What i meant was 'don't do this':
[COLOR="Blue"]"s/"[/COLOR]$old[COLOR="Blue"]"/"[/COLOR]$new[COLOR="Blue"]"/"[/COLOR]
in this form variables are 'outside' the string, which means that any space will cut the expression into pieces ([COLOR="Blue"]"s/abc"[/COLOR] [COLOR="Green"]"def/ghi"[/COLOR] [COLOR="Red"]"jkl/"[/COLOR] in my example) and sed will see not 1 but 2+ strings and will fail.
To protect against spaces you need to have variables inside ""

just use 1 big continuous [COLOR="Blue"]"s/$old/$new/"[/COLOR]

to illustrate:
```
$ how_many() { echo $#; printf "'%s'\n" "$@"; } # function printing number of parameters
$ old='abc def'
$ new='ghi jkl'
$ how_many "s/"$old"/"$new"/"
[COLOR="Red"]3
's/abc'
'def/ghi'
'jkl/'[/COLOR]
$ how_many "s/$old/$new/"
[COLOR="Blue"]1
's/abc def/ghi jkl/'[/COLOR]

```

---

### Post by CrewDK on 2013-01-30
&#1054;&#1050;. Thanx. I understand.

---

### Post by papibe on 2013-01-30
> **Vaphell said:**
> simple *sed "s/$old/$new/"* will work just fine

Good catch Vaphell ;)

---

### Post by CrewDK on 2013-02-19
Sorry for offtopic. 

On russian ubuntu support forum topic with this question was deleted after couple of weeks by moderator even without explain "why" or reply. 

I "love" russian people. :(

PS: And thank you all for your work one more time.

---

