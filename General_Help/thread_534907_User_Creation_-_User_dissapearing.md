---
title: "User Creation - User dissapearing"
date: 2007-08-25
forum: General Help
---

### Post by kaylus on 2007-08-25
I was in the process of creating user accounts for my children and for when my parents come over to use the computer. I created a guest account for them, created one named after my first daughter, then one after my second. As soon as the first daughter tried to log in it said invalid password, which it wasn't I am sure.

I decided I may have fat-fingered it and tried again, no luck. I logged in and went to System->Administration->Users and Groups and her account was missing! I created again and then tried to log in, it kept saying invalid password/user combo and when I went to check again, her account is missing!

I tried logging into my youngest daughters account, the one I created third, no problem! I tried logging in as the guest account, no problem! I went to check /etc/passwd and there is no entry for the account that dissapeared. What is the problem here? I've created it 4 times and it keeps dissapearing. 

-Confused-

---

### Post by Happy_Man on 2007-08-25
Try a different name, perhaps a nickname? Maybe that is screwing it up somehow....

---

### Post by kaylus on 2007-08-25
While this solution works, it does not work as I would want it to. I don't want to "patch" it with a different name, it's something easy for the child to remember along with her password and I don't want to have to switch up the other daughters as well once one gets a "handle"/"alias".

Regardless of my own personal opinions on the matter, even if I did create a user under a different name, it doesn't explain the issues I'm having and I am definitely of the mind not to be stuck with issues such as dissapearing users on my computers. Does anybody have any ideas of what I could look through to try to resolve this?

It's been so long since I've been shell-surfing on the user management side.

---

### Post by kaylus on 2007-08-26
Note: For a hackish kind of fix it appears that using "useradd" from the shell/command line works fine. I still set the permissions in the GUI user/group editor, but now I have a workable account. I've lost the ability to recreate the error now, but hopefully the next time it crops up more information can be gathered to see why it's actually happening. This is one of those things that could be a big annoyance to the end user.

---

### Post by K.Mandla on 2007-08-26
That would be worthy of a bug report. ... By the way, did you look for any pre-existing bug reports along those lines? It might be that someone reported the problem, and a workaround was found (it'll probably be adduser, though ;) ).

---

