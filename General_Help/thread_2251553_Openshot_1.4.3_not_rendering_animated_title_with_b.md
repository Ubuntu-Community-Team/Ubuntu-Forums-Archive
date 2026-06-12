---
title: "Openshot 1.4.3 not rendering animated title with blender"
date: 2014-11-04
forum: General Help
---

### Post by monkeyinastripedsh on 2014-11-04
Hi If I did something wrong please tell me.

I recently installed openshot and started using it I want to create an animated title, however when I started to create the title it came up with a message saying that the path that it takes to run blender is incorrect. I then immediately open up a browser and Google it I have followed all of their instructions and still nothing. This should have been fixed a long time ago and for a while it apparently it was but now it seems to not work again. most of the solutions that I have done are unnecessary due to the fact that it has been fixed however I tried them anyway.

No luck If there is a way to fix this please do tell!

I am on Ubuntu 14.4

---

### Post by monkeyinastripedsh on 2014-11-05
Anyone? Come on this forum has to have SOMEONE who can help me.
Just tell me that I am an idiot and help me please. this is rather frustrating. Usually I get some sort of reply helpful or not.

---

### Post by JoeDaddy on 2015-01-03
Found this on another site and it worked for me.  Very simple solution! "I'm using Ubuntu 14.04.1 and needed to change the location of blender  from the default of 'blender' to '/usr/bin/blender' since this is the  path used to access blender.  **From a terminal screen type 'which  blender' (omitting quotes)** will display the path to the blender  executable.**  Enter the** **entire output line including the / at the  beginning into the Blender location line of preferences.**" Thanks to [rdgreenlaw (rgreenlaw)]("https://launchpad.net/%7Ergreenlaw") at [https://answers.launchpad.net/openshot/+question/249837](https://answers.launchpad.net/openshot/+question/249837)

---

