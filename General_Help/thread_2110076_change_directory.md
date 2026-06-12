---
title: "change directory?"
date: 2013-01-29
forum: General Help
---

### Post by sohlinux on 2013-01-29
Is there a quick way of changing directory for example

I am in /data/test/009

I want to get to /data/test/008

usually I would 

cd ..

cd 008

but how can I go directly with one command from folder 009 to to 008? without cd ..

thanks

---

### Post by omeomi on 2013-01-29
easy (but still with cd)
```
cd ../008
```

---

### Post by raja.genupula on 2013-01-29
I think nothing with out cd .. but there is some advantage with cd ...look at the image

---

### Post by sohlinux on 2013-01-29
> **omeomi said:**
> easy (but still with cd)
```
cd ../008
```

thanks but that didnt work, it just cd back one level but didnt cd to 008

---

### Post by sohlinux on 2013-01-29
> **raja.genupula said:**
> I think nothing with out cd .. but there is some advantage with cd ...look at the image

thanks but that didnt work

cd .. ; cd 009
bash: cd: 009: No such file or directory

---

### Post by omeomi on 2013-01-29
> **sohlinux said:**
> thanks but that didnt work, it just cd back one level but didnt cd to 008

Thats weird since that is supposed to work just fine, see the attached screenshot. 

Did you type a space between ../ and the dir name? Because that would just bump you up one level.

---

### Post by raja.genupula on 2013-01-29
> **sohlinux said:**
> thanks but that didnt work

cd .. ; cd 009
bash: cd: 009: No such file or directory

you see that image ?

---

### Post by sohlinux on 2013-01-29
> **omeomi said:**
> Thats weird since that is supposed to work just fine, see the attached screenshot. 

Did you type a space between ../ and the dir name? Because that would just bump you up one level.
I tried all ways but it only goes back one level

why use screen shots?

---

### Post by sohlinux on 2013-01-29
> **raja.genupula said:**
> you see that image ?

yes I see it but it doesnt work on mine

---

### Post by omeomi on 2013-01-29
What is the output of this:
```
 ls /data/test
```

I added the screenshot to demonstrate that the command does work on my system.

---

### Post by raja.genupula on 2013-01-29
> **sohlinux said:**
> I tried all ways but it only goes back one level

why use screen shots?

you need to mention all them in a single line and separate each with a ; and it will work for all levels . you just need to assume currently where you are .

and screen shots for more clarity.

---

### Post by sohlinux on 2013-01-29
> **omeomi said:**
> What is the output of this:
```
 ls /data/test
```

I added the screenshot to demonstrate that the command does work on my system.

ls /data/test

001/ 002/ 003/ 004/ 005/ 006/ 007/ 008/ 009/

---

### Post by omeomi on 2013-01-29
Ok, just checking :-)

Could you maybe add a screenshot of your own terminal when you type either my or raja's commands?

Are you using the default Ubuntu terminal?

---

### Post by sohlinux on 2013-01-29
cd .. ; cd 008 works now, not sure why it didnt first time

thanks guys ;)

---

### Post by raja.genupula on 2013-01-29
> **sohlinux said:**
> cd .. ; cd 008 works now, not sure why it didnt first time

thanks guys ;)


Mark your thread as solved from thread tools.

---

