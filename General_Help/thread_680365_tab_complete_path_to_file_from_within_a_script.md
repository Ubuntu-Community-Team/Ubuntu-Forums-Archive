---
title: "tab complete path to file from within a script"
date: 2008-01-27
forum: General Help
---

### Post by p-stone on 2008-01-27
Hi there
I'm trying to write a script to allow me to burn dvds from the command line
I have it completed and operational, the only issue is when the script asks me to specify the path to the folder or image that I want to burn, I cannot use tab complete, I have to type the full path out manually. Is anyone aware of a way to add tab complete functionality to scripts?
thanks in advance

---

### Post by ryanVickers on 2008-01-27
no, but you could read the first part of the string, create a variable that consists of the "ls" output, aka all possible files, and then say "That's not a complete path, but is this what you meant?" and then the first bit should be enough for it to get what you want ;)

---

