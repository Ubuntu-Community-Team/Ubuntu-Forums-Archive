---
title: "Apache Installation"
date: 2005-04-01
forum: General Help
---

### Post by ExemplarUbuntu on 2005-04-01
Is there a simple way of installing Apache httpd on Ubuntu ? Everything seems to start with downloading source code, frankly, life's too short. 

I can't see it in the Synaptic installer.

---

### Post by bihe on 2005-04-01
[QUOTE=ExemplarUbuntu]Is there a simple way of installing Apache httpd on Ubuntu ? Everything seems to start with downloading source code, frankly, life's too short. 

I can't see it in the Synaptic installer.[/QUOTE]

it's definetly in the repository. search for apache2 in synaptic, or opern a shell
sudo apt-get install apache2. the 1.3.x branch is in universe

---

### Post by ExemplarUbuntu on 2005-04-05
Thanks, I was looking for httpd.

I had a look for the config file and can't find it in /etc/httpd and which httpd shows nothing. How do I check it has installed ?

I apologise for the basic questions, I'm new to Apache.

---

### Post by bmichel on 2005-04-05
Directory is /etc/apache2

look after apache2.conf for Apache2 global parameters

and sites-available/default for your local web site parameters

if you are really a newby with apache, be careful when you change some parameters. Make a backup of these 2 files and test changes one by one.

use sudo apache2ctl restart to reload apache2 after change.

---

### Post by ExemplarUbuntu on 2005-04-05
Thanks. I've now found the Apache2 folder and tried to run apache2ctl but it folds at line 79 where it tries to start httpd.

Seems it can't find http and neither can I. Do I need to install the mpm worker ?

---

### Post by bmichel on 2005-04-05
apache 2  is started automatically once installed.

try    ps -ef | grep apache2
to see running processes or launch your web browser with [http://localhost](http://localhost) . Welcome page of apache should appear.

you should have installed apache2, apache2-common, apache2-mpm-prefork (or another apache2-mpm...). prefork is mandatory in case of php4.
use synaptic and do a search on apache2 keyword.

---

### Post by ExemplarUbuntu on 2005-04-06
Merci.

I installed the mpm worker with Synaptic and the [http://localhost](http://localhost) page is now accessible.

Peter

---

### Post by qbase on 2005-04-06
How do I get SSL working with apache2-common?
Why isn't it enabled as default?  :confused:

---

### Post by bmichel on 2005-04-06
[QUOTE=qbase]How do I get SSL working with apache2-common?
Why isn't it enabled as default?  :confused:[/QUOTE]
 Check this url:
[http://www.gpltarragona.org/node/view/318](http://www.gpltarragona.org/node/view/318)

it's not plain english but you should be able to get it.

---

