---
title: "Is there a way to install jHipster on Ubuntu 14.04?"
date: 2015-04-15
forum: General Help
---

### Post by angry-hipster on 2015-04-15
[COLOR=#111111][FONT=Ubuntu]Can you give an advise is it possible to install crappy jHipster on Ubuntu 14.04? Yesterday I try to do this by following regular routine on the jHipster site but got a lot of  errors. After I start to search how install it on Ubuntu and something was successful but after when I try to install  jHipster it gives me crappy messages " WARN engine generator-jhipster@2.7.0: wanted: {"node":">=0.10.0","npm":">=1.4.0"} (current: {"node":"v0.10.25","npm":"1.3.10"}) " a lot of stupid text and that's all[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Does somebody have successful experience with this?[/FONT][/COLOR]

---

### Post by dragonfly41 on 2015-04-15
[COLOR=#111111][FONT=Ubuntu]"npm":">=1.4.0" ... says it all.

[/FONT][/COLOR]In my 14.04 I had a look and Synaptic Package Manager shows npm version 1.3.10

So you will need to _manually_ install npm version 1.4.0 or latest.

[https://www.npmjs.com/package/npm](https://www.npmjs.com/package/npm)

---

### Post by dragonfly41 on 2015-04-15
For information.. on Ubuntu 14.04 .. I've just now had to install npm for a php5 framework .. laravel5 .. elixir.

[http://laravel.com/docs/5.0/elixir](http://laravel.com/docs/5.0/elixir)

this installed ..

node -v v0.10.38
npm -v 1.4.28

---

