---
title: "Compiling Conglomerate: libs are missing"
date: 2014-04-18
forum: General Help
---

### Post by claus on 2014-04-18
Hi all,

I would like to install the XML editor Conglomerate, which I downloaded as a .tar.gz archive. At the end of ./configure, I am getting:

configure: error: Library requirements (  gtk+-2.0 >= 2.4.0              gconf-2.0 >= 1.2.0		  libxml-2.0 >= 2.0.0	  libxslt >= 1.0.0		  libbonobo-2.0 >= 2.0.0	  libbonoboui-2.0 >= 2.0.0	  libgnomeui-2.0 > 2.0.0  libglade-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I did try to  display the PKG_CONFIG_PATH variable, but I  am only getting a blank line (I tried 'echo PKG_CONFIG_PATH').

What can I do to solve this problem?

TIA,

Claus

---

### Post by steeldriver on 2014-04-18
Do you really need to build it from source? What Ubuntu version are you running? It seems to be available from the repository e.g. on 12.04:

```

$ apt-cache search Conglomerate
conglomerate - user-friendly XML editor
conglomerate-common - common files for the user-friendly XML editor

```

Anyhow, if you still want to build it yourself you will need to make sure you have installed all the prerequisite development packages (libgtk2.0-dev, libgconf2-dev etc.)

---

### Post by claus on 2014-04-18
>  It seems to be available from the repository e.g. on 12.04

My, why didn't I think of that first? ;-) I still have 10.04 installed (but I will upgrade soon), and it is included in the repository. Thanks a lot!

Claus

---

### Post by claus on 2014-04-18
>  It seems to be available from the repository e.g. on 12.04

My, why didn't I think of that first? ;-) I still have 10.04 installed (but I will upgrade soon), and it is included in the repository. Thanks a lot!

Claus

---

