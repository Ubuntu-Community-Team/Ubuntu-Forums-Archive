---
title: "I am already stuck (Installing beryl)"
date: 2006-10-15
forum: General Help
---

### Post by jincast90 on 2006-10-15
Im installing beryl and aiglx for my intel intigrated graphicscard. Im using this guide [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX) and I am already stuck when i get to the place where it says: 

Make sure to get the public key for the repository:

wget [http://ubuntu.beryl-project.org/quinn.key.asc](http://ubuntu.beryl-project.org/quinn.key.asc) -O - | sudo apt-key add -

As far as i know it means I have to add it in synaptic. So I do so. Reaload the packages, and I get an error. What am I doing wrong?

---

### Post by Crooksey on 2006-10-15
Tried running from terminal?

---

### Post by PriceChild on 2006-10-15
Could you please give us the error?

---

### Post by Ramses de Norre on 2006-10-15
You need to execute that line in terminal. 
And to be honest: if you were not able to figure that out, I'd think twice before you start with beryl. You need to know that beryl is software in development and far from stable so you'll almost certainly get into problems at some point.

But if you think you can handle the trouble shooting, go ahead because it is a very nice wm ;)

---

### Post by jincast90 on 2006-10-15
> **Ramses de Norre said:**
> You need to execute that line in terminal. 
And to be honest: if you were not able to figure that out, I'd think twice before you start with beryl. You need to know that beryl is software in development and far from stable so you'll almost certainly get into problems at some point.

But if you think you can handle the trouble shooting, go ahead because it is a very nice wm ;)

Well yo be honest last time I tried and do it all from the terminal it screwed so much up, that I had to reformate. And I would prefer that not too happen so I tried other things.

---

### Post by jincast90 on 2006-10-15
So to get it clear, do I have to ad deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx to my /etc/apt/sources.list save it, close it and then open up the terminal and add this line:
wget [http://ubuntu.beryl-project.org/quinn.key.asc](http://ubuntu.beryl-project.org/quinn.key.asc) -O - | sudo apt-key add -

and then continue from there?

---

### Post by serious7 on 2006-10-15
i kept getting that error earlier today. I just had to add more sources and keep executing the same command till it finally downloaded and installed but now my x-server is f*ed up and can't load into ubuntu anymore lmao.

---

### Post by jincast90 on 2006-10-16
> **serious7 said:**
> i kept getting that error earlier today. I just had to add more sources and keep executing the same command till it finally downloaded and installed but now my x-server is f*ed up and can't load into ubuntu anymore lmao.

Yep that's what happend to me too.. It sux does'nt it?

---

