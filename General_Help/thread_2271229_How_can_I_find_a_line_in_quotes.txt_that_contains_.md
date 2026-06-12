---
title: "How can I find a line in quotes.txt that contains specific words?"
date: 2015-03-28
forum: General Help
---

### Post by Rytron on 2015-03-28
Hi.

I have a text file called quotes.txt. How can I find a line(s) that contains certain words? E.g. Find all lines that contain both **AronRa** and **Atheists** and atheists on the same line. I can use find in the text editor (Geany/Pluma), but that only finds one word at a time.

Would it be possible to copy the the applicable line(s) into a new text file?

Thanks.

---

### Post by steeldriver on 2015-03-28
two greps?

```

grep 'AronRa' quotes.txt | grep 'Atheists' > somefile.txt

```

one perl?

```

perl -ne 'print if /AronRa/ && /Atheists/' quotes.txt > somefile.txt

```

an awk?

```

awk '/AronRa/ && /Atheists/' quotes.txt > somefile.txt

```

---

### Post by Rytron on 2015-03-28
> **steeldriver said:**
> two greps?

```

grep 'AronRa' quotes.txt | grep 'Atheists' > somefile.txt

```

Hi steeldriver.

Thank you, that worked perfectly.

---

### Post by Rytron on 2015-03-28
> **steeldriver said:**
> two greps?

```

grep 'AronRa' quotes.txt | grep 'Atheists' > somefile.txt

```

one perl?

```

perl -ne 'print if /AronRa/ && /Atheists/' quotes.txt > somefile.txt

```

Both gave the same correct output.

Note that another quote line has 'AronRa' and 'Atheist' (singular). Is there a method to also include that and have all greps case insensitive?

Something like?
```
grep 'AronRa' quotes.txt | grep 'Atheists' | grep 'Atheist' > somefile.txt
```

---

### Post by Rytron on 2015-03-28
> **steeldriver said:**
> two greps?

...

```

awk '/AronRa/ && /Atheists/' quotes.txt > somefile.txt

```

Also works great. You are an ace at coding.

---

### Post by ajgreeny on 2015-03-28
You can use the -i option with grep to ignore the case.
For the use of the words in singular you can just search singular; both versions will then show as the plural word will.contain the singular.
For words such as mouse and mice grep will.not work for both and I think you would hsve to use the awk version.

---

### Post by matt_symes on 2015-03-28
Hi

egrep can also be used if you know the order of the words you're searching for.

```
matthew-laptop:/home/matthew:2 % cat ttt
line 1
AronRa test atheist test
line 3
matthew-laptop:/home/matthew:2 % egrep -i "aron.*eist" ttt 
AronRa test atheist test
matthew-laptop:/home/matthew:2 % 
```

Using egrep you can add anchors and other regex.

Kind regards

---

### Post by Rytron on 2015-04-10
With the same file, how can I use case insensitive commands (for awk, grep, and perl) for e.g. find both 'Agnostic' and 'YouTube' (both are on same line in text file) by only using a command like so (all searches in lc):

```
awk '/agnostic/ && /youtube/' quotes.txt > somefile.txt
```

---

### Post by steeldriver on 2015-04-10
With perl, you can add a regex *modifier* (in this case, i for case *i*nsensitive):

```

perl -ne 'print if /agnostic/i && /youtube/i' quotes.txt > somefile.txt

```

With awk, there is an IGNORECASE flag
```

awk 'BEGIN{IGNORECASE=1;} /youtube/ && /agnostic/' quotes.txt > somefile.txt

```

With grep, you can use the -i command-line switch
```

grep -i 'youtube' quotes.txt | grep -i 'agnostic' > somefile.txt

```

---

### Post by Rytron on 2015-04-11
Cheers steeldriver. That's perfect. ):P

---

