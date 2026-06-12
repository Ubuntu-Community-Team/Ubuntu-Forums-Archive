---
title: "Uuntu packages not found: what gives?"
date: 2007-06-10
forum: General Help
---

### Post by malibu on 2007-06-10
I've run into this before, and it's getting a bit frustrating.  Specifically, I am trying to install Gallery 2 on Feisty.  I found some instructions which indicate to run an 'apt-get install gallery2'.  Cool.. Should be easy.  But when I try it I get 'package not found'.  I try 'apt-get update' and then the install again with the same result.  Finally I go to the Ubuntu packages page which lists 'gallery2' as a valid package.  Can anyone tell me what might be happening here?  I haven't done anything funny with my aptitude config at all.  It's a basic PHP-MySql server install.

---

### Post by Nythain on 2007-06-10
did you enable universe and multiverse repo's in your /etc/apt/sources.list

---

### Post by Eric_Jardas on 2007-06-10
[https://help.ubuntu.com/community/MythTV/Install/Live/Feisty/Repositories?highlight=%28repositories%29](https://help.ubuntu.com/community/MythTV/Install/Live/Feisty/Repositories?highlight=%28repositories%29)

---

### Post by malibu on 2007-06-10
No.. What is that?

Thank you, that's what it was.  What is the purpose of not allowing all the packages by default?  It is alittle counter-intuitive.

---

### Post by cookies on 2007-06-10
> **malibu said:**
> No.. What is that?

Thank you, that's what it was.  **What is the purpose of not allowing all the packages by default?  It is alittle counter-intuitive**.

Quite simply, copyright issues. Canonical doesn't want to get sued over including some things, so by default Ubuntu leaves certain packages unavailable until you enable them.

---

