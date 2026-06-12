---
title: "List files in package"
date: 2007-10-10
forum: General Help
---

### Post by Anicka on 2007-10-10
I have a somewhat strange question. Is there a way to list the files in a package from the repos WITHOUT actually downloading the package? I know that if the package is installed I can get the list with dpkg -L *package* or if it's downloaded with dpkg -c *package*.

Any ideas?

---

### Post by kevdog on 2007-10-10
Take a look at this:
[http://www.ubuntugeek.com/what-package-is-that-file-in.html](http://www.ubuntugeek.com/what-package-is-that-file-in.html)

---

### Post by Anicka on 2007-10-10
But it still assumes that the package is downloaded and it gives the answer to the opposite question (which package does the file belong to), right?

---

### Post by Anicka on 2007-10-10
Ok, found a semi-good way (webbrowser, [http://packages.ubuntu.com/feisty/allpackages](http://packages.ubuntu.com/feisty/allpackages), go to package and list files). It will be sufficient for now, but a one line command had been better...

---

