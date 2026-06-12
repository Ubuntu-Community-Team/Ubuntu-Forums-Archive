---
title: "I wanna install the gcc and java compilers..."
date: 2006-07-04
forum: General Help
---

### Post by cobbweb on 2006-07-04
Hey, 
 
 I am taking a computer programing course and would like to install the gcc (i think thats it for c++ and c) and java compilers . I heard you could use somethign like sudo install essentials or somthing like that for everything. Does anyone know the command for that? Thanks,
   Also, 
 
 I just installed Dapper don't have any IDE's I like bluefish and also a cool program called ajura (or somthing simular to that, i can't seem to remember the name but i really loved that program) does anyone know how to install these programs or where i can get them. Thanks , 

 Cobbweb

---

### Post by aysiu on 2006-07-04
The command is ```
sudo aptitude update
sudo aptitude install build-essential
``` Some people think *build-essential* is a security risk, but they generally tend to say that in only theoretical discussions and never actually mention it in threads where users ask to install it. I don't see what the big deal is since every other major Linux distribution includes tools for compiling.

For Bluefish, you'll need to [enable extra repositories](http://www.psychocats.net/ubuntu/sources). Then you can ```
sudo aptitude update
sudo aptitude install bluefish
``` Ajura, however, does not appear to be in the repositories. I can't find it in a Google search, either. Do you have a link to the project's webpage?

---

### Post by meng on 2006-07-04
For the IDEs, try
```
sudo aptitude install bluefish
sudo aptitiude install amaya
```

---

### Post by cobbweb on 2006-07-04
I can't find amaya afer i didn't the install. Amaya sounds very simular so I think that my just be the IDE I was thinking of. I would also like to install the javac thingy compiler. What is the command to install the java compiler?? 
 thanks for all the help guys, 

 Cobbweb

---

### Post by aysiu on 2006-07-04
So you did install Amaya? What happens if you press Alt-F2 and type ```
amaya
```?

---

### Post by cobbweb on 2006-07-04
humm ok this is weird, 

 I am on a MacBook using Parallel and when push alt f2 the apple bar shows up. Wierd... i tried typing amaya in the terminal and I puts a site done in java up. However I don't belive this was the program that I was thinking of. I think i installed it last time off of automatix, however i installed automatix and when i type my password it it gets stuck trying to find some key or somthing and doesnt do anything. 

 Cobbweb

---

### Post by cobbweb on 2006-07-04
ok the program i want is called 

Anjuta

---

### Post by aysiu on 2006-07-04
[QUOTE=cobbweb]ok the program i want is called 

Anjuta[/QUOTE]
It's also in the repositories along with Bluefish: ```
sudo aptitude update
sudo aptitude install anjuta
```

---

### Post by meng on 2006-07-04
Sorry to lead you astray. anjuta, amaya, you can see why I got confused.

---

