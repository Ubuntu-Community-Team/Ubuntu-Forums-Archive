---
title: "Convert Writter ASCII file to a CSV file ."
date: 2018-10-27
forum: General Help
---

### Post by eightbits2010 on 2018-10-27
I need to add a ASCII file (LibreOffice writer) to a LibreOffice Calc file?
The text file is just a copied text file in LibreOffice Writter            
 
The file has this format :
 8 WAKA - CBS
2 WCOV - FOX
10 WDIQ - PBS
4 WNCF - ABC
1004 WNCF - ABC
11 WSFA - NBC
1012 WSFA - NBC
24 A&E

This I think should be a space delimited file (?).


All I want to do is import the ASCII file into LibreOffice Calc so I can sort it for print out.
I have done this once before but now I can't seem to get it.
I searched youtube but the tutorials did not help. Also the LibreOffice help didn't do it either.
I am sure it is something stupid but just can't seem to get it right.
I thought if I could get the ASCII file to a CSV file but I don't see how to do that either.

Using Ubuntu 16.04 and LibreOffice Version: 5.4.6.2

---

### Post by HermanAB on 2018-10-28
Simply save it as a text file and then open it with Calc.  You should not need to do anything special.

---

### Post by The Cog on 2018-10-28
In your text editor, choose Select All and Copy (Ctrl-A Ctrl-C in Write). Then in a new Calc spreadsheet, right-click a cell and select Paste Special > Unformatted Text. Up pops a text import wizard where you can choose space separated.
P.S. HermanAB is right: Calc also pops up the same wizard if you simply open a text file.

But if you have saved it as a plain text file (not a .odt document) then there are tools for sorting. For instance, I saved your example text as z.txt. Now I can sort on the second field with the command "sort -k 2 z.txt" (-k 2 says use the second field as the sort key).```
steve@Steves-lappy:~/test$ sort -k2 z.txt 
24 A&E
8 WAKA - CBS
2 WCOV - FOX
10 WDIQ - PBS
1004 WNCF - ABC
4 WNCF - ABC
1012 WSFA - NBC
11 WSFA - NBC

```
To sort numerically (key 1) you need to tell it to use general numbering, or it would sort textually, putting 1004 before 11. You can also make nice spacing if you want by passing the output through column, and you probably want to write the output to another file (z2):```
steve@Steves-lappy:~/test$ sort -gk1 z.txt | column -t > z2.txt
steve@Steves-lappy:~/test$ cat z2.txt
8     WAKA  -  CBS
2     WCOV  -  FOX
4     WNCF  -  ABC
10    WDIQ  -  PBS
11    WSFA  -  NBC
24    A&E
1004  WNCF  -  ABC
1012  WSFA  -  NBC

```
Of course, if you want the resuilt in a spreadsheet then the copy/paste above is easiest.

---

### Post by eightbits2010 on 2018-10-28
Thanks for the responces. I will try the HermanAB soulution first and them try The Cog next.
I can reply with the results either way.

---

### Post by eightbits2010 on 2018-10-28
Changing the file to a file.txt did the trick. The only problem I had was the sort stopped at a empty row (no contents) and I had to scratch
my head a little bit, and eventually I got it right.
Now, if I can just find the 'solved' input.

---

### Post by The Cog on 2018-10-29
> **eightbits2010 said:**
> Now, if I can just find the 'solved' input.
It's under the Thread Tools pull-down at the top-right of the page.

---

### Post by him610 on 2018-10-29
+++
Thanks to all three of you - eightbits2010, who asked the question, HermanAB and The Cog who both contributed to the answer. 
I have had the same problem before, just never thought to ask.
This one will definitely go into my bag of tricks.

---

