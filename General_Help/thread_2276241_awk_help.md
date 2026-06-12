---
title: "awk help"
date: 2015-05-01
forum: General Help
---

### Post by CantankRus on 2015-05-01
I have a file with this info (small section of larger file)....
```
/form 	 div class="observations" 
             div id="summaries" 
             div class="wrapper" 
                 ul 
                             li class="summary" [COLOR="#FF8C00"]id="summary-1"[/COLOR] 
             ul 
                 li class="airT" [COLOR="#FF0000"]18.8[/COLOR] &deg;C /li 
                                 li class="extT" 
                    Lowest  span class="temp" 15.1 &deg;C
                     span class="time" 7:29 am /span                  /span  /li 
                                                 li class="extT" 
                    Highest  span class="temp" 19.4 &deg;C
                     span class="time" 2:11 pm /span                  /span  /li 
                                                     li class="rain" 0 mm  span of rain since 9 am /span  /li 
```

I want to print the [COLOR="#FF0000"]temperature[/COLOR] using awk.

The string [COLOR="#FF8C00"]id="summary-1"[/COLOR] is unique and I found an awk command to print the line I want with...
```
awk '/id="summary-1"/{x = NR + 2}NR == x' file
```
How do I manipulate the command to print just the 3rd field of that line?
Thanks.

---

### Post by Lars Noodén on 2015-05-01
Would that not be like this?

```
 awk '/id="summary-1"/{x = NR + 2}NR == x{ print $3 }'  file
```

I'd use perl's HTML::TokeParser module for that kind of screen scraping myself.

---

### Post by CantankRus on 2015-05-01
> **Lars Noodén said:**
> Would that not be like this?

```
 awk '/id="summary-1"/{x = NR + 2}NR == x{ print $3 }'  file
```

I'd use perl's HTML::TokeParser module for that kind of screen scraping myself.
Ahh, that was easy.
Thanks for the tip but to this  awk[COLOR="#808080"]ward[/COLOR] amateur the only perl I know comes from oysters. :p

---

### Post by Lars Noodén on 2015-05-01
> **CantankRus said:**
> Ahh, that was easy.
Thanks for the tip but to this  awk[COLOR="#808080"]ward[/COLOR] amateur the only perl I know comes from oysters. :p

:)  

awk is just a bunch of if-then statements.  But if (when) you need a bigger text processing hammer, there is perl.  It's pretty easy to pick up because it is so flexible, but since there are around 28,000 mature [CPAN modules](http://www.cpan.org/modules/01modules.index.html) to choose from, finding the ones to help can take time.

---

