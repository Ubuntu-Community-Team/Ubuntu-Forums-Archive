---
title: "Loop in Login screen"
date: 2018-03-11
forum: General Help
---

### Post by caslor2 on 2018-03-11
Hi to all linux - friends

i am using an Ubuntu Flavor  (Xubuntu GUI)  as my major system for the last 1,5 year

until now i hadnt any major problem   but recently i come cross to a major problem

when i boot my pc  and Xubuntu login screen appeared, i placed my password for my account and the xubuntu login screen  after went dark for a second  it appeared again and again.. 

1) i can login as guest session 
2) i tried to boot from an older kernel at boot option but still the same
3) i used  ctrl+alt+F1   or ctrl+alt+F3  to go into shell  and i tried to login in my acount..   and i managed it

but when i  used the     startx  comand...  nothing happened  (xauth: timeout in locking authority file /home/caslor/.xauthority)

when i use my root account and startx  command   then everything going well ... i can login to Xfce GUI 

4) i have deleted the .xauthority  as one solution i found in the Internet suggested  but nothing changed 
5) i removed my nvidia drivers also as an other solution suggested 
6) i removed and re-installed  xfce enviroment...   nothing changed
7) i installed Lubuntu GUi  but had the same results  (cant loging with my acount.. only with  guest session 

any suggestions ?

also i would like to ask something more...   when i am in shell  and want to list something  ( ls -lA) i can see only the last results...  how can i see all the results in the shell ? to scroll up  or see them as pages in order to check all the listed files)



Thanks in advance

---

### Post by again? on 2018-03-12
Login to the ctrl+alt+F1 console as your normal user..
Check permissions of ~/.Xauthority
ls -al ~/.Xauthority

Should be similar but your user name...
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] ls -al ~/.Xauthority**
-rw------- 1 glen glen 52 Mar 13 09:47 /home/glen/.Xauthority
```

---

