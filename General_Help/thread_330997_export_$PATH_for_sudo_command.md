---
title: "export $PATH for sudo command"
date: 2007-01-03
forum: General Help
---

### Post by jae1227 on 2007-01-03
I installed the JDK from Sun so I now have it in my $PATH. But if i type 
```
sudo java
```
It runs the GJC or what ever it it called, the GCC version of Java no the JDK form Sun. I edited my .bashrc so that every time I logon the export command is executed. Anyways how can I do this for root so if I type 
```
sudo java
```
it will run the JDK fromSun

---

### Post by bodhi.zazen on 2007-01-04
I am not following on the JAVA stuff ....

but ....

Try editing /root/.bashrc similar to ~/.bashrc

HTH

---

### Post by taurus on 2007-01-04
```
update-alternatives  --configure java
```

---

### Post by NoNo_231 on 2007-01-04
Another alternative is to use galternatives. 

sudo aptitude install galternatives

and then from a terminal 

sudo galternatives

You will see where your alternatives are pointed and you can change them.

---

