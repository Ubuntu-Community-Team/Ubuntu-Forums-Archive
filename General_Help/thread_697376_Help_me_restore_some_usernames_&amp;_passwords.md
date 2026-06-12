---
title: "Help me restore some usernames &amp; passwords"
date: 2008-02-15
forum: General Help
---

### Post by ppcw on 2008-02-15
Hi

I have a Debian Sarge 3.1 server , don't know if its the right place to ask here but here you go. 

The HDD crashed a week ago. 

I had some password protected directory with 100+ users that had access to that folder with a username and a password. 

Somehow, I've managed to save that file that contains the usernames and passwords , can't remember where I took it from then but I've used WinSCP to browse the server. 

Now I got the file , the server is back with the same structure but I don't know where to put the file back so the users can keep their old usernames and passwords. 

Any tips ? :)

---

### Post by seventhc on 2008-02-15
wouldn't you want to put each user back into their own directory???
like if mine was /john and it was lost, but you recaptured it. Shouldn't it go back to /john ???
or am I missing something?
 Nobody here will hack for you, if you are an admin, and you have the files, you should know what to do.
Sorry if I seem crass, but...if you can't fix this, why are you an admin???

---

### Post by lloyd_b on 2008-02-15
> **ppcw said:**
> Hi

I have a Debian Sarge 3.1 server , don't know if its the right place to ask here but here you go. 

The HDD crashed a week ago. 

I had some password protected directory with 100+ users that had access to that folder with a username and a password. 

Somehow, I've managed to save that file that contains the usernames and passwords , can't remember where I took it from then but I've used WinSCP to browse the server. 

Now I got the file , the server is back with the same structure but I don't know where to put the file back so the users can keep their old usernames and passwords. 

Any tips ? :)

FYI - there *isn't* any single file that contains all of the information required to recreate the users.  The "passwd" file contains the usernames, groups, etc, but the hash of the passwords is stored in the "shadow" file.  Then there's the "groups" file, which defines what the different groups are.  

Depending on exactly what that file is (it might help us if you told us its name or provided some sample data from it...), you might be able to extract *some* of the info you require from it, and feed it through a script (using the "adduser" command) to do some of the work required to restore your users.

But there is no "copy back one file and we're done" solution to this problem.

Lloyd B.

P.S.  I trust that you now understand the importance of backups?

---

### Post by seventhc on 2008-02-15
Basckup's rock :guitar:
Sorry if I sounded a  bit off, but whenever I see  p/w question, I question the question. No harm intended.

---

