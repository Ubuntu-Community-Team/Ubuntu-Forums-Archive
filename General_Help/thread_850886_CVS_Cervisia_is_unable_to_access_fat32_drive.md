---
title: "CVS Cervisia is unable to access fat32 drive"
date: 2008-07-06
forum: General Help
---

### Post by Miikee on 2008-07-06
I'm not sure if this is the correct place for this question.  But..  I've been trying for a couple of days to get CVS Cervisia to work with some already existing php, html, etc files.

The files are all located on a shared fat32 drive.  And because of this all the files are under root : plugdev ownership. I am trying to create the cvsroot repository at this directory on the shared drive.  Each time I try though I get a Warning about changing chmod permissions.  But when I check the directory where I tried to create the repository there is a folder named 'cvsroot' created.

But when I goto Cervisia, I can't bring up the repository or any files.

I'm wondering what user I need to add to the group 'plugdev' to give CVS Cervisia permission.  So far I have added my personal username('miikee' and apache('www-data') to group 'plugdev'.
Or, is this not even the problem?  Am I skipping a step?  

Thank you for your help, I appreciate it.

---

### Post by Miikee on 2008-07-06
when i try to create a new repository, I get the error:

mkdir -p '/share/My_Documents/Projects/Web/MiikeeOrg/Postiki' && cvs -f -d '/share/My_Documents/Projects/Web/MiikeeOrg/Postiki' init
cvs init: warning: cannot chmod .#14692: Operation not permitted
cvs init: warning: cannot chmod .#14693: Operation not permitted
cvs init: warning: cannot chmod .#14694: Operation not permitted
cvs init: warning: cannot chmod .#14696: Operation not permitted
cvs init: warning: cannot chmod .#14697: Operation not permitted
cvs init: warning: cannot chmod .#14698: Operation not permitted
cvs init: warning: cannot chmod .#14699: Operation not permitted
cvs init: warning: cannot chmod .#14700: Operation not permitted
cvs init: warning: cannot chmod .#14701: Operation not permitted
cvs init: warning: cannot chmod .#14702: Operation not permitted
cvs init: warning: cannot chmod .#14703: Operation not permitted
cvs init: warning: cannot chmod .#14705: Operation not permitted
cvs init: warning: cannot chmod .#14706: Operation not permitted
cvs init: warning: cannot chmod .#14707: Operation not permitted
cvs init: warning: cannot chmod .#14709: Operation not permitted
[Finished]

please help, I have been searching and reading irrelevent information about this for days.  I just can't seem to search the right phrase or I'm missing something that everyone else gets.    

Thank you for your help.

---

