---
title: "I need help creating a launcher"
date: 2008-01-31
forum: General Help
---

### Post by onesojourner on 2008-01-31
I nedd to run to commands in terminal. I need to cd into a directory and then I need to run the program.

```
cd xwii
```

then

```
./xwii profiles/classic
```

---

### Post by jan quark on 2008-01-31
hm dont get me wrong but I dont exavtly understand you

try this

right click on the panel> then add to panel > search something like custom application launcher > under command browse to the specific file you want to run

hope that helps

---

### Post by dannyboy79 on 2008-01-31
> **onesojourner said:**
> I nedd to run to commands in terminal. I need to cd into a directory and then I need to run the program.

```
cd xwii
```

```
./xwii profiles/classic
```
the custom command would be this when you create the launcher like the guy above states:
cd ~/xwii && ./xwii profiles/classic

that should work.

---

### Post by onesojourner on 2008-01-31
thanks dannyboy79. Thats what I needed.

---

### Post by dannyboy79 on 2008-01-31
you're welcome, if there's a launcher where you need a whole mess of commands to do something, then you would just create a bash script and in the lanucher, you just call for the bash script to run. make sure to make the script executable. sudo chmod +x script

---

### Post by onesojourner on 2008-01-31
ok I had a problem. I created the Launcher but I get this error when I try to launch it.

There was an error creating the child process for this terminal

---

### Post by onesojourner on 2008-01-31
The code I need to run is this
```
cd ~/xwii && ./xwii profiles/classic.xwii

```

It works fine when I run it in terminal but when I try to creat a launcher I set it as runn application in terminal, But I get the above error.

---

