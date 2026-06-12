---
title: "Sudo command writing password into commandline instead of getting prompt?"
date: 2006-12-04
forum: General Help
---

### Post by mariyo on 2006-12-04
Hello :)

Is it possible to make a command _like_
*sudo --password=mariyostestpass echo hei;* ?

I try to use PHP at my server to make new subdomains and stuff, but I can't exectute sudo-commands because of the password prompt..

Hope u guys reading this get my point..

Thanks for helping anyway :)

<< - MY FIRST POST - >>

---

### Post by lamego on 2006-12-04
read the sudo manual: 
```
man sudo
man visudo
```
You can setup sudo so that it does not ask for the password when specific commands are run by specific users.
Please use with care.

---

### Post by mariyo on 2006-12-04
thx...

but I don't know what to type..

should I just write under the root-line just the same as root has setting to mariyo istead of root?

I'm a little new t Linux, sorry my stupid questions :neutral:

---

