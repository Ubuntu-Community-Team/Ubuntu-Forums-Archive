---
title: "How to sync my password and group files?"
date: 2008-04-01
forum: General Help
---

### Post by MountainX on 2008-04-01
I'm setting up NFS. My user and group IDs are not the same on all computers (there are just a handful of computers), all running either Gutsy or Hardy. How do I sync passwords and groups?

If there is some automated way that's easy, I'll do that. But if it isn't easy I could just copy the files or do some other manual step. 

My questions:
1. If I replace the passwd and group files on a computer is there a chance I will get locked out or have some other problem?
2. Where is the actual password stored?
3. What are the exact (newbie) steps for making all machines have the same user and group IDs and passwords?

Thanks

---

### Post by MountainX on 2008-04-01
one hour (**edit** 2 or 3 hours) of googling and I can't seem to find an answer to this simple question.

What search terms should I use besides things like these?
Linux OR Ubuntu nfs password OR passwd sync

I would like to know the details of manually sync'ing all my passwd and group files and the gotchas (before they get me).

I would also like to know the alternatives to manually doing it.

Can I use some sync software (maybe unison?) to keep them all in sync? What is the danger of getting locked out of my computer(s)?

---

### Post by pointone on 2008-04-01
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

### Post by MountainX on 2008-04-01
OpenLDAP is step two for me. For step 1 I am going to manually make sure all users have same UID on all computers. Just want to make sure I don't screw up stuff in the process.

---

