---
title: "Help with sed"
date: 2014-06-25
forum: General Help
---

### Post by abhishek11 on 2014-06-25
I have a text file :
```
1000     10000     (-3,0)     (1,0)    (-0.21259151,-0.17763971)
```

I wish to remove '(' , ',' and ')' so as to get 8 rows of information. I was trying to do this with sed :
```
sed 's/)//'  input.dat > output.dat 
sed 's/(//'  output.dat > output1.dat
sed 's/,/ "\t"/'  output1.dat > output2.dat
  
```
The problem with this only the first instance of the characters specified are getting removed. How do I remedy this ?

---

### Post by abhishek11 on 2014-06-25
[COLOR=#000000][FONT=Arial][FONT=Arial]
sed 's/[(,)]/\t/g' yourfile | column -t > newupdatedfile 


[/FONT]
[/FONT][/COLOR]
is the answer given by 'sat' at [http://stackoverflow.com/questions/24400313/gnuplot-datafile-multiple-separator](http://stackoverflow.com/questions/24400313/gnuplot-datafile-multiple-separator)

---

### Post by Lars Noodén on 2014-06-25
Here are two other resources that are useful for getting started with sed:

[http://www.grymoire.com/Unix/Sed.html#uh-6](http://www.grymoire.com/Unix/Sed.html#uh-6)

[http://www.catonmat.net/blog/sed-one-liners-explained-part-one/](http://www.catonmat.net/blog/sed-one-liners-explained-part-one/)

---

