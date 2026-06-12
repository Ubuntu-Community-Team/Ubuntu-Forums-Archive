---
title: "help with find and grep"
date: 2013-06-02
forum: General Help
---

### Post by emonti on 2013-06-02
Hi  I want to search through a list of files and match on the presence of two or more words(i.e. must all be present in the file) and output the matches, each highlighted in colour. 

The output should be prefixed by filename and line number for (each match)

 I tried the following:   

```

user$ cat test.txt
  Gresham's law: bad money chases out good money

```

```

    find . -name '*txt'  | while read filename ; do grep -Hin "law" $filename | grep -Hin "money" | grep -Hin "Gresham" ; done

(standard input):1:(standard input):1:./test.txt:1:Gresham's law: bad money chases out good money

```

   In the above output, I can see a useful result... but:  

1. I don't need to see ```
'(standard input):1:(standard input):1:'
``` and 

2. Only the word 'Gresham' is highlighted in colour... I want each search term to be highlighted in colour in the final output, if possible.  

Any help would be much appreciated.  Thanks.
p.s. bash -version: GNU bash, version 4.2.24(1)-release (x86_64-pc-linux-gnu)

---

### Post by steeldriver on 2013-06-02
The highlighting will be lost if you pipe the grep output through something else - so in your case only the final grep's colour is showing

Yo can tell a single grep to match on multiple search patterns using -e pattern1 -e pattern2 etc. - also you can execute grep directly from find instead of having a separate loop e.g. something like this should work:

```
find -name '*.txt' -exec grep -Hin -e 'law' -e 'money' -e 'Gresham' {} +
```

EDIT: oops, -e ORs the patterns - I just noticed you want to AND them - I'll have a think about that and get back to you

---

### Post by rnerwein on 2013-06-02
hi
how about this: grep -inH -e 'bad' -e 'money' -e 'Gresham'  `find . -type f`
ciao

---

### Post by steeldriver on 2013-06-02
So... I don't think there's an easy way to do it with grep

You could do something like

```

while read -rd $'\0' file; do [[ $(grep -i 'law' "$file") && $(grep -i 'money' "$file") && $(grep -i 'Gresham' "$file") ]] && grep -Hin -e 'law' -e 'money' -e 'Gresham' "$file"; done < <(find . -name '*.txt' -print0)

```

which finds files that contain all the patterns and then greps again to highlight the instances (it's more efficient than it looks because the [[ A && B && C ]] test construct works from L to R and stops as soon as any part evaluates false)

With awk in the mix, I think that you could do it like

```
while read -rd $'\0' file; do awk 'BEGIN{RS=""}; /law/ && /money/ && /Gresham/ {print}' "$file" | grep --label="$file" -Hin -e 'law' -e 'money' -e 'Gresham' "$file"; done < <(find . -name '*.txt' -print0)
```

which may be faster than multiple greps depending on file size

---

### Post by emonti on 2013-06-02
Thanks for the replies.

I tried the solutions but no cigar. I get OR results. As you noted, [**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500"), I'm looking to AND.

My knowledge of these tools is bare essentials, more or less, so the closest I've come is the command I showed in the intial post.

Can anyone explain why it is I get :

<CODE>
'(standard input):1:(standard input):1:'
</CODE>

?

---

### Post by steeldriver on 2013-06-02
Yes - you get [FONT=courier new](standard input)[/FONT] because you're calling the second and third greps with the -H (print filename) flag when you are piping input to them from stdin - so there **is** no filename. You can work around this if your script keeps track of the filename and you use the --label="$filename" parameter to the remaining greps - see my example with awk in post #4

BTW I realized after posting it that the awk version is not going to be case-insensitive - there are ways to fix that, if you decide to give the awk route a try

---

### Post by steeldriver on 2013-06-02
sorry I just realized there was a typo in my previous reply - I had tested it with a different set of keywords and one of them crept into my reply ('Brown' instead of 'money'). Try it again with:

```

while read -rd $'\0' file; do [[ $(grep -i 'law' "$file") &&  $(grep -i 'money' "$file") && $(grep -i 'Gresham' "$file") ]]  && grep -Hin -e 'law' -e 'money' -e 'Gresham' "$file"; done <  <(find . -name '*.txt' -print0)

```


```

$ cat test.txt
Gresham's law:
Bad money chases out good money
$
$
$ while read -rd $'\0' file; do [[ $(grep -i 'law' "$file") && $(grep -i 'money' "$file") && $(grep -i 'Gresham' "$file") ]] && grep -Hin -e 'law' -e 'money' -e 'Gresham' "$file"; done < <(find . -name '*.txt' -print0)
./test.txt:1:Gresham's law:
./test.txt:2:Bad money chases out good money

```

---

### Post by emonti on 2013-06-02
Aaahh! It works!!!

Thank-you. That is a very useful command. I will use it often. (this one worked for me: 

```
while read -rd $'\0' file; do [[ $(grep -i 'law' "$file") && $(grep -i 'money' "$file") && $(grep -i 'Gresham' "$file") ]] && grep -Hin -e 'law' -e 'money' -e 'Gresham' "$file"; done < <(find . -name '*.txt' -print0))
```

Thank-you for the explanation, too... about standard input.

I will try to understand the rest of the command, too.

---

### Post by emonti on 2013-06-02
I found that this works too:

```

find . -name '*txt'  | while read filename ; do grep -Hin "law" $filename | grep -i "money" | grep -i "Gresham" ; done | grep -Ei "Gresham|law|money"
```

(but only if all the words are on the same line)

---

### Post by steeldriver on 2013-06-02
... yes I deliberately made my test.txt file split into 2 lines to make sure it would cover the more general case, since that seemed to be what you were asking for in your original post

If this is something you need to do a lot of, you could save the trouble of having to type each keyword in 2 places by putting a list of keywords in a file:

```

$ cat keywords
money
Gresham
law

```

 and then doing something like

```

while read -rd $'\0' file; do
  allfound=1
  while read -r keyword; do
    grep -qi "$keyword" "$file" 2>/dev/null
    if [ "$?" -ne 0 ]; then
      allfound=0;
      break;
    fi
  done < keywords
  if [ "$allfound" -eq 1 ]; then
    grep -Hinf keywords "$file"
  fi
done < <(find . -name '*.txt' -print0)

```

---

### Post by emonti on 2013-06-02
Is there a way I can put this in a script and take in a list of arguments(being 'N' number of words)... instead of pasting each word into the command twice?

ok thanks... just read your reply.... (digesting)

---

### Post by kjohri on 2013-06-03
```
find . -name "*.txt" | xargs grep -Hin 'string1\|string2'
```

---

### Post by emonti on 2013-06-03
[**[COLOR=#000000]kjohri[/COLOR]**]("http://ubuntuforums.org/member.php?u=733211"), thanks but your solution gives me string1 OR string2.

If you read the question and responses, I'm looking for string1 AND string2.

Idealistically speaking, steeldriver's solution may be a bit verbose but it works perfectly.

Thanks anyway.

---

