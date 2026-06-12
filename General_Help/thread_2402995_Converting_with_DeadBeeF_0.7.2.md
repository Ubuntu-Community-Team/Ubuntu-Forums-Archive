---
title: "Converting with DeadBeeF 0.7.2"
date: 2018-10-06
forum: General Help
---

### Post by czgirb on 2018-10-06
[FONT=arial][FONT=arial]
[/FONT]now, i'm using xubuntu 18.04
everything was newly installed
and yesterday i found that my daedbeef unable to convert a thing

for ogg, i installed:
```
sudo apt-get install vorbis-tools
```
with following settings:

```

Output File Name ....... %a - %t [%l] .......... *is this the right format for **Number - Artist - Title**?*
DSP Preset ............. Pass Through
Output Sample Format ... Keep Source Format
When File Exist ........ Prompt
Command Line ........... oggenc -q 9 -o %o -
Method ................. PIPE

```

and i able to convert a thing, but i can't find the file
why? please guide me how to solve this problem?
[/FONT]

---

### Post by Yellow Pasque on 2018-10-06
Can you run from the terminal and see if you get more specific error(s)?

---

### Post by czgirb on 2018-10-11
> **Temüjin said:**
> Can you run from the terminal and see if you get more specific error(s)?

how to run from terminal ?

---

### Post by czgirb on 2018-10-13
as requested:

czgirb@czgirb-laptop:~$ deadbeef
deadbeef: command not found
czgirb@czgirb-laptop:~$ man deadbeef
No manual entry for deadbeef
czgirb@czgirb-laptop:~$

---

### Post by mc4man on 2018-10-13
You are using the snap version of deadbeef which has little to no actual encoding ability. To see what's up the terminal command to run  is 
```
deadbeef-vs
```

To use the full featured one, opens with just command of deadbeef either add this ppa & run 
```
sudo apt install deadbeef
```
[https://launchpad.net/~starws-box/+archive/ubuntu/deadbeef-player](https://launchpad.net/~starws-box/+archive/ubuntu/deadbeef-player)

Or just download appropiate package from ppa & install with apt

To get rid of the snap version,
```
sudo snap remove deadbeef-vs
```

---

### Post by deadflowr on 2018-10-13
Is deadbeef in any Ubuntu repository?

---

### Post by mc4man on 2018-10-13
> **deadflowr said:**
> Is deadbeef in any Ubuntu repository?
Opps, had forgotten I'd grabbed the package from this ppa
[https://launchpad.net/~starws-box/+archive/ubuntu/deadbeef-player](https://launchpad.net/~starws-box/+archive/ubuntu/deadbeef-player)

---

### Post by czgirb on 2018-10-13
[QUOTE=mc4man;13808261]You are using the snap version of deadbeef which has little to no actual encoding ability. To see what's up the terminal command to run  is 
```
deadbeef-vs
```

czgirb@czgirb-laptop:~$ deadbeef-vs
deadbeef-vs: command not found
czgirb@czgirb-laptop:~$

---

### Post by czgirb on 2018-10-13
> **mc4man said:**
> 
To get rid of the snap version,
```
sudo snap remove deadbeef-vs
```


czgirb@czgirb-laptop:~$ sudo snap remove deadbeef-vs
[sudo] password for czgirb: 
snap "deadbeef-vs" is not installed
czgirb@czgirb-laptop:~$

---

### Post by mc4man on 2018-10-13
So if deadbeef isn't installed and deadbeef-vs isn't installed then where did you get it & how are you opening it?

---

### Post by czgirb on 2018-10-13
> **mc4man said:**
> So if deadbeef isn't installed and deadbeef-vs isn't installed then where did you get it & how are you opening it?

Menu > Multimedia > DeadBeeF

---

### Post by Yellow Pasque on 2018-10-13
> **czgirb said:**
> Menu > Multimedia > DeadBeeF

That is how you open it. Where did you get the deadbeef package/source from?

---

### Post by czgirb on 2018-10-14
> **Temüjin said:**
> That is how you open it. Where did you get the deadbeef package/source from?

i install it as it was stated from a webpages, which i don't remember the URL
i starting to smell that there is something with mine
please guide me how to fix it ... please ...

---

### Post by czgirb on 2018-10-23
> **czgirb said:**
> i install it as it was stated from a webpages, which i don't remember the URL
i starting to smell that there is something with mine
please guide me how to fix it ... please ...



[SIZE=5]please guide me how to fix it. please !!![/SIZE]

---

