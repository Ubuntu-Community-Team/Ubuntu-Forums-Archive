---
title: "formatting Text file (sed?)"
date: 2007-03-23
forum: General Help
---

### Post by Tadhg on 2007-03-23
I have a quick question.

I have a text file which contains english words,basically,it's a dictionary. At the moment, the words are single spaced with multiple words on a line.

I want to edit it so each word is on it's own seperate line. Any idea how this is done? I'd imagine using sed or some such?

---

### Post by Arby on 2007-03-23
I don't know sed but I could probably do it in perl. Something along the lines of this (untested)

```

open(FH, $ARGV[0]);
while (<FH>) {
       my @line = split /\s/, $_;
       foreach my $word (@line) {
                     print "$word\n";
                     }
       }

``` save that as 'reformat.pl' and call it like this ```
perl reformat.pl inputfile >output.txt
``` That could probably be rewritten to get rid of the 'open' line and do it as a one liner if there are any more experienced perl hackers around. I could never figure that bit out.

---

### Post by Ramses de Norre on 2007-03-23
So you want to replace each space by a newline?
This should do: ```
sed -e 'se[[:space:]]e\neg' -i file
```

---

### Post by Arby on 2007-03-23
OK, that's much nicer than my way, use that :)

---

### Post by Tadhg on 2007-03-23
Thanks for that. The sed one did it.

---

### Post by highneko on 2007-03-23
> **Ramses de Norre said:**
> So you want to replace each space by a newline?
This should do: ```
sed -e 'se[[:space:]]e\neg' -i file
```
Why the -e and -i? Wouldn't the following be the same?
```
#example
sed 's/ /\ntest/g'<<<'    '
#on a file
sed 's/ /\n/g' file
```

---

### Post by Ramses de Norre on 2007-03-25
> **highneko said:**
> Why the -e and -i? Wouldn't the following be the same?
```
#example
sed 's/ /\ntest/g'<<<'    '
#on a file
sed 's/ /\n/g' file
```

When you use "-e" in front of the action, you can set multiple actions for one file. So I keep the habit of using "-e" for only one action too.
The "-i" tells sed to write directly to the file instead of stdout, so no redirecting is needed.

---

### Post by shane2peru on 2007-10-19
> **Ramses de Norre said:**
> When you use "-e" in front of the action, you can set multiple actions for one file. So I keep the habit of using "-e" for only one action too.
The "-i" tells sed to write directly to the file instead of stdout, so no redirecting is needed.

Ok, you are the sed King.  You helped me in another post with sed and I have learned alot about sed and have used it several times.  It is a great app.  Here is what I have now, and I can't figure out how to fix this text file.  

```

 CAPIT. I.

 

 LIBRO de la generacion de Ie&#353;u Chri&#353;to hijo de David, hijo de Abraham.

 

 2 Abraham engendrò à I&#353;aac. Y I&#353;aac engendrò à Iacob. Y Iacob engendrò à Iudas, 

y à &#353;us hermanos.

 

 3 Y Iudas engendró de Thamar à Phares y á Zarã. Y Phares engendró à E&#353;rom. Y 

E&#353;rom engendró à Aram.

 

 4 Y Aram engendró à Aminadab. Y Aminadab engendró à Naa&#353;on. Y Naa&#353;on engendró à 

Salmon.

 

 5 Y Salmon engendró de Raab à Booz. Y Booz engendró de Ruth à Obed. Y Obed 

engendró à Ie&#353;&#353;e.

```
This is a sample of the text that I have.  I want to change it to this:
```

 CAPIT. I.

 LIBRO de la generacion de Ie&#353;u Chri&#353;to hijo de David, hijo de Abraham.

 2 Abraham engendrò à I&#353;aac. Y I&#353;aac engendrò à Iacob. Y Iacob engendrò à Iudas, 
y à &#353;us hermanos. [COLOR="Red"]This is only one line, just wrapped here[/COLOR]

 3 Y Iudas engendró de Thamar à Phares y á Zarã. Y Phares engendró à E&#353;rom. Y 
E&#353;rom engendró à Aram. [COLOR="Red"]This is only one line, just wrapped here[/COLOR]

 4 Y Aram engendró à Aminadab. Y Aminadab engendró à Naa&#353;on. Y Naa&#353;on engendró à 
Salmon. [COLOR="Red"]This is only one line, just wrapped here[/COLOR]

 5 Y Salmon engendró de Raab à Booz. Y Booz engendró de Ruth à Obed. Y Obed 
engendró à Ie&#353;&#353;e. [COLOR="Red"]This is only one line, just wrapped here[/COLOR]

```
I have tried several different sed regex combinantions, and have looked for a detailed example guide and can't seem to find it.  How can I do that with sed?  Any help would be greatly appreciated!  Thanks. 

Shane

---

