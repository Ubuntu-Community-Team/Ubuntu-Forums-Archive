---
title: "Screen turns off every 30 seconds of idle activity on Ubuntu 22.04.1 LTS"
date: 2022-11-19
forum: General Help
---

### Post by Agnishom_Chattopadhyay on 2022-11-19
My screen turns off every 30 seconds of idleness. My power settings is set differently, but it doesn't help.

---

### Post by nickdc on 2022-11-21
As a workaround, have you tried caffeine? [https://www.imaginelinux.com/caffeine-for-ubuntu/](https://www.imaginelinux.com/caffeine-for-ubuntu/)   If you put caffeine indicator in with your startup applications, it will put an icon in your panel that you can use to toggle the screen cut-out on and off. Leave it on and you can return hours later and the screen will be just as you left it.

---

### Post by Agnishom_Chattopadhyay on 2022-11-21
This is a good idea, but I do like the feature of the screen turning off. 30 seconds is too little time, however. I want my screen to turn off every 5 minutes

---

### Post by Agnishom_Chattopadhyay on 2022-11-23
Any suggestions? Any component I should reinstall or any config file I can tweak so that I can get "normal" behavior?

---

### Post by tea for one on 2022-11-23
Try:-
Automatic Suspend = Off
Power Button Behaviour = Power Off

---

### Post by Agnishom_Chattopadhyay on 2022-11-26
Wow, that seems to have worked! How did you guess such a bizzare solution?

---

### Post by tea for one on 2022-11-26
Not really a guess, these are the default settings when I installed Ubuntu 22.04.
I've never had any reason to fiddle about with the power options.
Anyway, if you are satisfied with the result and to help other forum members/searchers, it is a nice gesture to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Agnishom_Chattopadhyay on 2022-11-26
I still do not know why this works, but oh well. 

Have a nice weekend, anyway.

---

