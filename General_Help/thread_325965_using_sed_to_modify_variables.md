---
title: "using sed to modify variables"
date: 2006-12-26
forum: General Help
---

### Post by summersab on 2006-12-26
Alright, so here's what I want to do. I need to be able to modify a variable in bash using sed. I cannot figure out the syntax. So far, I know:

value=$(something something something)
sed 's/find/replace/g' $value

However, the second line doesn't work. I want to find an occurance within a local variable and modify it. If I have to create a second variable, that's fine. If you want to know the practical purpose, I'm trying to modify gconf lists from the prompt. I set

value=$(gconftool-2 --get /key/in/gconf)

Then do the sed operation,

sed 's/\]/,newvalue/g' $value

Then reset the key

gconftool-2 --set --type list --list-type string /key/in/gconf $value

So, if I can modify variables, that will be the key to happiness. Thanks for your help!

---

### Post by neouser99 on 2006-12-26
If I am understanding correctly, this looks like some string manipulation, from within a bash script.

I would suggest using regex, since that is all sed is doing anyway, but in a more round about way.

[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

-neo

---

### Post by summersab on 2006-12-26
Absolutely perfect and exactly what I wanted to do! Thank you so much!

value=$(gconftool-2 --get /key/in/gconf)
value=${value/find/replace}
gconftool-2 --set --type list --list-type string /key/in/gconf $value

BINGO! I win . . .

---

