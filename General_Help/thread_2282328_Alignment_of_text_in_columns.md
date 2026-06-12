---
title: "Alignment of text in columns"
date: 2015-06-13
forum: General Help
---

### Post by vasa1 on 2015-06-13
When I run ls -l I see the output nicely aligned:
```
06:56 PM / $ ls -l
total 104
drwxr-xr-x   2 root root  4096 May 28 06:56 bin
drwxr-xr-x   4 root root  4096 Jun 11 06:08 boot
drwxr-xr-x   2 root root  4096 Nov 14  2014 cdrom
drwxr-xr-x  16 root root  4280 Jun 13 15:13 dev
drwxr-xr-x 128 root root 12288 Jun 13 15:39 etc
drwxr-xr-x   3 root root  4096 Nov 14  2014 home
lrwxrwxrwx   1 root root    33 Jun 11 06:07 initrd.img -> boot/initrd.img-3.13.0-54-generic
lrwxrwxrwx   1 root root    33 May 20 07:01 initrd.img.old -> boot/initrd.img-3.13.0-53-generic
drwxr-xr-x  22 root root  4096 Nov 14  2014 lib
drwxr-xr-x   2 root root  4096 Feb 27 06:58 lib64
drwx------   2 root root 16384 Nov 14  2014 lost+found
drwxr-xr-x   3 root root  4096 Nov 14  2014 media
drwxr-xr-x   2 root root  4096 Apr 11  2014 mnt
drwxr-xr-x   4 root root  4096 Dec  1  2014 opt
dr-xr-xr-x 151 root root     0 Jun 13  2015 proc
drwx------   8 root root  4096 Dec 24 19:05 root
drwxr-xr-x  23 root root   840 Jun 13 15:15 run
drwxr-xr-x   2 root root 12288 May 28 06:55 sbin
drwxr-xr-x   2 root root  4096 Jul 23  2014 srv
dr-xr-xr-x  13 root root     0 Jun 13  2015 sys
drwxrwxrwt   7 root root 12288 Jun 13 18:41 tmp
drwxr-xr-x  10 root root  4096 Jul 23  2014 usr
drwxr-xr-x  13 root root  4096 Jul 23  2014 var
lrwxrwxrwx   1 root root    30 Jun 11 06:07 vmlinuz -> boot/vmlinuz-3.13.0-54-generic
lrwxrwxrwx   1 root root    30 May 20 07:01 vmlinuz.old -> boot/vmlinuz-3.13.0-53-generic
06:58 PM / $ 
```By "nicely aligned", I mean that numbers in the second, fifth, and eighth columns are "right-justified". How is this alignment achieved?

When I use **expand**, each column is left-justified. Here's a sample of what I start with (from a spreadsheet) in which the row contents are separated by single tabs (apparent when the rows are pasted into a text editor):
```
Bill	Flat	Amount (Rs.)
1	05A-001	828
2	05A-002	2,222
24	05B-104	-12,030
25	05B-201	753
26	05B-202	36,008
35	06-003	748
46	06-302	54,383
54	07A-102	55,392
83	07B-401	-10,839
84	07B-402	4,900
86	08-002	10,247
87	08-003	748
88	08-004	2,65,703
154	10B-002	21,839
175	10C-104	-12,017
177	10C-202	796
178	10C-203	3,038
179	10C-204	792
358	10C-104	-12,046
362	10C-204	-3,366
365	10C-303	-11
1366	10C-304	807

```
Here's what I see with **expand**:
```
07:07 PM ~/Desktop $ expand --tabs=14 <expand.txt
Bill          Flat          Amount (Rs.)
1             05A-001       828
2             05A-002       2,222
24            05B-104       -12,030
25            05B-201       753
26            05B-202       36,008
35            06-003        748
46            06-302        54,383
54            07A-102       55,392
83            07B-401       -10,839
84            07B-402       4,900
86            08-002        10,247
87            08-003        748
88            08-004        2,65,703
154           10B-002       21,839
175           10C-104       -12,017
177           10C-202       796
178           10C-203       3,038
179           10C-204       792
358           10C-104       -12,046
362           10C-204       -3,366
365           10C-303       -11
1366          10C-304       807
07:07 PM ~/Desktop $ 

```The third column is left justified.

Is there a way to get the output the way ls -l outputs its contents?

---

### Post by Holger_Gehrke on 2015-06-13
There's probably dozen of ways to do this. Here's one:
```

awk --use-lc-numeric '{printf "%5u %7s %10.3f\n",$1,$2,$3}' expand.txt

```

You might want to change the format specifiers and perhaps add a 'BEGIN' clause to set the separator and output headings ...

---

### Post by vasa1 on 2015-06-13
> **Holger_Gehrke said:**
> There's probably dozen of ways to do this. Here's one:
```

awk --use-lc-numeric '{printf "%5u %7s %10.3f\n",$1,$2,$3}' expand.txt

```

You might want to change the format specifiers and perhaps add a 'BEGIN' clause to set the separator and output headings ...
Thanks for replying :)

Your code is nearly perfect for what I want. The version of **awk** I'm using (**mawk** is default in Lubuntu 14.04) seems to have a problem with with **--use-lc-numeric**.

The first line also needs fixing. I'll play around a bit now that you've pointed me in the right direction.

```
09:53 PM ~/Desktop $ awk --use-lc-numeric '{printf "%5u %7s %10.3f\n",$1,$2,$3}' expand.txt
awk: not an option: --use-lc-numeric
09:53 PM ~/Desktop $ awk '{printf "%5u %7s %10.3f\n",$1,$2,$3}' expand.txt
    0    Flat      0.000
    1 05A-001    828.000
    2 05A-002      2.000
   24 05B-104    -12.000
   25 05B-201    753.000
   26 05B-202     36.000
   35  06-003    748.000
   46  06-302     54.000
   54 07A-102     55.000
   83 07B-401    -10.000
   84 07B-402      4.000
   86  08-002     10.000
   87  08-003    748.000
   88  08-004      2.000
  154 10B-002     21.000
  175 10C-104    -12.000
  177 10C-202    796.000
  178 10C-203      3.000
  179 10C-204    792.000
  358 10C-104    -12.000
  362 10C-204     -3.000
  365 10C-303    -11.000
 1366 10C-304    807.000
09:53 PM ~/Desktop $ 

```

---

### Post by vasa1 on 2015-06-13
```
awk -F"\t" '{ printf "%5s %12s %16s\n",$1,$2,$3 }' expand.txt
```seems to work.
```
11:04 PM ~/Desktop $ awk -F"\t" '{ printf "%5s %12s %16s\n",$1,$2,$3 }' expand.txt
 Bill         Flat     Amount (Rs.)
    1      05A-001              828
    2      05A-002            2,222
   24      05B-104          -1,2030
   25      05B-201              753
   26      05B-202           36,008
   35       06-003              748
   46       06-302           54,383
   54      07A-102           55,392
   83      07B-401          -10,839
   84      07B-402            4,900
   86       08-002           10,247
   87       08-003              748
   88       08-004         2,65,703
  154      10B-002           21,839
  175      10C-104          -12,017
  177      10C-202              796
  178      10C-203            3,038
  179      10C-204              792
  358      10C-104          -12,046
  362      10C-204           -3,366
  365      10C-303              -11
13666      10C-304              807

```

---

