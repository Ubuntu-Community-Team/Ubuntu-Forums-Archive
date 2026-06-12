---
title: "Linux Commands"
date: 2013-01-08
forum: General Help
---

### Post by kaushikgaurav on 2013-01-08
Hello All,

I am trying to learn basic linux commands and would really appreciate your help on this one.

I am trying to make directory/folder which has more folders in it.

I want to name my Folder 2013, then it contains a folder names Volume 18 and further that folder "Volume 18" should contain folders "Issue 1, Issue 2, Issue 3....Issue 6"

Can some one help me with how to use mkdir command in simplest way.
maybe in one line, The issue I am facing are:

1) I do not know how to make nested folders with mkdir
2) How do I get mkdir to name folders with space in the name (Volume 18)

Please help

Sincerely,
Gaurav

---

### Post by jerome1232 on 2013-01-08
something like this would create "2013" in the present working directory if it doesn't exist, "Volume 18" below that, then the folders "Issue 1" through "Issue 6" below that. Adjust the number in blue as needed.

```
mkdir -p 2013/Volume\ 18/Issue\ {1..[COLOR="RoyalBlue"]6[/COLOR]}
```


edit: -p makes mkdir create parent directories if they don't already exist.
Using a backslash will escape the next character entered, and is a way to allow spaces in names (ie... My\ folder = "My folder")
The last bit with the curly braces is using shell expansion, I don't know much about how it works so I can't sufficiently explain it. Maybe someone with more bash guru than I can.

---

### Post by kaushikgaurav on 2013-01-08
Thanks that was helpful,
Yes, I am aware of shell expansion as I am reading them now.

Detailed explanation of shell expansion is provided here:
[http://linuxcommand.org/lc3_lts0080.php]("http://linuxcommand.org/lc3_lts0080.php")

---

