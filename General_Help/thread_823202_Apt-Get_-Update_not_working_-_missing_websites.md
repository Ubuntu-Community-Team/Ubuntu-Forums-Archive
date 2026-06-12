---
title: "Apt-Get -Update not working - missing websites?"
date: 2008-06-09
forum: General Help
---

### Post by Redlazer on 2008-06-09
When I run sudo apt-get update, I get a bunch of missing websites. I tried to run --fix-missing, but i either get the same error or it gves me the --help printout.

Ideas?

-Fred

---

### Post by F3u3rfr3i on 2008-06-09
Same thing, and someone had something about going to System, Administration ect.. to turn on other hosts, I can't find that either, so right now my apt-get is broke, and I tried going to the url, and indeed the folder / files are gone.

---

### Post by Redlazer on 2008-06-10
Anyone have any idea?

-Fred

---

### Post by avtolle on 2008-06-10
First question: which release are you running, i.e., 6.10, 7.04,...?

EDIT: Second question, are you by chance running ppc?

---

### Post by Powerman2442 on 2008-06-10
I had a similar problem with this error...

"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list"

Not sure if you two are having a similar error, but I had to post my sources.list.

**sudo gedit /etc/apt/sources.list**

And post the contents of that. I'm sure someone will be able to help you. I ended up having a missing repository.

Good Luck!

---

### Post by Robux the great on 2008-06-10
Hi I am new to this aswell but when I had this problem I checked my sources.list file and found that some of the repos were commented out.

You may have to manualy add some repos to your sources.list file

Have a look at the ubuntu wiki

Regards

Rob

---

### Post by editrix on 2008-06-10
It's also possible that the repository you're using is down. If you have Synaptic installed, try Settings > Repositories, Download from: > Other, Select Best Server. Choose Server, Close. After doing this try running your commands again.

This may work in Adept, too. I don't use it so I don't know.

---

