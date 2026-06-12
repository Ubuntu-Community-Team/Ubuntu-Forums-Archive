---
title: "Install SMART Notebook"
date: 2014-01-20
forum: General Help
---

### Post by gelyn28 on 2014-01-20
I'm trying to install SMART Notebook on my laptop running Ubuntu 12.04 LTS and I've run into a bit of a problem. 
I have instructions on how to install it, [identical to the ones given here]("http://www.linkedin.com/groups/I-want-install-Smart-Board-65688.S.5801287571497570305"), but after running the first "sudo dpkg -i " command it seems to first start to work, but then I run into this error message in terminal: 

Errors were encountered while processing: smart-common

I'd appreciate any help, thank you.

---

### Post by gelyn28 on 2014-01-20
I ended up being able to resolve this issue. It seems that I didn't have libgl1-mesa-glx installed. Once I installed that, I was able to follow the directions I had given above and install it.

---

