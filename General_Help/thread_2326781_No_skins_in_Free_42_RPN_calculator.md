---
title: "No skins in Free 42 RPN calculator"
date: 2016-06-04
forum: General Help
---

### Post by Roland_Msl on 2016-06-04
I created the folder .free42 in my user folder

and downloaded from [http://thomasokken.com/free42/](http://thomasokken.com/free42/)

the Linux Ubuntu version
the Skins
the Windows version

I put all the contence of the packed archieves into the folder .free42

When I click on Decimal42, the caclulator starts, but the menu skins shows only a black area, no skins to choose from :confused:.
When I click on Decimal42.exe, the file is opened by WINE and the menu skins works like expected.

---

### Post by howefield on 2016-06-04
What is the operating system that you are using, I tested in 16.04 and the calculator seems to work ok with skins.

---

### Post by Roland_Msl on 2016-06-06
> **howefield said:**
> What is the operating system that you are using, I tested in 16.04 and the calculator seems to work ok with skins.

Also 16.0.4

In my user folder, it's all copied into
.free42

---

### Post by howefield on 2016-06-06
What is the output of 

```
ls -al ~/.free42/
```

---

### Post by Roland_Msl on 2016-06-06
> **howefield said:**
> What is the output of 

```
ls -al ~/.free42/
```


```
hanno@hanno-Aspire-ES1-331:~/internet/cgi.pege.org/cgi-bin$ ls -al ~/.free42/
insgesamt 14724
drwxr-xr-x  2 hanno hanno    4096 Jun  4 19:40 .
drwxr-xr-x 40 hanno hanno    4096 Jun  6 19:16 ..
-rw-r--r--  1 hanno hanno   75804 Jun 15  2013 42ck.gif
-rw-r--r--  1 hanno hanno    3320 Jun 15  2013 42ck.layout
-rw-r--r--  1 hanno hanno   73085 Jun 15  2013 42ct.gif
-rw-r--r--  1 hanno hanno    2382 Jun 15  2013 42ct.layout
-rw-r--r--  1 hanno hanno  108989 Jun 15  2013 Andy480x800.gif
-rw-r--r--  1 hanno hanno    2101 Jun 15  2013 Andy480x800.layout
-rw-r--r--  1 hanno hanno  117915 Jun 15  2013 Ehrling42sl.gif
-rw-r--r--  1 hanno hanno    2242 Jun 15  2013 Ehrling42sl.layout
-rw-r--r--  1 hanno hanno   53393 Jun 15  2013 Ehrling42sm.gif
-rw-r--r--  1 hanno hanno    2185 Jun 15  2013 Ehrling42sm.layout
-rwxrwxr-x  1 hanno hanno 2889408 Apr 18 00:35 free42bin
-rwxr-xr-x  1 hanno hanno 1975296 Apr 17 18:41 Free42Binary.exe
-rwxrwxr-x  1 hanno hanno 4658336 Apr 18 00:35 free42dec
-rwxr-xr-x  1 hanno hanno 4119040 Apr 17 18:41 Free42Decimal.exe
-rw-r--r--  1 hanno hanno   88880 Jun 15  2013 HP-41.gif
-rw-r--r--  1 hanno hanno   20403 Jun 15  2013 HP-41.layout
-rw-r--r--  1 hanno hanno   31190 Jun 15  2013 HP42CY.gif
-rw-r--r--  1 hanno hanno   12851 Jun 15  2013 HP42CY.layout
-rw-r--r--  1 hanno hanno  129227 Jun 15  2013 HP42S.gif
-rw-r--r--  1 hanno hanno    2079 Jun 15  2013 HP42S.layout
-rw-r--r--  1 hanno hanno   60169 Jun 15  2013 kacskin.gif
-rw-r--r--  1 hanno hanno    2220 Jun 15  2013 kacskin.layout
-rw-r--r--  1 hanno hanno   60127 Jun 15  2013 kacskin_yellow.gif
-rw-r--r--  1 hanno hanno    2220 Jun 15  2013 kacskin_yellow.layout
-rw-r--r--  1 hanno hanno   53924 Jun 15  2013 KD0GLS_Compact.gif
-rw-r--r--  1 hanno hanno    2124 Jun 15  2013 KD0GLS_Compact.layout
-rw-r--r--  1 hanno hanno   71900 Jun 15  2013 KD0GLS_Full.gif
-rw-r--r--  1 hanno hanno    2131 Jun 15  2013 KD0GLS_Full.layout
-rw-rw-r--  1 hanno hanno    4799 Mai 30 13:26 keymap
-rw-r--r--  1 hanno hanno   86643 Jun 15  2013 Khor.gif
-rw-r--r--  1 hanno hanno    6001 Jun 15  2013 Khor.layout
-rw-r--r--  1 hanno hanno    7639 Jun 15  2013 KR.gif
-rw-r--r--  1 hanno hanno    1994 Jun 15  2013 KR.layout
-rw-r--r--  1 hanno hanno   87036 Jun 15  2013 Michaels-HP.gif
-rw-r--r--  1 hanno hanno    2117 Jun 15  2013 Michaels-HP.layout
-rw-r--r--  1 hanno hanno   10831 Jun 15  2013 Original.gif
-rw-r--r--  1 hanno hanno    1929 Jun 15  2013 Original.layout
-rw-rw-r--  1 hanno hanno       4 Jun  4 19:54 print
-rw-rw-r--  1 hanno hanno    6312 Apr 18 00:35 README
-rw-r--r--  1 hanno hanno    3752 Jun 15  2013 README.txt
-rw-r--r--  1 hanno hanno    9637 Jun 15  2013 SemiAuto42b.gif
-rw-r--r--  1 hanno hanno    4238 Jun 15  2013 SemiAuto42b.layout
-rw-r--r--  1 hanno hanno    9552 Jun 15  2013 SemiAuto42.gif
-rw-r--r--  1 hanno hanno    4205 Jun 15  2013 SemiAuto42.layout
-rw-r--r--  1 hanno hanno    8050 Jun 15  2013 SemiReal42.gif
-rw-r--r--  1 hanno hanno    1946 Jun 15  2013 SemiReal42.layout
-rw-r--r--  1 hanno hanno   10768 Jun 15  2013 Standard.gif
-rw-r--r--  1 hanno hanno    2063 Jun 15  2013 Standard.layout
-rw-rw-r--  1 hanno hanno    4345 Jun  4 19:54 state
-rw-r--r--  1 hanno hanno   45936 Jun 15  2013 Voyager42.gif
-rw-r--r--  1 hanno hanno    2023 Jun 15  2013 Voyager42.layout
-rw-r--r--  1 hanno hanno   10073 Jun 15  2013 Widgi42.gif
-rw-r--r--  1 hanno hanno    2021 Jun 15  2013 Widgi42.layout
[email]hanno@hanno-Aspire-ES1-331:~/internet/cgi.pege.org/cgi-bin$
```

---

### Post by jordanthompson on 2016-12-11
Having the same problem on Ubuntu 16.10.  The Skins dropdown menu is empty.  I have my gifs and layouts in ~/.free42 with the same permissions listed above.

Any suggestions?   Thanks in advance/

---

### Post by howefield on 2016-12-12
Might be worth asking the question @ [https://groups.google.com/forum/#!forum/free42discuss](https://groups.google.com/forum/#!forum/free42discuss) if you haven't already.

---

