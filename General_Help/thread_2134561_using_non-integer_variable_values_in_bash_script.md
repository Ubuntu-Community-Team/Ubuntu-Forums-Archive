---
title: "using non-integer variable values in bash script"
date: 2013-04-11
forum: General Help
---

### Post by telemaster on 2013-04-11
So, I have a fairly simple bash script whose function is to make automated input files for another program.
The only complication arises because of the need for non-integer variables. 
Here is the script

```

#!/bin/bash
for i in 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40; do
mkdir $i
evenshrink=$(( $i / 2 ))
cd $i
cat > interstitial.d12<< !
**PROGRAM**
$evenshrink $evenshrink (**only relevant line of program**)
#!/bin/bash


for j in 5 7 9 11 13 15 17 19 21 23 25 27 29 31 33 35 37 39; do
mkdir $j
oddshrink=$(( $j / 2 ))|bc -l
cd $j
cat > interstitial.d12<< !
**SAME PROGRAM**
$oddshrink $oddshrink (**only line different in second case**)

```

As you can see I use the "-bc -l" command that I just recently looked up, in order to instruct bash to process decimals.
Unfortunately, instead of printing $oddshrink, I just get blank spaces where they should occur!
Anyone know what else I'm missing?

Many thanks, telemaster

---

### Post by steeldriver on 2013-04-11
The idea is that bc should actually perform the floating point arithmetic - doing integer arithmetic like $(( $j / 2 )) in the shell and then passing the result to bc after won't work afaik - try something like

```
oddshrink=$(echo "scale=2; $j/2" | bc)
```

e.g.

```
$ for j in {5..39..2}; do oddshrink=$(echo "scale=2; $j/2" | bc); echo $oddshrink; done
2.50
3.50
4.50
5.50
6.50
7.50
8.50
9.50
10.50
11.50
12.50
13.50
14.50
15.50
16.50
17.50
18.50
19.50
```

---

### Post by Vaphell on 2013-04-11
if you really wanted to stay with bash you could also multiply j by 5, 50, 500 depending on the desired precision and put dot by hand. 

```
$ for j in 5 13; do t=$((j*10/2)); echo "$j/2 = ${t%?}.${t:0-1}"; done
5/2 = 2.5
13/2 = 6.5
$ for j in 5 13; do t=$((j*1000/2)); echo "$j/2 = ${t%???}.${t:0-3}"; done
5/2 = 2.500
13/2 = 6.500
```


${t%?} = trim ? pattern from the right. ? stands for single character
${t:0-n} = last n characters

edit: this method appears to be 100x faster than the *echo | bc* approach :o

---

