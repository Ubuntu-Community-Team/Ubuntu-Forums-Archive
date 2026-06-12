---
title: "g++ linking error"
date: 2007-05-20
forum: General Help
---

### Post by katzman on 2007-05-20
Hi guys;
not sure where i should have posted this so I ahve done so here.
I ahve been writing my first program in c (an interface between lcdproc and mpd).
I started writing this in just plain text files but swtiched to kdevelop to have make files and the lijke.
This worked great for a while until a error started copping up about undefined refrences.
Basiucally the make command genereates a set of .o files and then when it tries to link these it gives undefined reference errors for all the functions not in the main source file.
I should add that this project is a main c++ file which uses some c headers (some stock one by me)
if i run the command
g++ *.c *.cpp -lmpd -o lcdmpd
 (-lmpd to use the the libmpd libraries)
i get a nice binary which runs just fine..so the code seems to be okay.
Anyone have any idea what is going one cause it is driving me nuts

I have attached the spource package kdevelop gives me

---

