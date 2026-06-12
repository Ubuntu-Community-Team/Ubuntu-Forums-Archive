---
title: "pureftpd won't start"
date: 2005-06-24
forum: General Help
---

### Post by z-two on 2005-06-24
Hi,
I have previously run an ftp server off a windows machine, and now that i have made the switch to running ubuntu most of the time i have decided to try and install an ftp server here too. The server is just for me and a couple of friends to use now and again.

I installed pureftpd using apt (would it be better for me to compile it??), but instantly ran into a problem when trying to run it for the first time, i got the error:

"Unable to start a standalone server: Address already in use"

But when i start it with the -S option to set a port other than port 21 it starts fine. Does this mean that there is another application allready listening for something on port 21??

Anyway my questions are,

[list=1]
[*]Is pureftpd a good ftp server to use for this type of thing, and is it ok to use apt to install or should i compile from source?
[*]Would it be better for me to run the server as a standalone or with inetd
[*]What should i do to try and correct this error, if it is something blocking the port or whatever how can i find out what it is, and how can i prevent it from doing so?
[/list] 

Thanks

---

### Post by jiyuu0 on 2005-06-24
i've recently added a section for pureftpd in [http://ubuntuguide.org](http://ubuntuguide.org)

using the apt-get method to install it

---

### Post by z-two on 2005-06-24
Isn't that section about proftpd rather than pureftpd. I keep getting annoyed by their similarities in name, search for stuff about pureftpd in google and most of the stuff is about proftpd. Anyway thanks for the response.

---

### Post by jiyuu0 on 2005-06-24
[QUOTE=z-two]Isn't that section about proftpd rather than pureftpd. I keep getting annoyed by their similarities in name, search for stuff about pureftpd in google and most of the stuff is about proftpd. Anyway thanks for the response.[/QUOTE]

soli... i saw it wrongly too :(

---

