---
title: "pc  with 64gb ram after reboot  see only 3gb"
date: 2015-02-06
forum: General Help
---

### Post by faustf on 2015-02-06
hi  guy 
i  have  pc   with  64gb ram i  have  lubuntu 14 installed , it  work  good  but  tomorrow after reboot  , the  pc  see  only  3gb  how  is  possible ???

my test:
1. go in bios  and  it see me  correct 64gb , upgrade bios , remove memory  and  clean ,  but  always  lubuntu see me 3 gb 
2. remove hdd  , and  insert new hdd , install debian , and  debian  see me  correctly  64 gb 

i attach my configuration 
[ATTACH=CONFIG]259768[/ATTACH]

result  of  free -m 

  total       used       free     shared    buffers     cached
Mem:          3184       3016        167         56         83       1255
-/+ buffers/cache:       1677       1506
Swap:         1592         10       1581



i hope  someone  can help  me  

for  the moment  thankz  at all  :)

---

### Post by kpatz on 2015-02-06
Are you running lubuntu 32-bit or 64-bit?  You need 64-bit to access over ~3GB of RAM.

---

### Post by faustf on 2015-02-06
64 bit  ofcourse

i think some  configuration file or  some map memory , but i dont know  where  , is  changed ,  because  with  new hdd  and  fresh debian install  go perfect  and  see me  64gb

---

### Post by gordintoronto on 2015-02-07
Could you post the output of this command: uname -a

---

