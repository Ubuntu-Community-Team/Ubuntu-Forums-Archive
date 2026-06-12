---
title: "All terminal programmes now default to the / directory instead of home"
date: 2006-10-22
forum: General Help
---

### Post by mcpish on 2006-10-22
I think I accidently deleted some kind of config file or something.

No matter what terminal programme I use now, when I open it up it always defaults me to the / directory rather than the ~/ directory (home directory of whatever user is logged in).  This only started in the last week or so.  

I'm sure it's something simple but i have no clue what to edit to make it return to the old behavior of defaulting to the home directory.

---

### Post by bsussman on 2006-10-22
What happens when you type:

```
you@yoursys:~$ cd
you@yoursys:~$ pwd
/home/you

```If you do not get something similar, I imagine the env variables are screwed up.

at a cmd prompt, type:

```
bos@Dillon:~$ env|grep HOME
```to verity that it is the HOME env variable that is getting screwed up.

I imagine you want to look at ~/.bash_profile or ~/.bashrc

Next try would be /etc/bash.bashrc - this is where system wide settings are kept for bash login shells.

Your passwd record could be screwed up as well.

Type:
```
bos@Dillon:~$ grep bos /etc/passwd
```replacing 'bos' with your login.
note that the 6th field is your home dir.  Izzit correct?

Add a new user.  Do they have the same problem?

---

### Post by mcpish on 2006-10-22
All of those tests seem to check out fine.  Yet I still have the problem.  weird.  Oh well I'm going to install Edgy Eft when it's released anyhow so that'll probably fix it in any case.

---

