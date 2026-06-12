---
title: "HOW TO UPGRADE mesa3.0 to mesa 3.3 in   UBUNTU 12.04"
date: 2014-12-19
forum: General Help
---

### Post by baapek on 2014-12-19
I am using 12.04 /  I know about 14.04.I want to stick to 12.04 for while.

Here on << glxinfo  >> command  I get  mesa version 3.0/2.1.
I am looking to upgrade this mesa version to 3.3 or more
As the continuous streaming is not happening from IP Camera in 12.04 
which I am expecting in by changing to mesa 3.3 version.(Because OPENGL support failed is the prompt while streaming)

Kindly suggest me method/command........how to upgrade mesa to future version


THANK YOU

---

### Post by monkeybrain20122 on 2014-12-19
You mean opengl 3.3, mesa is at version 8.04 for Precise, current stable version is 10.3 (Utopic) and developmental version is 10.5.Whether you can run OpenGL 3.3 would depend on your actual graphic card in addition to how update your mesa is. 

For 12.04 you can get mesa 10.3 from [https://launchpad.net/~pali/+archive/ubuntu/graphics-drivers-stable](https://launchpad.net/~pali/+archive/ubuntu/graphics-drivers-stable)  and the latest and greatest (10.5) from [https://launchpad.net/~pali/+archive/ubuntu/graphics-drivers](https://launchpad.net/~pali/+archive/ubuntu/graphics-drivers)

But it can be risky to update your graphic stack, you should install ppa-purge to downgrade the packages in case something goes wrong, and back up/clone your install in case things get really wrong so that you can't even run ppa-purge

I suggest you add the repository with synaptic (sudo apt-get install synaptic) and disable the repository once things are working instead of keep updating with it.
  
P.S. This is a support question, I think thread shouldn't be here.

---

### Post by coffeecat on 2014-12-19
Not an Ubuntu, Linux and OS **Chat** question.

*Thread moved to **General Help**.*

---

