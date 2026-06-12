---
title: "GNOME launcher"
date: 2020-07-23
forum: General Help
---

### Post by anneranch on 2020-07-23
Is it possible to combine / chain commands in "luncher"? 
There are many ways to combine CLI commands, none of them work.
For example "tilda && ls " should execute "ls" after "tilda" successfully returns

---

### Post by ActionParsnip on 2020-07-23
It'll read your ~/.bashrc file so if you add the command to the end of the file it'll run

---

### Post by ActionParsnip on 2020-07-23
Or try making the launcher run:
```

tilda newtab --in mainwindow ls

```

---

### Post by anneranch on 2020-07-23
Pardon my ignorance 

how does "tidla" reads "newtab"  ?
It dose not even when started via launcher by putting tilda in command line. 

"New Tab" is a menu text and the only text / keyboards recognized are standard Linux, such as "ls".

I  have several bashrc files and not sure which one to edit. But I'll try that.

---

### Post by anneranch on 2020-07-23
OK, I feel very uncomfortable doing this .

After starting tilda I type after prompt  edit ./.bashrc  
I have never used "edit" before. 

I got into bashrc file and there is nothing even remotely related to gnome launcher in it 
I could not figure out  how to exit the file so I closed the tilda.

---

