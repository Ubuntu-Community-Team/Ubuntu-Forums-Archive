---
title: "Opera Java Plugin"
date: 2005-09-26
forum: General Help
---

### Post by karuptdata on 2005-09-26
I have been trying to get java plugin installed for go d knows how long i have searched hi and low to no avail any ideas??

---

### Post by KillerBOB on 2005-09-26
Hi! I became curious (sp?) when I read your post, and found out that my Opera did not find the Java plugin either. I eventually found the solution - Java seems to be disabled by default in Opera.

This is the steps I did to enable Java:

```
1. Start up Opera (in my case Opera 8.5, should be similar for 8.x I guess)
2. Go to "Tools - Preferences"
3. Go to "Content" and check the box "Enable Java"
4. Press "Java options" 
5. Input "/usr/lib/j2re1.5-sun/lib/i386/" (without quotes) into "Java path"-field
6. Press "Validate Java Path"-button
7. Restart Opera
```

Now Java should work! 

Be sure that you use the correct path to Java, check by typing this (in terminal):
```
locate libjava.so
```
In my case that returned:
```
/usr/lib/j2re1.5-sun/lib/i386/libjava.so
```

Hope this helps!

/Anders

---

### Post by karuptdata on 2005-09-26
Thanks i got it up and running...Wow that was annoying me for days...LOL thanks again!

---

### Post by KillerBOB on 2005-09-26
Good! I'm glad it worked!
/Anders

---

### Post by 3dxtrip on 2006-10-24
Useful Tip

Thanks!

---

