---
title: "Problem starting program in terminal"
date: 2013-01-23
forum: General Help
---

### Post by paulemony on 2013-01-23
I have a program (model flight sim crrcsim) in folder **Downloads/crrcsim-0.9.11** which contains executable file ```
crrcsim
```but I can't start it in terminal, ```
cd Downloads/crrcsim-0.9.11 && crrcsim
``` just says command not found, but if I go into the folder & click executable ```
crrcsim
``` it opens. If I put a short cut or a launcher on desktop & click on it I get error message ```
unable to load airplane file:
error opening airplane specification file: Error opening
```
Basically I want a launcher of some kind on Desktop but if it won't open in terminal anyway it can't be done, what to do?

---

### Post by papibe on 2013-01-23
> Hi paulemony.

Could you post the result of these commands?
```
ls -l Downloads/crrcsim-0.9.11

file *crrcsim*
```
Regards.

Ignore that.

Try this:
```
cd Downloads/crrcsim-0.9.11 && **[COLOR="Red"]./[/COLOR]**crrcsim
```

---

### Post by paulemony on 2013-01-24
Yes, that's it, works in terminal, not sure what the **./**does exactly but one to remember for next time. Still doesn't work as Desktop Launcher but wll tweak it till it does! Thx.

---

### Post by mcduck on 2013-01-24
> **paulemony said:**
> Yes, that's it, works in terminal, not sure what the **./**does exactly but one to remember for next time. Still doesn't work as Desktop Launcher but wll tweak it till it does! Thx.

"./" tells the shell to look for the program in your current directory ("." is the current directory, ".." is the parent directory).

What comes to the desktop launcher, it sounds like the program is looking for some files in your current directory and isn't able to find them unless you actually are in the program's directory when you start it. In that case the easy solution is to create a simple shell script  to cd into the program's directory and start it, and then point your launcher to that script instead of the executable file.

---

### Post by paulemony on 2013-01-24
I half-anticipated you by using a shell script *instead* of a launcher, but didn't think of creating a launcher pointing at it.If they're both on Desktop and the shell script is called **crrcsim** then logic dictates that's all that's needed as a command for the launcher, needless to say it's not that simple, it needs the whole shebang **/home/username/Desktop/crrcsim**. Academic in a way as the shell script does the job and the launcher would just be something else on the desktop, but have learnt something new!

---

