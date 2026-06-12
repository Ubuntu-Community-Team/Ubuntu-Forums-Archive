---
title: "apt-get update not working, source list"
date: 2015-11-28
forum: General Help
---

### Post by Bleakley on 2015-11-28
Hi, I get the following error when running sudo apt-get update

E: Type '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Ha&#65533;&#65533;' is not known on line 1 in source list /etc/apt/sources.list.d/atareao-atareao-trusty.list
E: The list of sources could not be read.

I do: 
less /etc/apt/sources.list.d/atareao-atareao-trusty.list

 and get:
"/etc/apt/sources.list.d/atareao-atareao-trusty.list" may be a binary file.  See it anyway? 

Which doesn't seem very helpful. 

Any advice?

---

### Post by Bashing-om on 2015-11-28
Bleakley; Hello;

I would 'cat' that file and "see" what the line reads:
```

cat /etc/apt/sources.list.d/atareao-atareao-trusty.list

```
depending on what is, is what action to take to remedy .

[INDENT][INDENT]package manager not happy
[INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bleakley on 2015-11-28
cat /etc/apt/sources.list.d/atareao-atareao-trusty.list

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Ha&#65533;&#65533;
_&#65533;9h!f!5&#65533;&#65533;;&#65533;c&#65533;g.'&#65533;&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;'ST&#65533;UK^&#65533;&#65533;&#65533;&FH¸&#65533;u&#65533;&#65533;&#65533;Fp&#65533; 7&#65533;G&#65533;&#65533;&#65533;g&#65533;}&#65533;h&#65533;&#65533;&#65533;'&#65533;&#65533;&#65533;J&#65533;a&#65533;&#65533;&#65533;CB&#65533;&#988;X&#65533;&#65533;d&#65533;Q&#65533;&#65533;&#65533;8&#65533;'&#65533;&#65533;

:(

---

### Post by Bashing-om on 2015-11-28
Bleakley; Uh Huh ...

For sure that is 'binary' .. The files should be a ASCII text file.
Remove that erroneous file :
```

sudo rm -r /etc/apt/sources.list.d/atareao-atareao-trusty.list

```

And IF you desire this package on your system:
refer to:
[https://launchpad.net/~atareao/+archive/ubuntu/atareao](https://launchpad.net/~atareao/+archive/ubuntu/atareao)
and follw the instructions given on the site to properly install the PPA.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-11-28
If you really need something from that atareao-atareao source you will need to go to [https://launchpad.net/~atareao/+archive/ubuntu/atareao](https://launchpad.net/~atareao/+archive/ubuntu/atareao) and follow the instructions to enable it again.

Whoops! I missed that post from Bashing-om.  Nevermind; you now have it from both of us.

---

