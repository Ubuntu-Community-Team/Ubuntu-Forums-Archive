---
title: "sort function is broken?"
date: 2015-08-05
forum: General Help
---

### Post by chipmunk02115 on 2015-08-05
I found this weird behavior with the [FONT=courier new]/usr/bin/sort[/FONT] function on my version of Ubuntu (below). Consider the tab-delimited text file of 10 rows below (blank white spaces is a tab), please see attachment or below:

[COLOR=#ff0000][FONT=courier new]bta-mir-126     1033    1133
bta-mir-1260b   378     391
bta-mir-127     178     224
bta-mir-1271    66      103
bta-mir-1277    194     178
bta-mir-128-1   4713    5362
bta-mir-1281    64      34
bta-mir-1282    121     136
bta-mir-128-2   398     506
bta-mir-1284    216     248[/FONT][/COLOR]

Call this tab-delimited text file testing0.txt. I would like to sort this file alphanumerically by the 1st (first) column alone. Here are the sequence of line commands:
[SIZE=3][FONT=courier new]
[/FONT][/SIZE][FONT=courier new][COLOR=#ff0000]sort -d -k1,1 testing0.txt > testing1.txt
cut -f1 testing1.txt |sort -d > testing2.txt
cut -f1 testing1.txt |diff - testing2.txt[/COLOR][/FONT][SIZE=3]
[/SIZE]
I expected the last line command [FONT=courier new]diff[/FONT] to be empty - but it turns out that "bta-mir-1281" goes before or after "bta-mir-128-1", depending on whether I sort the 1st column with other columns or not.

I have used the sort function on unix for years and have never seen this odd behavior which I think is a bug. I have tested these 3 command lines on the tab-delimited text file on SunOS, RedHat and Mac unix flavors, and every one returned empty diff in the last line, as expected.

I would be deeply grateful if someone can spot what I am doing wrong, or tell whether there is indeed a bug with the sort function in my version of Ubuntu. Thank you in advance! 

Ubuntu 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:21:34 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by papibe on 2015-08-05
Hi chipmunk02115.

I believe your are suffering from the "last resort comparison", a standard set on POSIX.

If you disable it by using the option **--stable** (or just **-s**), you should fix your difference problem.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by chipmunk02115 on 2015-08-05
Thank you very much Papibe - per your suggestion, I modified my 3 command lines to:

[COLOR=#ff0000][FONT=courier new]sort **-s** -d -k1,1 testing0.txt > testing1.txt
cut -f1 testing1.txt |sort **-s** -d > testing2.txt
cut -f1 testing1.txt |diff - testing2.txt[/FONT][/COLOR]

and this time around, the [FONT=courier new]diff[/FONT] in the 3rd line is indeed empty (as opposed to previously where it returned a 1 line difference) - as one would hope. So I learned something new today "last resort comparison". Thank you again - you are a star :KS!!

---

### Post by vasa1 on 2015-08-06
Hi,

I made the following file "bta.txt":```
bta-mir-126	1033	1133
bta-mir-1260b	378	391
bta-mir-127	178	224
bta-mir-1271	66	103
bta-mir-1277	194	178
bta-mir-128-1	4713	5362
bta-mir-1281	64	34
bta-mir-1282	121	136
bta-mir-128-2	398	506
bta-mir-1284	216	248

```and then I sorted it this way:```
$ LC_ALL=C sort bta.txt
bta-mir-126	1033	1133
bta-mir-1260b	378	391
bta-mir-127	178	224
bta-mir-1271	66	103
bta-mir-1277	194	178
bta-mir-128-1	4713	5362
bta-mir-128-2	398	506
bta-mir-1281	64	34
bta-mir-1282	121	136
bta-mir-1284	216	248

```Is that what you want?

I also pasted the contents of bta.txt into LibreOffice Calc (and gave the cells row headers). Then I sorted by column A:```
A	B	C
bta-mir-126	1033	1133
bta-mir-1260b	378	391
bta-mir-127	178	224
bta-mir-1271	66	103
bta-mir-1277	194	178
bta-mir-128-1	4713	5362
bta-mir-128-2	398	506
bta-mir-1281	64	34
bta-mir-1282	121	136
bta-mir-1284	216	248

```

See:
[http://unix.stackexchange.com/questions/111160/how-to-sort-these-lines](http://unix.stackexchange.com/questions/111160/how-to-sort-these-lines)
[https://askubuntu.com/questions/597924/wrong-behavior-of-sort-command](https://askubuntu.com/questions/597924/wrong-behavior-of-sort-command)
[http://unix.stackexchange.com/questions/43465/whats-the-default-order-of-linux-sort](http://unix.stackexchange.com/questions/43465/whats-the-default-order-of-linux-sort)

---

