---
title: "Problem in Player/Stage while running 3 iRobots (Roomba)"
date: 2013-09-03
forum: General Help
---

### Post by mitali2 on 2013-09-03
Hi,
I am working on a player/stage project which currently has 3 (Later it will be extended to 6) iRobots -Roomba. 
As suggested in Jenny Owen's Tutorial on player/stage [http://www-users.cs.york.ac.uk/~jowen/player/playerstage-tutorial-manual.pdf](http://www-users.cs.york.ac.uk/~jowen/player/playerstage-tutorial-manual.pdf) , I was  giving different port numbers to each one of the robots.

Here is my .cfg file : 

driver
(   
  name "stage"
  provides [ "simulation:0"]
  plugin "stageplugin"
  worldfile "pacman.world"  
)


driver
( 
  name "stage"
  provides [ "6665:position2d:0" ]
  model "pacman" 
)




driver
( 
  name "stage"
  provides ["6666:position2d:0" ]
  model "ghost1" 
)


driver
( 
  name "stage"
  provides ["6667:position2d:0" ]
  model "ghost1" 
)


But, I am getting this error when I am running ./ghost1 and ./ghost2 :

**playerc error : got NACK from request**

The simulator is not able to run the other two robots, I guess.

Kindly help me in this regard.

---

### Post by cariboo on 2013-09-03
This isn't a beginner question, moved to General Help

---

### Post by mitali2 on 2013-09-03
Hi,
I am working on a player/stage project which currently has 3 (Later it will be extended to 6) iRobots -Roomba. 
As suggested in Jenny Owen's Tutorial on player/stage [http://www-users.cs.york.ac.uk/~jowe...ial-manual.pdf](http://www-users.cs.york.ac.uk/~jowe...ial-manual.pdf) , I was giving different port numbers to each one of the robots.


Here is my .cfg file : 


driver
( 
name "stage"
provides [ "simulation:0"]
plugin "stageplugin"
worldfile "pacman.world" 
)




driver
( 
name "stage"
provides [ "6665:position2d:0" ]
model "pacman" 
)








driver
( 
name "stage"
provides ["6666:position2d:0" ]
model "ghost1" 
)




driver
( 
name "stage"
provides ["6667:position2d:0" ]
model "ghost1" 
)




But, I am getting this error when I am running ./ghost1 and ./ghost2 :


playerc error : got NACK from request


The simulator is not able to run the other two robots, I guess.


Kindly help me in this regard.

---

### Post by mitali2 on 2013-09-03
Thanks for moving it.

---

### Post by QIII on 2013-09-03
Merged threads...

I see you figured out that it had already been moved.  ;)

---

