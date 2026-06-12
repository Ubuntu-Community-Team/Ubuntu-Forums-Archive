---
title: "Unable to Start X,  Waiting for X Server"
date: 2012-12-02
forum: General Help
---

### Post by morbid_bean on 2012-12-02
I am not able to start x from CLI

I get an error that says:

```
waiting for Xserver to shut down Server terminaged successfully (0). Closing log file.
```

---

### Post by ohnonot on 2012-12-03
with what command are you trying to start X?
is another xsession already running?

---

### Post by morbid_bean on 2012-12-04
From a fresh boot I enter the following command:

```
jim@Tux:~$ startx
```

Then the screen flashes black and then I am presented with the error message.

---

### Post by ohnonot on 2012-12-04
i see.
you should really give more information.
my interpretation of your sparse description:
you installed a barebone system and added graphical desktop environment packages to that? 
that right?
which, exactly?

i tried something like this twice - both times with debian. first i tried to build my own desktop environment brew from the command line, but it was impossible for a halfnerd like me.
next, i also installed from command line but followed instructions from debian.org to install one package (i think it was lxde-task) that pulled everything else in. that worked but for reasons i don't remember anymore i ended up reinstalling precompiled debian wheezy lxde, and that works just fine on my 2nd machine.

arch linux forums usually have good docs for this kind of advanced stuff.

so what exactly are you trying to brew?

---

