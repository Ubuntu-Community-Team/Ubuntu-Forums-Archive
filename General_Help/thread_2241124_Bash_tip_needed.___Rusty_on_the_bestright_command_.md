---
title: "Bash tip needed.   Rusty on the best/right command to see the root directory."
date: 2014-08-24
forum: General Help
---

### Post by Timmoore001 on 2014-08-24
I'm using Ubuntu 12.04 and when I go into the CLI, I get into the Home directory but I think I need to be at the top level.

What commands do I need to do this ?

A forgetful ,

Tim

---

### Post by Lars Noodén on 2014-08-24
Do you mean using **cd** to change directories?

cd ..  moves you up a directory (if it can) relative to your current directory
cd ~  moves you to your home
cd ~*user*  moves you to *user*'s home
cd -  moves you to the previous directory

Then there are also pushd / popd to remember where you once were.

---

### Post by dradius on 2014-08-24
> **Timmoore001 said:**
> I'm using Ubuntu 12.04 and when I go into the CLI, I get into the Home directory but I think I need to be at the top level.

What commands do I need to do this ?

A forgetful ,

Tim

To change directories you cd just like in dos/windows.  To get to the "top" directory you would do cd /

---

### Post by Timmoore001 on 2014-08-24
Many thanks . that is a great help !

now do I need su or sudo or something to see the admin directories ?

Many thanks again to those who responded !

A happier,

Tim

---

### Post by Lars Noodén on 2014-08-24
Which directories?  You can read most directories as a regular user.  Some, like the log files, are available to members of specific groups.  If you are the first user on the machine, you are already added to those groups.  Other than that, it depends on the directory.

---

### Post by Timmoore001 on 2014-08-24
/bin/ would be a start !

:  )

Tim

---

### Post by Bashing-om on 2014-08-24
Timmoore001l Hi !

To "see' the listing of - for instance "bin'" a directory, a simple:
```

ls -al /bin

```
Will do that .
Where the path is '/' the root directory, and right under '/' is 'bin' -> /bin !
See:
```

man ls

``` for the many options to the "list" command.

[INDENT][INDENT]my little bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Timmoore001 on 2014-08-24
near what I was looking for.

at the top of the tree there are loads of directories such as /bin/ also /usr/ and many more.

I was hoping to move from 'home' which is under /usr/ to the very top.

Hope that makes sense ?

Many many thanks for responding.

:  )))

Tim

---

### Post by nerdtron on 2014-08-24
>  I was hoping to move from 'home' which is under /usr/ to the very top. 

Can you re-phrase this sentence, it's seems a little confusing on what you want to do.

---

### Post by Bashing-om on 2014-08-24
Timmoore001; OK ;

To 'go' to the top of the directory tree:
```

cd /

```

To 'see" what is there:
```

ls -al

```
To lookee deeper
```

ls -al /etc

``` for example

To return to the resting place "/home"
```

cd

```

Your default prompt should always tell you where you are in the tree, else:
```

pwd

```
will tell you your location.

[INDENT][INDENT][INDENT]that process of learning
[/INDENT][/INDENT][/INDENT]

---

### Post by Timmoore001 on 2014-08-24
Many thanks all !

That seems to have fixed it.

:  )))

Tim

---

