---
title: "script for switching from compiz to metacity"
date: 2008-02-20
forum: General Help
---

### Post by kaiwan on 2008-02-20
Hi! 

I have ubuntu gutsy. I have Matlab2007B which does not work with compiz and I have to 
use metacity. I would like to write a script which will automaticaly go from compiz to matcity 
when I click to matlab launcher on my main menu.

Idea is:

1. To check is compiz is in use
2. If compiz if in use, switch to metacity, if not go to 3
3. start matlab 

How can do that?

---

### Post by aashay on 2008-02-20
killall compiz.real && metacity

---

### Post by kaiwan on 2008-02-20
ok, but what will happen if matacity is alredy running ?

---

### Post by aashay on 2008-02-20
Nothing. killall will fail and the 2nd part wont be executed
Edit: heres a slightly better one:
```
killall compiz.real && metacity --replace & matlab
```

---

### Post by sisco311 on 2008-02-20
#!/bin/bash

if [ 0`pidof compiz.real` -gt 0 ]; then
# echo compiz is running
  killall compiz.real
  sleep 1
  metacity --replace
else
# echo no compiz
fi

#echo starting matlab

---

### Post by kaiwan on 2008-02-20
> **aashay said:**
> Nothing. killall will fail and the 2nd part wont be executed
Edit: heres a slightly better one:
```
killall compiz.real && metacity --replace & matlab
```

works....thanks....

---

### Post by kaiwan on 2008-02-20
> **sisco311 said:**
> #!/bin/bash

if [ 0`pidof compiz.real` -gt 0 ]; then
# echo compiz is running
  killall compiz.real
  sleep 1
  metacity --replace
else
# echo no compiz
fi

#echo starting matlab

so I have to write this:

-------
if [ 0`pidof compiz.real` -gt 0 ]; then
  killall compiz.real
  sleep 1
  metacity --replace
fi   # this line ends command or what?

&&  matlab

---

### Post by zeller on 2008-02-20
Have you heard of [Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)? It may help.

---

### Post by sisco311 on 2008-02-20
here is the complete script:

```
#!/bin/bash

if [ 0`pidof compiz.real` -gt 0 ]; then
  echo compiz is running
  killall compiz.real
  sleep 1
  metacity --replace
else
  echo no compiz
fi

echo starting matlab
matlab&
wait `pidof matlab`

compiz --replace

```save it in a file and make it executable.

note: the script will restart compiz when you exit from matlab

---

### Post by kaiwan on 2008-02-20
> **zeller said:**
> Have you heard of [Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)? It may help.

yes, I have it...but I would like to learn some more about scripts....

---

### Post by kaiwan on 2008-02-20
> **sisco311 said:**
> here is the complete script:

```
#!/bin/bash

if [ 0`pidof cat` -gt 0 ]; then
  echo compiz is running
  killall compiz.real
  sleep 1
  metacity --replace
else
  echo no compiz
fi

echo starting matlab
matlab&
wait `pidof matlab`

compiz --replace

```save it in a file and make it executable.

note: the script will restart compiz when you exit from matlab

Ok, thanks....and last thing...if I dont want to start compiz when exiting matalab I yust commet the last line: #compiz --replace ?

---

### Post by sisco311 on 2008-02-20
> **kaiwan said:**
> Ok, thanks....and last thing...if I dont want to start compiz when exiting matalab I yust commet the last line: #compiz --replace ?

yes

---

### Post by kaiwan on 2008-02-20
> **sisco311 said:**
> here is the complete script:

```
#!/bin/bash

if [ 0`pidof compiz.real` -gt 0 ]; then
  echo compiz is running
  killall compiz.real
  sleep 1
  metacity --replace
else
  echo no compiz
fi

echo starting matlab
matlab&
wait `pidof matlab`

compiz --replace

```save it in a file and make it executable.

note: the script will restart compiz when you exit from matlab

I run this script and thera are 2 problems:
1. it runs matlab under terminal, not normal X gui
2. when exiting matlab I get this error message:
-----
>> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
-----

and when I exit the terminal compiz chrashes and I have to restart X...

---

### Post by sisco311 on 2008-02-20
run the script from the terminal with nohup:
```
nohup ./my-script-name.sh
```
or create a launcher on your desktop

replace the matlab command with the proper command to start matlab in gui mode(???matlab -desktop???)

you can ignore the compiz warnings

---

### Post by kaiwan on 2008-02-21
> **sisco311 said:**
> run the script from the terminal with nohup:
```
nohup ./my-script-name.sh
```
or create a launcher on your desktop

replace the matlab command with the proper command to start matlab in gui mode(???matlab -desktop???)

you can ignore the compiz warnings

command matlab shud give matlab in gui mode....but I think there is one more, i will look for it.
Hoever, I tried with nohup and my screen just blinks once, and nothing...compiz doesn't stop,
matlab doesn't run....like script doesn't get executed....

---

