---
title: "Bash script help"
date: 2015-06-20
forum: General Help
---

### Post by markodd on 2015-06-20
Hey, I need help on a bash script!

Basically, I need a bash script to create me an input file. I'll then use that file as an input to another program.

Let's say I have this table:

```
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
```


I need a script to add decimal places to the third column. something like:

```
2+0.25
1+0.25
2+0.25
1+0.25
2+0.25
3+0.25
```

In order to become

```
2.25
1.25
2.25
1.25
2.25
3.25
```


My idea was to do something like:

```
NAME=aname

for sumthis in 0.25 0.5 0.75 1.0

do
cat > $NAME.sumthis.in << EOF

A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3

EOF

```
That third table, however, needs to be itself + sumthis.

Can anyone help me please? I'd be forever in your dept.

---

### Post by steeldriver on 2015-06-20
I'd probably use awk for something like this

```

$ awk -v sumthis=0.25 '{$3+=sumthis}1' << EOF
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
EOF
A 1.1 2.25
B 1.2 1.25
A 1.3 2.25
B 1.4 1.25
A 1.5 2.25
B 1.7 3.25

```

---

### Post by markodd on 2015-06-20
> **steeldriver said:**
> I'd probably use awk for something like this

```

$ awk -v sumthis=0.25 '{$3+=sumthis}1' << EOF
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
EOF
A 1.1 2.25
B 1.2 1.25
A 1.3 2.25
B 1.4 1.25
A 1.5 2.25
B 1.7 3.25

```


I don't understand how that would work. What does "$ awk -v sumthis=0.25 '{$3+=sumthis}1'" do exactly? I need something that sums "sumthis" inside the "for" cycle, so that a file is created for each "sumthis".

Also, there's a whole lot more information in the file I need to create. The only thing that change is that table though.

---

### Post by steeldriver on 2015-06-20
[LIST]
[*][FONT=courier new]$[/FONT] just denotes the command prompt 
[*][FONT=courier new]awk -v sumthis=0.25[/FONT] says to run the awk program, passing in a value 0.25 for the variable sumthis 
[*][FONT=courier new]'{$3+=sumthis}1'[/FONT] is a little awk script that says take the third field (column) and add the value of sumthis to it, then print the line (1 is a [code golf]("https://en.wikipedia.org/wiki/Code_golf") way of doing that in awk) 
[/LIST]

To do it for multiple values of sumthis, you can wrap it in a loop e.g.

```

name=aname

for sumthis in 0.25 0.5 0.75; do
awk -v sumthis="$sumthis" '{$3+=sumthis}1' << EOF > "$name.$sumthis.in"
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
EOF
done

```

---

### Post by markodd on 2015-06-20
> **steeldriver said:**
> 
[LIST]
[*][FONT=courier new]$[/FONT] just denotes the command prompt
[*][FONT=courier new]awk -v sumthis=0.25[/FONT] says to run the awk program, passing in a value 0.25 for the variable sumthis
[*][FONT=courier new]'{$3+=sumthis}1'[/FONT] is a little awk script that says take the third field (column) and add the value of sumthis to it, then print the line (1 is a [code golf]("https://en.wikipedia.org/wiki/Code_golf") way of doing that in awk)
[/LIST]

To do it for multiple values of sumthis, you can wrap it in a loop e.g.

```

name=aname

for sumthis in 0.25 0.5 0.75; do
awk -v sumthis="$sumthis" '{$3+=sumthis}1' << EOF > "$name.$sumthis.in"
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
EOF
done

```

Sadly, this won't work for me. For the following reason:

I need something that creates files, with the only change between them being that third column. For example:

```
Name = aname

for sumthis in 0.25 0.5 0.75 

do

cat > $NAME.sumthis.in << EOF 

texthere
more text
even more text
some more text here

A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3


EOF

```
I need sumthis added to that third column. The text needs to be there. I don't know how to use your idea here. Is it possible?

---

### Post by steeldriver on 2015-06-20
Well, you could cat the fixed text, and then append the table

```

for sumthis in 0.25 0.5 0.75; do
  cat << EOF > "$name.$sumthis.in"
texthere
more text
even more text
some more text here
EOF

  awk -v sumthis="$sumthis" '{$3+=sumthis}1' << EOF [COLOR=#0000ff]**>>**[/COLOR] "$name.$sumthis.in"
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
EOF
done

```

---

### Post by markodd on 2015-06-20
> **steeldriver said:**
> Well, you could cat the fixed text, and then append the table

```

for sumthis in 0.25 0.5 0.75; do
  cat << EOF > "$name.$sumthis.in"
texthere
more text
even more text
some more text here
EOF

  awk -v sumthis="$sumthis" '{$3+=sumthis}1' << EOF [COLOR=#0000ff]**>>**[/COLOR] "$name.$sumthis.in"
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
EOF
done

```

Hey, thank you. I think this is closer to what I want, though not functioning just yet. 

What if there's also text after the table and the text before the table consists of text with symbols such as $ and # and all that? 

```
Name = aname

for sumthis in 0.25 0.5 0.75 

do

cat > $NAME.sumthis.in << EOF 

&texthere
/more text
even more text
some more text here

A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3

moretext here bla bla
```

On second thought, this is way too hard. There must be a simpler way to do this :// Maybe I'll just learn python so I can do this...

---

### Post by steeldriver on 2015-06-20
You can simply append other stuff after the table with another cat << EOF >> $outfile

You can prevent shell expansion within the here-doc text by quoting any part of the end marker e.g. use "EOF" instead of plain EOF

```

for sumthis in 0.25 0.5 0.75; do

  outfile="$name.$sumthis.in"

  cat << "EOF" > "$outfile"
texthere
more $text
even more text
some $name text here

EOF

  awk -v sumthis="$sumthis" '{$3+=sumthis}1' << "EOF" >> "$outfile"
A     1.1     2
B     1.2    1
A     1.3     2
B     1.4    1
A     1.5    2
B     1.7     3
EOF

  cat << "EOF" >> "$outfile"

more $text after the table
even more text after the table
some $name text here after the table
EOF

done

```

---

### Post by markodd on 2015-06-20
@steeldriver, you're the best man. Thank you very much!

---

