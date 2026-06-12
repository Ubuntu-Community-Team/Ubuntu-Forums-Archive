---
title: "BiCon help in Ubuntu 7.04 fiesty"
date: 2007-11-11
forum: General Help
---

### Post by Pronco on 2007-11-11
First of all, I would like to introduce BiCon. Its a console program that supports bidirectional text display.

Regarding my problem:

When I'm trying to install and compile the bicon program everything is working properly during the installation. but in order to let my console support the bicon font. It has to be loaded in the console screen using **consolechars** command

Here's the following loading syntax:

[php]consolechars -f /usr/local/share/bicon/font/bicon-8x16-512.psfu.gz[/php]

but unfortunately it doesn't work and the following error has been occurred during the execution process:

[php]Couldnt get a file descriptor referring to the console
get_console_fd: Invalid argument[/php]

What does it supposed to be ?

Your help would be much appreciated

Thank You!
Pronco

---

### Post by Pronco on 2007-11-12
Any updates

---

