---
title: "Deny Particular Updates"
date: 2006-11-21
forum: General Help
---

### Post by terces on 2006-11-21
I currently have about 30 repositories in my sources.list file.

Unfortunately, there are going to be similar programs in different repositories and sometimes there is an "update" to a program coming from a repository that I don't want to supersede the version of what I currently have.

Is there any way to deny updates on a per basis.  I like it when the notification isn't in the panel so that when it does show I know that there really are new updates that I want to look over.

---

### Post by qamelian on 2006-11-21
> **terces said:**
> I currently have about 30 repositories in my sources.list file.

Unfortunately, there are going to be similar programs in different repositories and sometimes there is an "update" to a program coming from a repository that I don't want to supersede the version of what I currently have.

Is there any way to deny updates on a per basis.  I like it when the notification isn't in the panel so that when it does show I know that there really are new updates that I want to look over.
There is an option in Synaptic under the Package menu that can be used to lock packages to a specific version.

---

### Post by terces on 2006-11-21
My situation is:

say I have XXGGXX version 3... fine

say I want X Y and Z repositories and Z happens to be an unsupported restricted repository that could contain illegal packages... but I want Z for say Flash 9 Beta 2 and stuff like that... but it just so happens that Z also has XXGGXX version 4 and I don't want version 4 to be coming from there - I'd rather wait for it to come from a trusted source like X or Y. 

See, the locking the version doesn't work.  Thanks for the suggestion though.  Any other ideas?

---

### Post by drphilngood on 2006-11-22
You can also just comment out the sources in question when not wishing to use them.
```
gksudo gedit /etc/apt/sources.list
```
then place ## in front of the repos in question.

---

### Post by qamelian on 2006-11-22
> **terces said:**
> My situation is:

say I have XXGGXX version 3... fine

say I want X Y and Z repositories and Z happens to be an unsupported restricted repository that could contain illegal packages... but I want Z for say Flash 9 Beta 2 and stuff like that... but it just so happens that Z also has XXGGXX version 4 and I don't want version 4 to be coming from there - I'd rather wait for it to come from a trusted source like X or Y. 

See, the locking the version doesn't work.  Thanks for the suggestion though.  Any other ideas?
Both of the version 4s though will usually have slightly different package names. When you lock the version, you do it based on the package names. It does work; I do this all the time to prevent certain apps from upgrading to versions I suspect to be less stable. It has never failed to work yet.

---

