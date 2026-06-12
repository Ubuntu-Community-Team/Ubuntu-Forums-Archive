---
title: "Can an X program be started from another terminal ?"
date: 2008-04-27
forum: General Help
---

### Post by akudewan on 2008-04-27
Pressing Ctrl+Alt+Fn takes me to another terminal. Is it possible to start a program in my current X session using this terminal ?

This would come in handy to me if compiz or emerald hang, since many times, I can't even run any program directly.

---

### Post by bodhi.zazen on 2008-04-27
yes, it should work just fine. You can test with 

```
xeyes
```

---

### Post by bingoUV on 2008-04-27
> **akudewan said:**
> Pressing Ctrl+Alt+Fn takes me to another terminal. Is it possible to start a program in my current X session using this terminal ?

This would come in handy to me if compiz or emerald hang, since many times, I can't even run any program directly.

 You will have to set the environment variable DISPLAY, to mostly :0.0 but it might be different. Try the following from a graphical terminal emulator inside your X session to know what is its value :  ```
 echo $DISPLAY 
```  Now go to a text terminal by ctrl - alt - Fn  ```
 export DISPLAY=:0.0 
xterm & 
```  (assuming :0.0)

---

### Post by akudewan on 2008-05-01
> **bingoUV said:**
> You will have to set the environment variable DISPLAY, to mostly :0.0 but it might be different. Try the following from a graphical terminal emulator inside your X session to know what is its value :  ```
 echo $DISPLAY 
```  Now go to a text terminal by ctrl - alt - Fn  ```
 export DISPLAY=:0.0 
xterm & 
```  (assuming :0.0)

Thanks a lot! that works :)

---

