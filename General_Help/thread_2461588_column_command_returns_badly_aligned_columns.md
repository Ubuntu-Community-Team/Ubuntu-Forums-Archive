---
title: "column command returns badly aligned columns"
date: 2021-05-03
forum: General Help
---

### Post by GwibberFooey on 2021-05-03
I have recently loaded the latest Ubuntu software, which is version 21.04. And now I have problems with the column command in terminal. When I do the following command, then the columns, which should be nicely aligned, are instead severely scrambled. In fact, it is only the rows containing the directory names that are giving problems. 
```
$ pass | column 
```
On the other hand, when I do the following command, then the columns appear to be aligned as they should be. 
```
$ tree ~/.password-store | column
``` 
 
Until very recently I had Ubuntu Mate 18.04, and on that operating system there was no problem with scrambled columns. Likewise, when I run the command ```
pass | column
``` on the Raspberry Pi with Raspbian, there is no problem of scrambled columns.  
 
How to resolve it?

---

### Post by TheFu on 2021-05-05
column -t?

There is a manpage for column with many other options.

---

### Post by GwibberFooey on 2021-05-06
Here are four examples of the output I am getting for various commands. The first three are on Ubuntu 21.04, the last one is on a Raspberry Pi; the last one is equivalent to how ```
pass | column
``` behaved on Ubuntu 18.04. If I can figure out how to get Ubuntu 21.04 to behave like the last example, then I will mark this thread as solved.
```

keW3P@aL9doo:~$ pass | column -t
Password  Store                
&#9500;&#9472;&#9472;       pheeph3Y             
&#9474;         &#9500;&#9472;&#9472;                  kshdkfhal         
&#9474;         &#9500;&#9472;&#9472;                  gjye              
&#9474;         &#9500;&#9472;&#9472;                  Eeghoozoongo1vahde
...
&#9474;         &#9500;&#9472;&#9472;                  fht7c5
&#9500;&#9472;&#9472;       feofohCoi7phij           
&#9474;         &#9500;&#9472;&#9472;                  audaiJiu8ienge
&#9474;         &#9500;&#9472;&#9472;                  Ahpai9ieludae9

keW3P@aL9doo:~$ pass 
Password Store
&#9500;&#9472;&#9472; pheeph3Y
&#9474;   &#9500;&#9472;&#9472; kshdkfhal         
&#9474;   &#9500;&#9472;&#9472; gjye              
&#9474;   &#9500;&#9472;&#9472; Eeghoozoongo1vahde
...
&#9474;   &#9500;&#9472;&#9472; fht7c5
&#9500;&#9472;&#9472; feofohCoi7phij
&#9474;   &#9500;&#9472;&#9472; audaiJiu8ienge
&#9474;   &#9500;&#9472;&#9472; Ahpai9ieludae9

keW3P@aL9doo:~$ pass | column
Password Store                &#9474;   &#9500;&#9472;&#9472; woh8ailig6UWoh1eequi        &#9474;   &#9500;&#9472;&#9472; ahdkfha                &#9474;   &#9500;&#9472;&#9472; hadfhvba
&#9500;&#9472;&#9472; pheeph3Y            &#9474;   &#9492;&#9472;&#9472; le5Oi8c                &#9474;   &#9500;&#9472;&#9472; jlfdsf                &#9474;   &#9500;&#9472;&#9472; hfdkage
&#9474;   &#9500;&#9472;&#9472; kshdkfhal            &#9500;&#9472;&#9472; jafldja            &#9474;   &#9500;&#9472;&#9472; jdfhdahfkdakfhak        &#9474;   &#9500;&#9472;&#9472; dkafjdaljfajds
&#9474;   &#9500;&#9472;&#9472; gjye                &#9474;   &#9500;&#9472;&#9472; Ufagei2wi            &#9500;&#9472;&#9472; xe2eif6ohTh        &#9474;   &#9500;&#9472;&#9472; fht7c5
&#9474;   &#9500;&#9472;&#9472; Eeghoozoongo1vahde        &#9474;   &#9500;&#9472;&#9472; r4f                &#9474;   &#9500;&#9472;&#9472; ii4Aipo7k            &#9500;&#9472;&#9472; feofohCoi7phij
&#9474;   &#9500;&#9472;&#9472; fj5usM                &#9500;&#9472;&#9472; Ang3doye            &#9474;   &#9500;&#9472;&#9472; ji5Na7pa            &#9474;   &#9500;&#9472;&#9472; audaiJiu8iengeuwoyooLa
&#9474;   &#9500;&#9472;&#9472; zoekoch6oSh            &#9474;   &#9500;&#9472;&#9472; Ucoe5xahcah            &#9474;   &#9500;&#9472;&#9472; fhV3F7                &#9474;   &#9500;&#9472;&#9472; Ahpai9ieludae9

pi@raspberrypi:~$ pass | column
Password Store                &#9474;   &#9500;&#9472;&#9472; woh8ailig6UWoh1eequi        &#9474;   &#9500;&#9472;&#9472; ahdkfha                &#9474;   &#9500;&#9472;&#9472; hadfhvba
&#9500;&#9472;&#9472; pheeph3Y                  &#9474;   &#9492;&#9472;&#9472; le5Oi8c                     &#9474;   &#9500;&#9472;&#9472; jlfdsf                 &#9474;   &#9500;&#9472;&#9472; hfdkage
&#9474;   &#9500;&#9472;&#9472; kshdkfhal             &#9500;&#9472;&#9472; jafldja                         &#9474;   &#9500;&#9472;&#9472; jdfhdahfkdakfhak       &#9474;   &#9500;&#9472;&#9472; dkafjdaljfajds
&#9474;   &#9500;&#9472;&#9472; gjye                  &#9474;   &#9500;&#9472;&#9472; Ufagei2wi                   &#9500;&#9472;&#9472; xe2eif6ohTh                &#9474;   &#9500;&#9472;&#9472; fht7c5
&#9474;   &#9500;&#9472;&#9472; Eeghoozoongo1vahde    &#9474;   &#9500;&#9472;&#9472; r4f                         &#9474;   &#9500;&#9472;&#9472; ii4Aipo7k              &#9500;&#9472;&#9472; feofohCoi7phij
&#9474;   &#9500;&#9472;&#9472; fj5usM                &#9500;&#9472;&#9472; Ang3doye                        &#9474;   &#9500;&#9472;&#9472; ji5Na7pa               &#9474;   &#9500;&#9472;&#9472; audaiJiu8iengeuwoyooLa
&#9474;   &#9500;&#9472;&#9472; zoekoch6oSh           &#9474;   &#9500;&#9472;&#9472; Ucoe5xahcah                 &#9474;   &#9500;&#9472;&#9472; fhV3F7                 &#9474;   &#9500;&#9472;&#9472; Ahpai9ieludae9
  

```

---

