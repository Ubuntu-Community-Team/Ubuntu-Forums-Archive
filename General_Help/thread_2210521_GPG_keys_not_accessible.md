---
title: "GPG keys not accessible?"
date: 2014-03-11
forum: General Help
---

### Post by PDA1 on 2014-03-11
I'm using Ubuntu 10.04

Here's a strange one- I opened Thunderbird yesterday to send an encrypted email. Thunderbird said that the gpg keys are missing or not present or some such stuff.

In Terminal I checked my keys with the command- "gpg --list-keys" and it said there were no keys!

I checked Seahorse and none of my keys were present. Then I checked Seahorse as root and there my keys were!

Then as root again I tried the "gpg --list-keys" and there they were!

So I can't decrypt any of the files (in folders) I have on my machine without being in root. None of my keys appear in Seahorse without being in root. Thunderbird just says none of the keys are present (or something like that). 

What should I do?

---

### Post by Dave_L on 2014-03-11
How did you create the keys? As root, or as your normal user?

---

### Post by PDA1 on 2014-03-11
No idea. It was years ago.

Like I said, the problem just developed yesterday. I've never had this problem before.

I think it has to do something with permissions but I'm certainly not an expert or much knowledgeable about this sort of stuff.

---

### Post by Lars Noodén on 2014-03-11
What are the current permissions and ownerships of .gnupg and its contents?

```

ls -dlh ~/.gnupg/
ls -lh ~/.gnupg/

```

---

### Post by PDA1 on 2014-03-11
> **Lars Noodén said:**
> What are the current permissions and ownerships of .gnupg and its contents?

```

ls -dlh ~/.gnupg/
ls -lh ~/.gnupg/

```


Here are the results;

```
   ~$ ls -dlh ~/.gnupg/ 
 drwx------ 2 Frank Frank 4.0K 2014-03-10 22:24 /home/Frank/.gnupg/ 

 Frank@Frank-desktop:~$ ls -lh ~/.gnupg/ 
 total 244K 
 -rw------- 1 Frank Frank 9.2K 2011-10-25 16:53 gpg.conf 
 -rw------- 1 root  root   84K 2014-03-07 15:13 pubring.gpg 
 -rw------- 1 root  root   84K 2014-03-07 15:13 pubring.gpg~ 
 -rw------- 1 Frank Frank  600 2014-03-10 22:28 random_seed 
 -rw------- 1 Frank Frank 5.1K 2011-11-16 15:27 secring.gpg 
 -rw------- 1 Frank Frank 1.2K 2014-03-07 15:13 trustdb.gpg 
 Frank@Frank-desktop:~$  


```

---

### Post by Lars Noodén on 2014-03-11
Ok.  There's the problem, pubring.gpg is owned by root.  How it got that way is another question.  

You can set it back with chown.

```

sudo chown Frank:Frank ~/.gnupg/pubring*

```

---

### Post by PDA1 on 2014-03-11
Lars....I OWE YOU!!!

Thank you very much for the help!

---

### Post by Lars Noodén on 2014-03-11
No worries.  I do wonder how they got written over as being owned by root.  Did you recently run a graphical program like Seahorse using sudo instead of gksudo?  That might have done it.

---

