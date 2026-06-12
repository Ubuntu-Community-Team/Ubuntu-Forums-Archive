---
title: "Installing Garfield"
date: 2014-05-31
forum: General Help
---

### Post by vishesh2 on 2014-05-31
[COLOR=#000000]I tried to install garfield, ubuntu 14.04 (64bit)

I followed the steps given here in this link:[/COLOR]
[http://ubuntuforums.org/showthread.p...6#post10195676]("http://ubuntuforums.org/showthread.php?p=10195676#post10195676")[COLOR=#000000]

[/COLOR]
but when i tried [COLOR=#000000]make garfield-9 it gave me the following error:
[/COLOR]
fcasplit garfield-9.f
 FCASPLIT executing.
             Input file : garfield-9.f
           Shell script : garfield-9.shfca
              Make file : garfield-9.mkfca
        Fortran    name : gfortran  
        Fortran options : -c -g -O2 -fno-automatic  
             CC    name : gcc  
             CC options : -c -g -O2  
      Assembler    name : as  
      Assembler options :   
 106986 lines written for   460 decks
     27 trailing comment lines ignored.
fcasplit garfadd-9.f
 FCASPLIT executing.
             Input file : garfadd-9.f
           Shell script : garfadd-9.shfca
              Make file : garfadd-9.mkfca
        Fortran    name : gfortran  
        Fortran options : -c -g -O2 -fno-automatic  
             CC    name : gcc  
             CC options : -c -g -O2  
      Assembler    name : as  
      Assembler options :   
At line 786 of file /build/buildd/cernlib-20061220+dfsg3/src/patchy/fcasplit.F (unit = 11, file = '')
Fortran runtime error: File 'garfadd-9.f' does not exist
make: *** [main-9.f] Error 2

How to fix this?
Please help me, anyone?

---

### Post by ivan51 on 2014-08-29
Did you try [this recipe]("http://ubuntuforums.org/showthread.php?t=1636834&p=11976536#post11976536")?

---

### Post by ivan51 on 2014-08-29
I also try to install Garfield to my laptop (Ubuntu 14.04 LTS 64bit), and have an error in *make.*  Here my console output:
```

john@john-Vostro-1015:~/soft/garfield$ make garfield-9
rm *.f *.o
rm: cannot remove &#8216;*.f&#8217;: No such file or directory
rm: cannot remove &#8216;*.o&#8217;: No such file or directory
make: [garfield-9.f] Error 1 (ignored)
./patchy_step garfield-9


Nypatchy executing with files / options


1 PAM -
2 FORT garfield-9.f
3 read garfield-9.cra
4 print tty
5 CC -
6 AS -
7 DATA -
8 FO:2 -
9 CC:2 -
10 AS:2 -
11 DA:2 -

Version: PATCHY 5.05 /3 1996/06/29 17.00 .RJP, today: 14/08/29 16.52


1 + +EXE.
2 + +USE,CERN.
3 + +USE,*LINUX.
4 + +USE,MANYWIRE.
5 - * +USE,BIGMAP.
6 + +USE,HUGEMAP.
7 + +USE,LONGLIST.
8 + +USE,*GARFIELD.
9 + +USE,*MAGGARF.
10 + +USE,*HEEDGARF.
11 + +USE,P=PROJECTION,D=PLABEM,T=I.
12 + +USE,P=PROJECTION,D=PLAEQU,T=I.
13 + +USE,P=PROJECTION,D=PLAOVL,T=I.
14 + +USE,P=PROJECTION,D=PLATRC,T=I.
15 + +USE,P=PROJECTION,D=PLAEXP,T=I.
16 + +USE,P=PROJECTION,D=PLAEXC,T=I.
17 + +USE,P=PROJECTION,D=PLAEXD,T=I.
18 + +USE,P=PROJECTION,D=PLAEXI,T=I.
19 + +USE,P=PROJECTION,D=PLAEXE,T=I.
20 + +USE,P=NEBEM,T=I.
21 + +USE,P=CELL,D=CELBEM,T=I.
22 + +USE,P=CELL,D=CELSEL,T=I.
23 + +USE,P=CELL,D=CELSOL,T=I.
24 + +USE,P=CELL,D=CELSPR,T=I.
25 + +USE,P=CELL,D=CELSCT,T=I.
26 + +USE,P=CELL,D=MAPC4,T=I.
27 + +USE,P=CELL,D=MAPC5,T=I.
28 + +USE,P=CELL,D=MAPFM8,T=I.
29 + +USE,P=CELL,D=MAPFM9,T=I.
30 + +USE,P=GAS,D=GASMRG,T=I.
31 + +USE,P=FIELDCAL,D=EFIELD,T=I.
32 + +USE,P=FIELDCAL,D=EMCC10,T=I.
33 + +USE,P=MAGBOL7,D=MONTEFD,T=I.
34 + +USE,P=MAGBOL7,D=DLCMIC,T=I.
35 + +USE,P=MAGINTER,D=GASBMC,T=I.
36 + +USE,P=MAGINTER,D=GASIDE,T=I.
37 + +USE,P=MAGINTER,D=GASIDI,T=I.
38 + +USE,P=MAGINTER,D=GASIDO,T=I.
39 + +USE,P=MAGINTER,D=GASLEX,T=I.
40 + +USE,P=MAGINTER,D=GASEXU,T=I.
41 + +USE,P=MAGINTER,D=OUTEI7,T=I.
42 + +USE,P=MAGBOL7,D=DLCMIC,T=I.
43 + +USE,P=FIELDCAL,D=EFIELD,T=I.
44 + +USE,P=FIELDCAL,D=EFCFMP,T=I.
45 + +USE,P=DRIFTCAL,D=DLCEX1,T=I.
46 + +USE,P=DRIFTCAL,D=DLCIO1,T=I.
47 + +USE,P=DRIFTCAL,D=INTEXC,T=I.
48 + +USE,P=DRIFTCAL,D=ERFIR,T=I.
49 + +USE,P=DRIFTCAL,D=DLCCAL,T=I.
50 + +USE,P=DRIFTCAL,D=DLCSTA,T=I.
51 + +USE,P=DRIFTCAL,D=DLCWIR,T=I.
52 + +USE,P=DRIFTCAL,D=DLCWIM,T=I.
53 + +USE,P=DRIFTCAL,D=DLCEX1,T=I.
54 + +USE,P=DRIFTCAL,D=DLCSOL,T=I.
55 + +USE,P=DRIFTCAL,D=DLCVAC,T=I.
56 + +USE,P=DRIFTCAL,D=DLCVFU,T=I.
57 + +USE,P=SIGNAL,D=IONFMP,T=I.
58 + +USE,P=SIGNAL,D=SIGADD,T=I.
59 + +USE,P=SIGNAL,D=SIGADS,T=I.
60 + +USE,P=SIGNAL,D=SIGADM,T=I.
61 + +USE,P=SIGNAL,D=SIGFLS,T=I.
62 + +USE,P=SIGNAL,D=SIGWRT,T=I.
63 + +USE,P=SRIMREAD,T=I.
64 + +USE,P=GRAPHICS,D=GRTXHIGZ,T=I.


65 + +PAM,LUN=11,T=a,C. garfield-7.car


---> start reading file garfield-7.car


Read Pam file: GARFIELD 7.45 /00 110314 00.00




****!!!!! Patchy is crashing !!!!!****
please call for help: [EMAIL="zoll@cern.ch"]zoll@cern.ch[/EMAIL]


Bank chaining clobbered at name adr 784


Division 1 boundaries: 95 903


After:


180 KEEP LI/NL/NS/ND= 1 3 2 4, links: 171 0 99902
Z=QFVERS
st: .......1. 0 .. AU ....
with 1 lines at JSLA 1


189 KEEP LI/NL/NS/ND= 1 3 2 4, links: 180 0 99902
Z=QFVSNUM
st: .......1. 0 .. AU ....
with 1 lines at JSLA 1


198 KEEP LI/NL/NS/ND= 1 3 2 4, links: 189 0 99902
Z=QFVPRIM
st: .......1. 0 .. AU ....
with 1 lines at JSLA 1


207 KEEP LI/NL/NS/ND= 1 3 2 4, links: 198 0 99902
Z=QFVSEC
st: .......1. 0 .. AU ....
with 1 lines at JSLA 1


the memory is destroyed, dump the next few words:


212 : 2041C6 2113990
213 : 1863E 99902
214 : 0 0
215 : 1863E 99902
216 : 0 0
217 : E1 225
218 : C001030 201330736
219 : 1 1
220 : 1 1
221 : 0 0
222 : F 15
223 : 1863E 99902
224 : 0 0
225 : E1 225
226 : C001030 201330736
227 : 1 1
228 : 1 1
229 : 0 0
230 : F 15
231 : 1863E 99902
232 : 0 0
233 : E1 225
234 : C001030 201330736
235 : 1 1
236 : 1 1
237 : 0 0
238 : F 15
239 : 86202 549378


The first good bank after, starting at adr 239 is:


244 DECK LI/NL/NS/ND= 0 4 3 1, links: 251 0 0 99233
D=CELBEM


Division 2 boundaries: 62072 62197


Division 3 boundaries: 98730 99997


***!!! Kill the run for: fatal !!!***
make: *** [garfield-9.f] Error 2

```
Do someone know why this error appear?

---

### Post by uRock on 2014-08-29
Hello and welcome to the forums!

Please use code tags for terminal outputs. [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

Cheers & Beers,
uRock

---

### Post by eshan2 on 2014-11-15
Hi,
I am also facing the same problem. Could you find any solution? Please help.
Thanks!

---

