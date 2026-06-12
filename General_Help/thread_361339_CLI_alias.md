---
title: "CLI alias"
date: 2007-02-14
forum: General Help
---

### Post by fearevilleet on 2007-02-14
Hello,

How do I make a cli alias. For example every time I run songbird I need to type in 

cd Songbird
./Songbird

How could I make an alias so I can just type in songbird and run the commands. I tried searching on the fourms and google but was unable to find anything that was helpful.

---

### Post by taurus on 2007-02-14
Just add Songbird to your path and you can run it anywhere without changing to it or using the full path.  

```
gedit ~/.bashrc
```
And add these two lines to it.

```
PATH=$PATH:~/Songbird
export PATH
```
Either log out or back in or run

```
source ~/.bashrc
Songbird
```

---

### Post by LotsOfPhil on 2007-02-14
Or, to make an alias
```

cd
vi .bashrc

```
And add,
```

alias songbird="~/Songbird/songbird"

```
Then,
```

cd
source .bashrc

```

---

### Post by fearevilleet on 2007-02-14
Now when I do a songbird alias I receive

songbird
-bash: /home/evilleet/Songbird/songbird: No such file or directory

Dont I have to tell it to run songbird by using ./ ?

---

### Post by LotsOfPhil on 2007-02-14
Oops, that is a typo on my part. If you look back in the alias, it should be:
alias songbird="~/Songbird/Songbird"

Note the capital S in the second Songbird, that's the change. Other than that, make sure the path (/home/evilleet/Songbird/songbird) is right and it will work.

**No.** You do not have to type ./songbird

---

