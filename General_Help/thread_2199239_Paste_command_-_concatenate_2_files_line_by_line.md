---
title: "Paste command - concatenate 2 files line by line"
date: 2014-01-12
forum: General Help
---

### Post by Kevin McCready on 2014-01-12
I'm trying to use the paste command to concatenate 2 files line by line into file3.
File1
AAA
BBB
CCC

File2 
111
222
333

I want file3 to look like this:
AAA 111
BBB 222
CCC 333

But when I try: 
paste file1 file2 >file3
I get
AAA
BBB
CCC
111
222
333

And when I try:
paste -d '\n' file1 file2 >file3
I get the same problem.

---

### Post by Dave_L on 2014-01-12
That's odd. If I use your example, it works correctly.

Does the output of this:

```
paste --version
```

look similar to this?

> paste (GNU coreutils) 8.13
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David M. Ihnat and David MacKenzie.

If so, could you post the two input files as .txt attachments?

---

### Post by Kevin McCready on 2014-01-13
Yes my paste version is the same.
I've attached the files

---

### Post by Vaphell on 2014-01-13
these files have no newlines in them, it's all done with the carriage return.
also they appear to be of different lengths
```
$ sed 's/\r/\n/g' file1.txt | wc -l
990
$ sed 's/\r/\n/g' file2.txt | wc -l
987
```

```
$ paste  <( sed 's/\r/\n/g' file1.txt ) <( sed 's/\r/\n/g' file2.txt )
&#20113;&#33150;&#33268;&#38632;	Yún téng zhì y&#468;
&#38706;&#32467;&#26216;&#38684;	lù jié chen shu&#257;ng
&#34425;&#38675;&#38686;&#36745;	hóng ní xiá hu&#299;
&#38654;&#27785;&#38649;&#38477; 	wù chén báo jiàng
&#26149;&#29983;&#22799;&#38271;	 Ch&#363;nsh&#275;ng xià zh&#462;ng
&#31179;&#25910;&#20908;&#34255;	qi&#363;sh&#333;u d&#333;ng cáng
&#26102;&#20196;&#24212;&#20505;	shílìng y&#299;ng hou
&#23506;&#26469;&#26257;&#24448; 	hán lái sh&#468; w&#462;ng
&#36828;&#21476;&#27946;&#33618;	 Yu&#462;ng&#468; hónghu&#257;ng
&#28023;&#30000;&#27815;&#26705;	h&#462;itián c&#257;ngs&#257;ng
&#38470;&#22320;&#28418;&#31227;	lùdì pi&#257;oyí
&#26495;&#22359;&#30896;&#25758; 	b&#462;nkuài pèngzhuàng
...
&#36203;&#38384;&#22030;&#38887;	cénkuíqiú luán
&#22622;&#31482;&#37084;&#20924;	 X&#299;n r&#468; jí shèn
&#31668;&#37071;&#29088;&#38425;	díji&#283;chéng r&#462;n
&#23697;&#22862;&#35032;&#26686; 	x&#299;n fú jì zhào
&#24571;&#27741;&#27762;&#24910;	k&#275;w&#468;zhàn yàn
&#32735;&#35299;&#19998;&#20873;	 J&#299; shé tóng móu
&#27427;&#33531;&#27982;&#32903;	lí gé xu&#257;nyuán
&#26607;&#20213;&#28251;&#26191; 	
&#23879;&#20312;&#20189;&#32554;	
&#40654;&#33883;&#36713;&#36757; 	

```

---

### Post by stinkeye on 2014-01-13
Use gedit to change the files from **mac os classic** to **unix/linux**.

---

### Post by Kevin McCready on 2014-01-13
Thanks for that. I forgot to take out a few lines in one of them. They were both leafpad files. How can I tell the difference between a carriage return and newline?

---

### Post by Dave_L on 2014-01-13
Leafpad can also save with different line endings: LF (Unix/Linux), CR+LF (DOS/Windows) and CR (Mac).

The "file" command tells you what kind of line endings a file has:

```
$ file linuxfile.txt
linuxfile.txt: ASCII text
```

```
$ file macfile.txt
macfile.txt: UTF-8 Unicode text, with CR line terminators
```

```
$ file windowsfile.txt
windowsfile.txt: ASCII text, with CRLF line terminators
```

You can also view the file as hexadecimal. The "hexdump" command will do that. 
LF = 0A
CR = 0D
CRLF = 0D0A

---

### Post by Vaphell on 2014-01-13
*od -c* is more readable

```
$ od -c file2.txt | head -5
0000000   Y 303 272   n       t 303 251   n   g       z   h 303 254    
0000020   y 307 224  [COLOR="#0000FF"]\r[/COLOR]   l 303 271       j   i 303 251       c   h   e
0000040   n       s   h   u 304 201   n   g  [COLOR="#0000FF"]\r[/COLOR]   h 303 263   n   g    
0000060   n 303 255       x   i 303 241       h   u 304 253  [COLOR="#0000FF"]\r[/COLOR]   w 303
0000100 271       c   h 303 251   n       b 303 241   o       j   i 303
```

with newlines it would look like this
```
$ sed 's/\r/\n/g' file2.txt | od -c | head -5
0000000   Y 303 272   n       t 303 251   n   g       z   h 303 254    
0000020   y 307 224  [COLOR="#0000FF"]\n[/COLOR]   l 303 271       j   i 303 251       c   h   e
0000040   n       s   h   u 304 201   n   g  [COLOR="#0000FF"]\n[/COLOR]   h 303 263   n   g    
0000060   n 303 255       x   i 303 241       h   u 304 253  [COLOR="#0000FF"]\n[/COLOR]   w 303
0000100 271       c   h 303 251   n       b 303 241   o       j   i 303
```

---

### Post by Kevin McCready on 2014-01-13
Thanks Guys
That's been wonderful!
I'll mark it solved.
Major learnings for me here have been:
1.
'\' means tell sed that what follows is actual text (not regex) until you see the '/'
2.
paste file1 file2 #puts the files together into one file line by line so that are concatenated side by side or interleaved; but files must be formatted with newline, not with CR
3. 
the od command wasn't even on my list of commands. Now it is.

Cheers!

---

