---
title: "[SOLVED] Stop OpenOffice from auto installing after removal"
date: 2007-11-24
forum: General Help
---

### Post by gmaniac on 2007-11-24
I have Openoffice removed but now I want, through "language support", to add some other languages. The thing is that it starts to download openoffice, through some dependencies. 
The question is if there is a way to mark Openoffice as taboo(like yast) so it never installs?
thnx.

---

### Post by Forlong on 2007-11-24
That's possible through Synaptic. Choose *Package &#8594; Lock Version*

**But** then you won't be able to install packages that have this as a dependency. In other words: that won't help you.
You will have to install the language packages (you want to install) yourself - *Language Support* assumes you're on a standard install of Ubuntu.

---

### Post by gmaniac on 2007-11-24
Hooray... It worked. :)
As i now found out after pining, by checking the english support( which was marked with a **"-"** ) the installation of openoffice was starting.
I installed my other languages just fine! 

Although i can't understand two things.
1. Why is a massive download/app like this is a dependency for ubuntu
2. How could Pinning to a version and not wanting to install be one option.

Thanks again.

---

### Post by Forlong on 2007-11-24
Great. :)

> **gmaniac said:**
> 1. Why is a massive download/app like this is a dependency for ubuntu
Like I said, it is only when installing language support via that menu, because OOo is installed by default.
Or do you mean why is it installed by default in the first place?
> **gmaniac said:**
> 2. How could Pinning to a version and not wanting to install be one option.
Well, look at it this way: it's like saying »stay the way you are«.
If it's not installed, it remains "unininstalled" - if it is installed, it won't change to another version.

---

### Post by gmaniac on 2007-11-24
Technically I understand why it installs itself through the dependencies but i can't comprehend why it's is a dependency for ubuntu-desktop in the first place (i consider it bloated for my needs).
But since I got my way and learned how to stop this I don't care if they decide
to have a dependency for Microsoft Office now ;) .
thnx again.

---

### Post by Forlong on 2007-11-24
> **gmaniac said:**
> Technically I understand why it installs itself through the dependencies but i can't comprehend why it's is a dependency for ubuntu-desktop in the first place (i consider it bloated for my needs).
You are right in my opinion as well.
I wish there was an option in the install process where you can choose which software you want (Ekiga comes to mind too - never used it and probably never will).
I don't think most people use *all* of OOo's components, most notably Calc and Base.

But I guess Ubuntu wants to make sure you're seeing most of Linux' potential by default...

---

