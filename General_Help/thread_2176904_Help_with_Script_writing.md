---
title: "Help with Script writing"
date: 2013-09-26
forum: General Help
---

### Post by rolltide101x on 2013-09-26
I am writing a script that will install a specific Wine application in a specific place and I wanted to know how I tell the script to create a folder in a certain place on any computer no matter what their user name is.

Ex. I want the same script to create
home/john/"wine application folder"     and
home/michael/"wine application folder"    or
home/user_name/"wine application folder"


how do I tell a script to find out the path and then tell it to write a new folder to that path? Thanks!

---

### Post by steeldriver on 2013-09-26
If the script will be run by the user whose home directory is where you want the script to create the folder, then you can use the HOME environment variable e.g.

```
"$HOME/wine application folder"
```

Type 

```
echo $HOME
```

in a terminal to see what the current value is

---

### Post by rolltide101x on 2013-09-26
> **steeldriver said:**
> If the script will be run by the user whose home directory is where you want the script to create the folder, then you can use the HOME environment variable e.g.

```
"$HOME/wine application folder"
```

Type 

```
echo $HOME
```

in a terminal to see what the current value is


Thank you very much! 

```
mkdir $HOME/"wine application folder"
```

worked perfectly!  You are my hero lol

---

