---
title: "[SOLVED] Problems installing CCL cybercafe software"
date: 2007-06-18
forum: General Help
---

### Post by torresrg on 2007-06-18
Hello everyone:

I am setting up an internet cafe using Ubuntu 7.04 on the workstations and server, and I am trying to install the Cafe con Leche managing software. I am fairly new to linux and I am having a hard time trying to compile the necessary libraries for the software (libcclc). I keep getting an error from the C compiler that it cannot create the executable files (err:2813). Does anybody have detailed instructions on how to install this software or does anybody know of a similar o better software I could use and easier to install? 

Thank you in advance for your time and replies. [-o<

---

### Post by maruchan on 2007-06-19
Can you post the specific error message here? Maybe you're not running something with superuser priveleges?

---

### Post by torresrg on 2007-06-19
Maruchan:

First of all, thank you for taking the time to reply to my post. Second, when trying to compile in Ubuntu 6.06 this is what I get (copied from my terminal):

root@torresrg-desktop:/home/torresrg/ccl/libcclc-0.7.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

When trying to compile in Ubuntu 7.04 I get the following error:configure:2813: error: C compiler cannot create executables
See `config.log' for more details.

Again, thanks for your time and help.

regards.

---

### Post by torresrg on 2007-06-26
Ok, I have managed to install the ccl software for the server and a client in Feisty Fawn using a couple of deb packages I found on thread. I tested the installation and managed to connect the client to server. I can turn off the screen of the client, end, and start a session. My problems now are as follows:

1) I cannot shutdown or restart the client from the server.
2) I cannot relate a sold product with a client or a session.
3) I cannot make a session end when the time assigned to that session expires.

Does anybody have a manual or ideas on how to work this issues out?

Again, thanks in advanced for your time.

---

