---
title: "VMware Player: C header files?"
date: 2007-04-21
forum: General Help
---

### Post by Fuzzy Logic on 2007-04-21
Hello people.

When configuring VMware Player with vmware-config.pl I get the following question:
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

When i press ENTER it says the following thing:
> The path "/usr/src/linux/include" is not an existing directory.

I've searched on the internet a little about that, and on a dutch Ubuntu forum someone suggested that the path is /usr/src/linux-headers-[[version]]/include, but when I fill that in I get the following error:
> The directory of kernel headers (version 2.6.20-15) does not match your running
kernel (version 2.6.20-15-386).  Even if the module were to compile 
successfully, it would not load into the running kernel.

I realised that I use kernel 2.6.20-15-386, and that the kernel version in the path is without that 386. But the problem is I don't know what to do about it. Can anyone help me please? Thanks.

---

### Post by ArieT on 2007-04-21
You can install vmware player with synaptic. It's in multiverse

---

### Post by Fuzzy Logic on 2007-04-21
ArieT,

I tried to do that, but than it stopped somewhere on the half of the installation, when I opened the terminal it said that several files already existed and asked me if I wanted to overwrite them. When i answered yes it asked again over and over, when i said no it asked me again but after the second time it continued the installation and at the end it said error 1, but the Synaptic says that it's installed. And indeed, terminal does know the vmplayer command, but it always asks me to do the config.

---

### Post by zvacet on 2007-04-21
Uninstall existing vmplayer with synaptic and after that install it again.Your previous installation make you troubles.

---

### Post by Fuzzy Logic on 2007-04-21
zvacet,

I tried that, but that doesn't help, it still asks me those questions.

---

