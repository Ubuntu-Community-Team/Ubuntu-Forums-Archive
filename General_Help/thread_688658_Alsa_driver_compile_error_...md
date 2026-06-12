---
title: "Alsa driver compile error .."
date: 2008-02-05
forum: General Help
---

### Post by 4spect on 2008-02-05
Hi Everyone ..

I'm having a bit of a problem with my sound card ...
First of all it's a Intel HDA card.

My laptop is needed a update of the alsa driver everytime I reformat, and
I have done it 100 of times, but now I'm getting this wierd problem when I will try to 
compile the driver.

I've downloaded the alsa-driver-1.0.15.tar.bz2 and copied it to /usr/src/alsa/ and untared 
it

When I add the line:
sudo ./configure --with-cards=hda-intel (in the terminal)

It gives me a wierd error saying: (copied from terminal)

xx@xx-laptop:/usr/src/alsa/alsa-driver-1.0.15$ sudo ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
xx@xx-laptop:/usr/src/alsa/alsa-driver-1.0.15$ cofig.log
bash: cofig.log: command not found

I really don't get it, because i have the correct way wrote down in a text doc, and I've used it several times without any probs ..

Please help me ..
4spect

---

### Post by odiseo77 on 2008-02-05
I think you need build-essential (and gcc). In a terminal, type:

```
sudo apt-get install build-essential
```

Hopefully, it will install the needed dependencies to compile.

---

### Post by 4spect on 2008-02-05
> **odiseo77 said:**
> I think you need build-essential (and gcc). In a terminal, type:

```
sudo apt-get install build-essential
```

Hopefully, it will install the needed dependencies to compile.

Thanks for the quick reply, and it seemed to work fine with the alsa-driver-1.0.15 and the alsa-lib-1.0.15, but the alsa-utils-1.0.15 could only configure ..
When I run the sudo make command it says that no makefile found ..

Hope you can help me with this one ..
4spect

by the way; when I run alsamixer command it still says that I'm running 1.0.14 driver ?? Why?

---

### Post by odiseo77 on 2008-02-05
Did you execute "./configure" inside the alsa-utils directory? did the configure script finished fine? (most of times the makefile is created by the configure script).

---

