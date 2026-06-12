---
title: "Running a program with a different nice level, but not being root"
date: 2007-09-20
forum: General Help
---

### Post by apethedog on 2007-09-20
I have virtualbox with windows XP on my kubuntu installation, and I like to use it to run paintshop and other assorted windows-only programs inside my linux.

I've set everything up, and it runs well, but a little slow. It seems to use most of my processor power already without me setting a nice level, so this may be more of an academic question than anything else (although I would still like to test it, and see whether or not I notice a difference) but, I'd like to know the following:

Is it possible to set a nice level for a program, but, run it on your regular, non-root account. I've looked into the man pages, but I can't find a way to set a nice level for an already running process, and when I run the program with 

sudo nice virtualbox

I run it as root, and the windows system I had set up doesn't show up, because I'm not logged in as the person who created the thing. (Where I used to select "windows" from the list, and press 'run', it now shows an empty list with no options to select from).

1. Is it possible to nice a running process owned by another user? -or-
2. Is it possible to run something with root priviledges, but, whilst retaining the user ID you sudo'ed from.

Thank you.

---

### Post by tszanon on 2007-09-20
> **apethedog said:**
> I have virtualbox with windows XP on my kubuntu installation, and I like to use it to run paintshop and other assorted windows-only programs inside my linux.

I've set everything up, and it runs well, but a little slow. It seems to use most of my processor power already without me setting a nice level, so this may be more of an academic question than anything else (although I would still like to test it, and see whether or not I notice a difference) but, I'd like to know the following:

Is it possible to set a nice level for a program, but, run it on your regular, non-root account. I've looked into the man pages, but I can't find a way to set a nice level for an already running process, and when I run the program with 

sudo nice virtualbox

I run it as root, and the windows system I had set up doesn't show up, because I'm not logged in as the person who created the thing. (Where I used to select "windows" from the list, and press 'run', it now shows an empty list with no options to select from).

1. Is it possible to nice a running process owned by another user? -or-
2. Is it possible to run something with root priviledges, but, whilst retaining the user ID you sudo'ed from.

Thank you.
renice is the command to give a new priority to a running process. If it's owned by other user, probably you will need to use sudo.
And for your question #2, I don't think it's possible, but I don't know for sure.

---

### Post by apethedog on 2007-09-20
Thanks man. I would surmise that #2 is far too dangerous to exist, but I might be wrong. This answers my question, and problem, nicely.

(BTW, this forum moves *really* fast. I posted this 2 hours ago, and my thread is on the third page. I don't know how you question answering-guys keep up)

---

