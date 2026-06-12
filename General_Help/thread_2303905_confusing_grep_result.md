---
title: "confusing grep result"
date: 2015-11-22
forum: General Help
---

### Post by ktat on 2015-11-22
Hi,

I'm wondering if anyone can help me to understand what is going on with the attached file.

```
grep T scn01-1.txt 
```
gives the result
```
Binary file scn01-1.txt matches
```

As this is just a .txt file, I find this odd.  The file was created by a website, [http://www.onlineocr.net/]("http://www.onlineocr.net/").

If I change the command to
```
grep -a T scn01-1.txt 
```
all the lines with "T" are printed, but then when I change it to:
```
grep -a To scn01-1.txt 
```
for some reason there are no matches.  I would love to know what is going on here.

Thank you.

---

### Post by steeldriver on 2015-11-22
According to 'file', it is UTF-16 encoded

```

file scn01-1.txt 
scn01-1.txt: Little-endian UTF-16 Unicode text, with CRLF, CR line terminators

```

When you do 'grep -a T scn01-1.txt', grep is likely treating each multi-byte character as an ASCII character followed by a NUL; what looks like To in the output is actually \@T\@o but the NUL bytes are non-printing. Using 'xxd' for example:

```

grep -a T scn01-1.txt | xxd
0000000: 0020 0054 006f 000d 000a 0020 0054 006f  . .T.o..... .T.o
0000010: 000d 000a 0020 0054 006f 000d 000a 0020  ..... .T.o..... 
0000020: 004d 0065 0073 0073 0061 0067 0065 0020  .M.e.s.s.a.g.e. 
0000030: 0020 0054 0068 0061 0074 0020 0077 0061  . .T.h.a.t. .w.a
0000040: 0073 0020 0061 0020 006c 0061 0074 0065  .s. .a. .l.a.t.e
0000050: 0020 0072 0065 0070 006c 0079 0020 0074  . .r.e.p.l.y. .t
0000060: 0068 006f 0075 0067 0068 0074 0020 0079  .h.o.u.g.h.t. .y
0000070: 006f 0075 0020 0066 006f 0072 0067 006f  .o.u. .f.o.r.g.o
0000080: 0074 0074 0065 006e 0020 0062 006f 0075  .t.t.e.n. .b.o.u
0000090: 0074 0020 006d 0065 000d 000a 0020 0054  .t. .m.e..... .T
00000a0: 006f 000d 000a 0020 0054 006f 000d 000a  .o..... .T.o....
00000b0: 0020 0054 006f 000d 000a                 . .T.o....

```

You can probably convert to ASCII or UTF-8 using 'iconv' e.g.

```

iconv -f UTF-16 -t ASCII//TRANSLIT scn01-1.txt | grep -o 'To'

```

---

### Post by ktat on 2015-11-22
Thank, you - all is clear now ;)

---

