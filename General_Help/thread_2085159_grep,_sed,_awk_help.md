---
title: "grep, sed, awk help"
date: 2012-11-17
forum: General Help
---

### Post by MadsRC on 2012-11-17
I've tried to extract some text, with mixed results.

What I have is a text file formated like this:
```
62      abuse.ch Web abuse Tracker      httpbl.abuse.ch ipv4    -       -       b       (info)
542     Abuse.net       contacts.abuse.net      -       -       dom     i       (info)
652     abuse.ro IP RBL rbl.abuse.ro    ipv4    -       -       b       (info)
720     abuse.ro URI RBL        uribl.abuse.ro  -       -       dom     b       (info)
628     abusix.org Abuse Contact DB     abuse-contacts.abusix.org       ipv4    -       -       i       (info)
59      AHBL DNSbl      dnsbl.ahbl.org  ipv4    -       -       b       (info)

```

What I want is a way to extract, from the above, only:
```
httpbl.abuse.ch
contacts.abuse.net
rbl.abuse.ro
uribl.abuse.ro
abuse-contacts.abusix.org
dnsbl.ahbl.org
```

Some of the text extracted isn't separated by 2 '.' but 3 (like.this.is.eh?) and by 4.

So basicly i needsomething that strips finds anything connected by dots, no matter how many "sections"/octets there are.

---

### Post by Vaphell on 2012-11-17
are the columns delimited by tab?

---

### Post by MadsRC on 2012-11-17
Yes, they are delimited by tab :)

---

### Post by SuaSwe on 2012-11-17
This is the closest I can get:

```

suave@acer-lx:~$ sed 's/ \+ /\t/g' filename | tr '\t' , | awk -F, {print $3}'
> ^C
suave@acer-lx:~$ sed 's/ \+ /\t/g' filename | tr '\t' , | awk -F, '{print $3}'
httpbl.abuse.ch ipv4
contacts.abuse.net
ipv4
uribl.abuse.ro
abuse-contacts.abusix.org
dnsbl.ahbl.org

```

Turning two or more spaces into tabs; converting tabs to commas; awking out column 3. Problem I encountered was with the single space between "abuse.ro IP RBL" and "rbl.abuse.ro", hence the ipv4 thing.

Edit: if they are delimited by tab your end, you can use tr '\t' , then awk as I did above, without sed, and it will work correctly. :)

---

### Post by Vaphell on 2012-11-17
it's hard to see from the provided example which column would that be but you can try
```
awk 'BEGIN{FS="[\t]"}{ print $4; }' file
awk -F$'\t' '{ print $4; }' file
```
assuming 4th column

---

### Post by drmrgd on 2012-11-17
> **Vaphell said:**
> it's hard to see from the provided example which column would that be but you can try
```
awk 'BEGIN{FS="[\t]"}{ print $4; }' file
awk -F$'\t' '{ print $4; }' file
```assuming 4th column

Out of curiosity, why do you put '[]' in the FS statment or '$' in the '-F' option?  I've never seen that before, and I might find that handy.

---

### Post by Vaphell on 2012-11-17
that $ thing is a bash feature that interprets \x symbols, just like *echo -e*
```
$ echo 'a\tb'
a\tb
$ echo -e 'a\tb'
a	b
$ echo $'a\tb'
a	b
```
so $'\t' is simply a tab char, $'\n' would be newline, etc

and i used [] because what FS is a fullblown regex in reality and you can do things like this
```

$ echo $'a..b \t\tc' | awk '{ for( i=1; i<=NF; i++ ) print i ":" $i; }'
1:a..b
2:c
$ echo $'a..b \t\tc' | awk 'BEGIN{ FS="[\t .]"; } { for( i=1; i<=NF; i++ ) print i ":" $i; }'
1:a
2:
3:b
4:
5:
6:c
$ echo $'a..b \t\tc' | awk 'BEGIN{ FS="[\t .]+"; } { for( i=1; i<=NF; i++ ) print i ":" $i; }'
1:a
2:b
3:c
```

---

### Post by drmrgd on 2012-11-17
Oh cool!  I didn't realize that FS supports regexes.  That's going to come in handy!  Also didn't know about the '$' in bash.  Another good thing to keep in my back pocket.  Thanks!

---

### Post by MadsRC on 2012-11-17
> **SuaSwe said:**
> This is the closest I can get:

```

suave@acer-lx:~$ sed 's/ \+ /\t/g' filename | tr '\t' , | awk -F, {print $3}'
> ^C
suave@acer-lx:~$ sed 's/ \+ /\t/g' filename | tr '\t' , | awk -F, '{print $3}'
httpbl.abuse.ch ipv4
contacts.abuse.net
ipv4
uribl.abuse.ro
abuse-contacts.abusix.org
dnsbl.ahbl.org

```

Turning two or more spaces into tabs; converting tabs to commas; awking out column 3. Problem I encountered was with the single space between "abuse.ro IP RBL" and "rbl.abuse.ro", hence the ipv4 thing.

Edit: if they are delimited by tab your end, you can use tr '\t' , then awk as I did above, without sed, and it will work correctly. :)

Thank you! That did seem to work!!! Original file had 314 lines in it, and the output from that command also was 314 lines. Now i just need to test the URL's :P

---

