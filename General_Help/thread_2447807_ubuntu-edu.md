---
title: "ubuntu-edu"
date: 2020-07-26
forum: General Help
---

### Post by cmcanulty on 2020-07-26
I am setting up several computers for a local kids science center. I am having no luck finding any of the ubuntu-edu packages for 20.04. Can someone give me an update of these packages? I hate to start out with 18.04 instead of 20.04 just to get these packages.

---

### Post by &amp;KyT$0P# on 2020-07-26
They are meta-packages, so you could [look them up on packages.ubuntu.com]("https://packages.ubuntu.com/search?keywords=ubuntu-edu&searchon=names&suite=bionic&section=all") to see their dependencies, then individually [FONT=Courier New]apt-get install[/FONT] the packages they depend on that you want.

---

### Post by cmcanulty on 2020-07-26
So if I do that then I could install the bionic pkgs?

---

### Post by &amp;KyT$0P# on 2020-07-26
I'm suggesting you use that information to decide whether you need any bionic packages at all.

As the ubuntu-edu* packages are meta-packages, installing their dependencies manually provides exactly the same software as if you install just the meta-package.

---

### Post by cmcanulty on 2020-07-27
OK thanks I'll try that. Will take forever as there are maybe 100 packages

---

