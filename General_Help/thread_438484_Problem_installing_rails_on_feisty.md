---
title: "Problem installing rails on feisty"
date: 2007-05-09
forum: General Help
---

### Post by cknoblock on 2007-05-09
I installed ruby and rubygems via Synaptic, and afterwards installed rails via gem install rails --include-dependencies.  

After the install is completed it does not seem as if rails is installed. I run rails from the command terminal and I get the error stating to install rails via apt-get. How do I fix?

-chris

---

### Post by cknoblock on 2007-05-09
I was able to find rails under /var/lib/gems/1.8/bin. Seems to me that it goes in /usr/bin for everyone else. Can someone confirm this? Any ideas why this might happen?

Thanks!

-chris

---

### Post by chamstar on 2007-05-16
I found it best to install ruby (plus ir, rdoc etc.) from synamtic and then download gem from their website and run the install program (setup.rb). Installing gem or rails from Synaptic never worked for me (it appeared to install but did not run from the command line).

Cham.

---

### Post by TheOtherShoe on 2007-05-25
Installing gems in /var/lib/gems must have been a design decision by either Ubuntu or Debian. You can run programs installed as gems by adding the appropriate bin directory to your path.
```
PATH=$PATH:/var/lib/gems/1.8/bin
```

If you don't want to have to run that command every time you open a new terminal, add it to .bashrc in your home directory.

---

