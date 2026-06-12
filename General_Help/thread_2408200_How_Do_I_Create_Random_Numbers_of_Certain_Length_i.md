---
title: "How Do I Create Random Numbers of Certain Length in Ubuntu's Terminal?"
date: 2018-12-15
forum: General Help
---

### Post by scribner on 2018-12-15
Hi, what is the simplest way to generate, say, 20 random numbers that are all 10 digits long using Terminal in Ubuntu? I am new to Ubuntu and don't know anything about coding in Terminal. Additionally, is there a different app I should be using to do this in Ubuntu? The only programming language I've used is PHP, and I don't want to have to run this code on a web server.

---

### Post by CatKiller on 2018-12-15
You could use something like ```
tr -dc '0-9' </dev/urandom |  head -c 10
``` to generate a 10-digit random number.

---

### Post by Holger_Gehrke on 2018-12-15
Two thoughts on this:
[LIST]
[*] There is a special variable in bash named RANDOM which contains a different random number between 0 and 32767 (15 bits) every time it's accessed. With a bit of math you can produce random numbers of any size you need.
[*]PHP can be used as a scripting language outside of a web server. Take a look at the package php-cli.
[/LIST]

Holger

---

