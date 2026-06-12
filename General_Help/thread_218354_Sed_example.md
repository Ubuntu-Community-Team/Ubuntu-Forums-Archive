---
title: "Sed example"
date: 2006-07-18
forum: General Help
---

### Post by pat270881 on 2006-07-18
hello,

I read an sed example on a website:

$ sed -e 's/<[^>]*>//g' myfile.html

the explanation says, that this means [^>] any non > caracter. But why does ^> means any non > caracter? - I thought that ^ stands for the beginning of a line...??

the example is from this site: [http://www.gentoo.org/doc/en/articles/l-sed2.xml](http://www.gentoo.org/doc/en/articles/l-sed2.xml)

thanks in advance

---

### Post by kabus on 2006-07-18
> **pat270881 said:**
> 
the explanation says, that this means [^>] any non > caracter. But why does ^> means any non > caracter? - I thought that ^ stands for the beginning of a line...??


[abc] matches any of the characters a, b and c, [^abc] matches any character *but* a, b and c.
The caret has a different meaning within the brackets.
More on regular expressions here:

[http://sitescooper.org/tao_regexps.html](http://sitescooper.org/tao_regexps.html)

---

