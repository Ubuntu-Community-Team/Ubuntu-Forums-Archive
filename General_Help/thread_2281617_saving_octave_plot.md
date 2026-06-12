---
title: "saving octave plot"
date: 2015-06-08
forum: General Help
---

### Post by yasmin2 on 2015-06-08
Hello guys, i am new to octave and i am trying to plot data from a file on my desktop then save this file to a certain directory , now i managed to plot the data file but i tried saving it but failed, here's my code, any help ?

data = load ("/home/yasmin/Desktop/waitingTime.txt");
plot(data(:,1), data(:,2));
saveas(???)

---

### Post by steeldriver on 2015-06-08
The function you're looking for is 'print', I think

```

octave:1> help print
'print' is a function from the file /usr/share/octave/3.8.1/m/plot/util/print.m

 -- Function File: print ()
 -- Function File: print (OPTIONS)
 -- Function File: print (FILENAME, OPTIONS)
 -- Function File: print (H, FILENAME, OPTIONS)
**      Print a plot, or save it to a file.**

```

---

