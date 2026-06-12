---
title: "How do I delete all these temporary files?"
date: 2007-05-17
forum: General Help
---

### Post by Fireblend on 2007-05-17
I'm talking about the ones that end with ~ that get created everytime I modify any document. Any way to delete them? I appreciate the security, but right now I have to burn a file into a CD and windows users will be able to see like 5 different versions of all .txt. files inside.. Isn't there some way to clear them?

---

### Post by SeanHodges on 2007-05-17
There are a number of programs that create these backup files. You can remove them in a single directory using the following command while inside the directory:

rm ./~?*

---

