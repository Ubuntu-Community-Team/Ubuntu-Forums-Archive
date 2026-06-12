---
title: "Correct Place to put Downloaded Executables?"
date: 2012-12-06
forum: General Help
---

### Post by derricw on 2012-12-06
Hey guys,

I'm relatively new to linux.  I downloaded a package, Sublime Text 2, and after extracting it, the executable seems to run perfectly fine.

Where is the correct "linux" place for me to put this folder, which contains various other files that go with the executable?

From my understanding most executable files are stored in /usr/bin/, but when I put the executable in that folder, it doesn't run (i think because it doesn't have whatever companion files normally live in the local folder?).

Thanks in advance for the help.

-Derric

---

### Post by hwttdz on 2012-12-07
Here's a real quick overview: [http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

I'd probably suggest $HOME/bin, or even leave it somewhere not usually considered a binary directory and then make a link to it from $HOME/bin.  

My rough rules of thumb:
~/bin, ~/scripts - things that are for my user
for all users:
/usr/bin - only the package manager puts things here
/usr/local/bin - things that are straightforward "./compile && make && sudo make install"
/opt - larger things, sometimes goofy packages

---

### Post by derricw on 2012-12-07
Thanks for the advice!

I wound up leaving the folder in my home directory (renaming it with a "." to make it hidden), and then putting a link to the executable in /usr/local/bin/

This makes it that I can run it via terminal, which was one of my goals with this.

It sounds from my reading that there isn't a completely right way to do this.

---

### Post by Habitual on 2012-12-07
Love this Editor so much, I Paid for it.

I run mine from the extracted download location. :)

Not even a symlink to /usr/local/bin/ for me.
Your method is sound. :)

Merry Christmas!

---

