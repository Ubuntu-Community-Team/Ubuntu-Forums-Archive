---
title: "New to AWK, trying to process a schedule!"
date: 2018-01-14
forum: General Help
---

### Post by ben1836 on 2018-01-14
Hello everyone, I'm trying to process a large text file that is reliably formatted to pull out the information I need quickly. 


I'm brand new to this, really hoping for a lot of help in getting this worked out. I know I'm asking a lot!


I want to process this file as input and output to a new file.


So it's a schedule and I'm trying to pull out beginning and end times. Each three number group has a beginning and end time.
When a group of three numbers is alone (surrounded by whitespace) then I need it's beginning and end time.
When multiple groups of three numbers are together without whitespace, I only need the begginning time from the first group, and the end time of the last group.






The following text is an example of the formatting


```



  31  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28  1  2  3  4  5  6  7
  WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE
          889786         564889      986234386      937639         497208      208763                        BLK NO.  956 DYS OFF  17
  X  X  X ABCABC X  X  X ABCABC :  : ABCABCABC X  X ABCABC X  X  X ABCABC :  : ABCABC X  X                   CRD.   20.98 BLK.  37.64
  889= 0620/1640/0620; 786= 1150/2202/0802; 564= 0715/1640/0402; 986= 0638/1848/0587; 234= 1134/1818/0673;   TAFB  694.27 C/O    17.92
  386= 1319/2059/0487; 937= 0728/1324/0674; 639= 1023/2300/0785; 497= 0700/1608/0563; 208= 0902/1957/0643;
  763= 0758/1943/0896;                                                                                    




  31  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28  1  2  3  4  5  6  7
  WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE TH FR SA SU MO TU WE
                   593            304                  609               499            375                  BLK NO.  816 DYS OFF  17
  X  X  X  :  :  X ABCABCABC X  : ABCABCABC X  X  X  : ABCABCABC X  X  X ABCABCABC X  X ABCABCABC            CRD.   93.24 BLK.  29.45
  593= 1405/2003/0745; 304= 1600/2000/1643; 609= 1107/2301/7583; 499= 1306/2214/7491; 375= 0518/1003/8574;   TAFB  454.54 C/O    1.09



```
So reading this, looking at line 4 "          889786         " the start and end times are on line 6.
The information I'm looking for is that the start time for 889 = 0620 and the end time for 786 = 2202
Looking at line 13 "                   593            " the start and end times are on line 15.
For this, since it's a lone group of three numbers - I would need both the beginning and end of this group.
So, 593 starts at 1405 and ends at 2003.


IDEALLY, the output would look like this:
```
BLK NO.  956 DYS OFF  17
0620/2202
0715/1640
0638/2059
0728/2300
0700/1957
0902/1943




BLK NO.  816 DYS OFF  17
1405/2003
1600/2000
1107/2301
1306/2214
0518/1003
```

---

### Post by QIII on 2018-01-14
Hello!

What instruction have you received up to now?

What are the results of the work you have done to this point?

---

### Post by ben1836 on 2018-01-14
everything I've done so far has been processing the original schedule up until this point, which was basically stripping out irrelevant content then reordering everything in a reliable format. 

I don't know what i'm doing so i'm just reading around and going one little step at a time. 

So, beyond this point I haven't gotten anywhere. 


I'm currently reading through the awk man and tutorials online trying to get a feel for it. 

My plan doing it myself is to basically take the long road to get the final product and take it step by step - probably in the least efficient route possible haha. 
But honestly at this point i'm so unfamiliar with the tools that I'm not even sure what the next would be - reading more but it's slow going. 


I was hoping that someone far smarter and experienced than myself would be able to look at this and say, "oh, easy - here's how, or here's the general idea, or here's the tools to do that."

---

### Post by QIII on 2018-01-14
Can you provide the text of what you have attempted up to thus point?  That might provide a jumping off point for those who would like to help you move forward.

---

### Post by ben1836 on 2018-01-14
sure, here it what got the schedule from its original form into what i have now. 

```
awk 'BEGIN { RS="---" } /DYS OFF  27/ { sub("---.*","") ; print $0 }' /home/user/file > /home/user/file_sorted ; awk 'BEGIN { RS="---" } /DYS OFF  26/ { sub("---.*","") ; print $0 }'  /home/user/file >> /home/user/file_sorted ; ###rinse and repeat
```

---

