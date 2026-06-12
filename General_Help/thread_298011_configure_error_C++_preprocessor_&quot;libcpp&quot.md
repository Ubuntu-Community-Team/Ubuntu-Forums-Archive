---
title: "configure: error: C++ preprocessor &quot;/lib/cpp&quot; fails sanity check"
date: 2006-11-12
forum: General Help
---

### Post by slamdunk on 2006-11-12
Hi,

when I try to compile any c++ application, after:

./configure --prefix=/usr

I got this error:

configure: error: C++ preprocessor "/lib/cpp" fails sanity check

> ls -l /lib/cpp

/lib/cpp -> /etc/alternatives/cpp

> ls -l /etc/alternatives/cpp

/etc/alternatives/cpp -> /usr/bin/cpp

> cpp --version

cpp (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

is it a c++-compiler version problem? Is there a solution for it?

In Google I have not found a good solution...

Thanks,
Giulio

---

### Post by junglepeanut on 2006-11-12
What are you trying to install? Many times somebody has written some code to make sure that you compile with the same compiler they have as they have used options that maybe comiler specific, sometimes even version specific. Most of this can be remedied by reading the readme, install.txt, or configure script themselves and finding what you are looking for. 

Started rambling so no need to read below unless your bored.

ps I have no idea what I am talking about, just experience tells me the above not real knowledge. As when I try to install certain things I have had to do some crazy things, like disable wxwidgets, change lang=c++ to lang=ALL_C and other things. Most of the time I did not figure these things out myself but was able to locate an individual with the same platform I was using who had figured it out or had emailed say gnuplot to figure it out and thus posted a nice tutorial which I found through google. I mention gnuplot as installing the latest version a few months ago on an intel duo core mac was a pain in the but. Or since I am rambling, installing some fortran compilers requires genreating dummy routines that do nothing but the compiler expects them to be there so they better be there.

---

### Post by junglepeanut on 2006-11-12
Ooh, missed the any c++ application the first time. Not sure what the issue is.

You do have build-essential etc right?

---

### Post by slamdunk on 2006-11-12
Hi,

I have solved. It needed just install g++ package and relative dependencies.

Thanks,
Giulio

---

