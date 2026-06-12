---
title: "Small problem - Power button"
date: 2007-04-05
forum: General Help
---

### Post by SurR3AL on 2007-04-05
hey...
i have this really small but kinda irritating problem.....when i click the power button in ubuntu, it usually shows a new window with options for logout hibernate n stuff.....but for the past week, when i click it, ubuntu just logs out and brings me to the login screen. any way to remedy this?
Thanks :)

---

### Post by adam.tropics on 2007-04-06
Have a look in System-->Preferences-->Power management preferences. In the general tab, there is a setting for 'when power button is presses'. It should say 'Ask Me'.

---

### Post by MrGrey1 on 2007-04-11
> **adam.tropics said:**
> Have a look in System-->Preferences-->Power management preferences. In the general tab, there is a setting for 'when power button is presses'. It should say 'Ask Me'.

I have this problem and the above has not resolved the issue. It still logs me out instead of presenting the shutdown window. It's a real pain because the machine is usually accessed and shutdown via vnc which means I've had to use command line since this started happening a couple of weeks ago. On another note, two other machines freshly installed which don't have this issue... *SIGH*

Edit: can anyone tell me where the power config file is located? This issue, although pretty minor, has to be one of the most irritating I have come across. If the Preferences/Powermanagement options don't alter this behaviour is it a bug?

---

### Post by SurR3AL on 2007-04-13
ok i solved it :)

i went to 'system -> preferences -> sessions' and checked 'ask on logout'
after that everything was normal :D

---

### Post by MrGrey1 on 2007-04-13
It 'fixed itself' on my machine but now that you mention it I do remember changing that setting. YAY! New it was something simple I was over looking. 
:D

---

### Post by SurR3AL on 2007-04-14
hehe....glad i could refresh ur memory :P

---

