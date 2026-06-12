---
title: "[SOLVED] Subversion commit not working"
date: 2008-01-20
forum: General Help
---

### Post by tenjin on 2008-01-20
Hi,

I've had Subversion running under svnserve for ages. The latest set of Ubuntu updates seems to have broken something.

Permissions in the repository folder were broken, and after I reset them to svn:svn everything seemed to start working again.

However, whenever I try to check something in I get this error message:

"Commit failed (details follow):

Can't read from connection: An existing connection was forcibly closed by the remote host."

Any ideas what might be causing this? I have reinstalled subversion but it didn't make any difference.

FYI, I am running SVN on Gutsy. On the client side I have a Windows XP machine running TortoiseSVN, and a Macbook Pro running SynchroSVN. Both exhibit the same problem.

Cheers

D.

---

### Post by tenjin on 2008-01-21
* bump *

Any ideas?

Cheers

D.

---

### Post by geirha on 2008-01-21
Try killing svnserve, then start it with ```
svnserve -d --foreground
``` and see if it spits out any messages on the server-side when the client tries a commit...

---

### Post by tenjin on 2008-01-21
Hi,

Thanks for the tip. I tried that but there was no output to the console on the server.

Cheers

D.

---

### Post by tenjin on 2008-01-21
Hi,

This evening I created a test repository and successfully imported, checked out, changed, and committed some files.

So, this suggests that there is a problem with my original repository.

Looking at the two folder structures I see the following differences:

/drive2/svnsafe/conf (original archive) contains:

total 8
-rwxr-xr-x 1 svn svn   43 2008-01-19 23:57 passwd
-rwxr-xr-x 1 svn svn 1353 2008-01-20 00:23 svnserve.conf

While /drive2/svn (test archive) contains:

total 12
-rwxr-xr-x 1 svn svn  684 2008-01-21 23:41 authz
-rwxr-xr-x 1 svn svn  344 2008-01-21 23:46 passwd
-rwxr-xr-x 1 svn svn 1456 2008-01-21 23:47 svnserve.conf


DB FOLDER

/drive2/svnsafe/db (original archive) contains:

total 4255900
-rwxr-xr-x 1 svn svn    3780608 2008-01-16 09:14 changes
-rwxr-xr-x 1 svn svn       8192 2007-08-11 12:39 copies
-rw-r--r-- 1 svn svn      24576 2008-01-21 19:22 __db.001
-rw-r--r-- 1 svn svn     180224 2008-01-21 19:22 __db.002
-rw-r--r-- 1 svn svn     270336 2008-01-21 19:22 __db.003
-rw-r--r-- 1 svn svn     327680 2008-01-21 19:22 __db.004
-rw-r--r-- 1 svn svn     712704 2008-01-21 19:22 __db.005
-rw-r--r-- 1 svn svn      16384 2008-01-21 19:22 __db.006
-rwxr-xr-x 1 svn svn       1738 2005-11-04 22:47 DB_CONFIG
-rwxr-xr-x 1 svn svn        150 2008-01-21 19:22 __db.register
-rwxr-xr-x 1 svn svn          2 2005-12-05 21:45 format
-rwxr-xr-x 1 svn svn          4 2005-11-04 22:34 fs-type
-rwxr-xr-x 1 svn svn       8192 2006-09-16 19:56 locks
-rwxr-xr-x 1 svn svn       8192 2006-09-16 19:56 lock-tokens
-rwxr-xr-x 1 svn svn    1048576 2008-01-19 12:14 log.0000019629
-rw-r--r-- 1 svn svn    1048576 2008-01-20 19:20 log.0000019630
-rwxr-xr-x 1 svn svn    2633728 2008-01-16 09:14 nodes
-rwxr-xr-x 1 svn svn    6017024 2008-01-16 09:14 representations
-rwxr-xr-x 1 svn svn      20480 2008-01-16 09:14 revisions
-rwxr-xr-x 1 svn svn 4339163136 2008-01-16 09:14 strings
-rwxr-xr-x 1 svn svn     147456 2008-01-16 09:14 transactions
-rwxr-xr-x 1 svn svn       8192 2006-09-16 19:56 uuids

While /drive2/svn/db (test archive) contains:

total 28
-rwxr-xr-x 1 svn svn    7 2008-01-21 23:51 current
-rwxr-xr-x 1 svn svn    2 2008-01-21 23:41 format
-rwxr-xr-x 1 svn svn    5 2008-01-21 23:41 fs-type
drwxr-xr-x 2 svn svn 4096 2008-01-21 23:51 revprops
drwxr-xr-x 2 svn svn 4096 2008-01-21 23:51 revs
drwxr-xr-x 2 svn svn 4096 2008-01-21 23:51 transactions
-rwxr-xr-x 1 svn svn   37 2008-01-21 23:41 uuid
-rwxr-xr-x 1 svn svn    0 2008-01-21 23:41 write-lock


Can I assume from this that the version of SVN on my Ubuntu box has changed, and that the old repository format is not supported? BOTH archives were created on Ubuntu using:

svnadmin create <path/repository>

- but the original one on a WAY earlier version of Ubuntu.

If so, can I migrate my old repository to the new format?

Cheers

D.

---

### Post by tenjin on 2008-01-21
On reflection I think the original repository might have been a migration from CVS.

Would that account for the differences?

Cheers

D.

---

### Post by geirha on 2008-01-22
What version of svn do you have now? That the repository hierarchy changed between two versions sounds plausible to me. And a possible fix could indeed be a migration as you mentioned. Try dumping your old repository and load it into your test repository. [http://svnbook.red-bean.com/nightly/en/svn.reposadmin.maint.html#svn.reposadmin.maint.migrate](http://svnbook.red-bean.com/nightly/en/svn.reposadmin.maint.html#svn.reposadmin.maint.migrate)

As for the migration from cvs, I think the repository would look the same whether you created a new one or migrated from cvs.

[quote=svn_red-book]There are many reasons for dumping and loading Subversion repository data. Early in Subversion's life, the most common reason was due to the evolution of Subversion itself. As Subversion matured, there were times when changes made to the back-end database schema caused compatibility issues with previous versions of the repository, so users had to dump their repository data using the previous version of Subversion, and load it into a freshly created repository with the new version of Subversion. Now, these types of schema changes haven't occurred since Subversion's 1.0 release, and the Subversion developers promise not to force users to dump and load their repositories when upgrading between minor versions (such as from 1.3 to 1.4) of Subversion.[/quote]

---

### Post by tenjin on 2008-01-25
Hi,

That was it, thanks.

I dumped my old respository and then loaded it into the new one.

Everything works fine now.

BTW, the repository dump took about 8 hours for an 8Gb repository with 500+ revisions. Does that sound right, or indicative of other problems?

Cheers

D.

---

### Post by geirha on 2008-01-25
I have no idea how much time it should take, though I imagine a lot of processing is involved, so 8 hours don't surprise me, at least not for such a large repository. And whatever time it takes, as long as it completes successfully, I'd say there's no problems.

Oh, and please [mark the thread as solved](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) so that others with similar problems may find this thread a little easier.

---

