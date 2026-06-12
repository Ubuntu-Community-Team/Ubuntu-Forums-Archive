---
title: "some directories owned by regular user not accessible by regular user?"
date: 2024-11-29
forum: General Help
---

### Post by symtexxd on 2024-11-29
I'm having a strange issue where some directories in my home are not accessible by regular user but they are accessible by root?
when I list "ls -lh" as root I can clearly see the owner, group, and permissions are correct. what could be the problem? there are no ACLs and I've disabled apparmor but still no access.

Here is the output
symtex@latlap:~/projects$ ls -lh irules
ls: cannot access 'irules/rules': Permission denied
ls: cannot access 'irules/extensions': Permission denied
ls: cannot access 'irules/macban.zip': Permission denied
ls: cannot access 'irules/version': Permission denied
ls: cannot access 'irules/node_version': Permission denied
ls: cannot access 'irules/macban.tgz': Permission denied
ls: cannot access 'irules/codeshare': Permission denied
total 0
d????????? ? ? ? ?            ? codeshare
d????????? ? ? ? ?            ? extensions
-????????? ? ? ? ?            ? macban.tgz
-????????? ? ? ? ?            ? macban.zip
-????????? ? ? ? ?            ? node_version
d????????? ? ? ? ?            ? rules
-????????? ? ? ? ?            ? version

this is the output as root
symtex@latlap:~/projects$ sudo ls -lh irules
[sudo] password for symtex: 
total 220K
drwxrwxr-x 2 symtex symtex 4.0K May 21  2024 codeshare
drwxrwxr-x 3 symtex symtex 4.0K Nov 14  2023 extensions
-rw-rw-r-- 1 symtex symtex  98K Nov 16  2023 macban.tgz
-rw-rw-r-- 1 symtex symtex  98K May 21  2024 macban.zip
-r--r--r-- 1 symtex symtex    2 Nov 14  2023 node_version
drwxrwxr-x 2 symtex symtex 4.0K Nov 14  2023 rules
-r--r--r-- 1 symtex symtex    9 Nov 14  2023 version

---

### Post by yancek on 2024-11-29
The more common reasons for seeing multiple ?? in the ls output are that the directory they are in does not have execute permissions (run ls -l /home/semtex) or the filesystem or specific files are corrupted.  This is not uncommon and you can find lots of sites discussing it.

 [https://serverfault.com/questions/65616/question-marks-showing-in-ls-of-directory-io-errors-too](https://serverfault.com/questions/65616/question-marks-showing-in-ls-of-directory-io-errors-too)

---

### Post by The Cog on 2024-11-30
yes, let's see the irules directory permissions: **[COLOR="#0000FF"][FONT=Courier New]ls -ld irules[/FONT][/COLOR]**

---

### Post by symtexxd on 2024-11-30
I found out the problem some how the files metadata was corrupted. So I created new copies without preserving metadata this creates new file metadata

$sudo cp -r --no-preserve=all irules scriptirules

Then

$sudo chown -R symtex:symtex scriptirules

I can now edit the files again as regular user.

Thank you guys for your replies
Cheers!

---

