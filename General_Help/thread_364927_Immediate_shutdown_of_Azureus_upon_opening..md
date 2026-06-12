---
title: "Immediate shutdown of Azureus upon opening."
date: 2007-02-18
forum: General Help
---

### Post by aresgoddess on 2007-02-18
Today has been a strange day for my computer and i think the various problems might be related so here goes:

First off, the internet went offline but stayed connected. The connection was there, but nothing was going through. My laptop connects wirelessly to the router, while the family desktop connects directly to the router. Both could not connect at all. After calling both Time Warner and Belkin's tech support, I was told to reset the router. (The router is Belkin brand.) Which fixed the problem. 

Around the time the internet cut out, Azureus shut down by itself. After I realized that the internet wasn't working, I had gone to shut down all my internet programs and couldn't find Azureus open at all. Once the router problem and the connection problem that had ensued on my own computer had both been fixed, i found that Azureus closed almost immediately after i opened the program. 

Does anyone know what causes this or what I can do to fix this?

---

### Post by taurus on 2007-02-18
Run it from a terminal to see what's the problem is.

Applications -> Accessories -> Terminal
```
azureus
```

---

### Post by tesseract420 on 2007-02-21
Same thing happens to me:  here's the info, how to fix?

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=10302, tid=3085048736
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid10302.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by Catsworth on 2007-02-21
I had exactly the same problem here: [http://ubuntuforums.org/showthread.php?t=353197](http://ubuntuforums.org/showthread.php?t=353197)

Got it working (as you will see from the thread, so maybe the advice there will help you) but then realised last night that it's broken again :(

I think there's something in one of the updates that's borking it, I haven't had a chance to see if repeating the instructions that I was given last time will work again.

---

