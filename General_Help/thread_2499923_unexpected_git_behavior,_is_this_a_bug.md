---
title: "unexpected git behavior, is this a bug?"
date: 2024-08-15
forum: General Help
---

### Post by sandy-lcq on 2024-08-15
Refer following links, from git v2.35.2, upstream stop Git from  accepting top-level directories owned by someone other than the current
user. If you wish to make an exception to this behavior, you can use the  new multi-valued safe.directory configuration. The `safe.directory`
config setting is only respected in the system and global configs, not  from repository configs or via the command-line, and can have multiple
values to allow for multiple shared repositories.

[1] [https://github.blog/open-source/git/git-security-vulnerability-announced](https://github.blog/open-source/git/git-security-vulnerability-announced)
[2] [https://github.com/git/git/commit/8959555cee7ec045958f9b6dd62e541affb7e7d9](https://github.com/git/git/commit/8959555cee7ec045958f9b6dd62e541affb7e7d9)
[3] [https://github.com/git/git/commit/0f85c4a30b072a26d74af8bbf63cc8f6a5dfc1b8](https://github.com/git/git/commit/0f85c4a30b072a26d74af8bbf63cc8f6a5dfc1b8)
[4] [https://github.com/git/git/commit/313eec177ad010048b399d6fd14de871b517f7e3](https://github.com/git/git/commit/313eec177ad010048b399d6fd14de871b517f7e3)

But on ubuntu24.04, with git version 2.43.0,  the behavior is different.


sandy@pghost:/tmp/test1$ ls -l /tmp/test
total 0
-rw-rw-r-- 1 test_ubuntu test_ubuntu 0 Aug 15 18:37 README
sandy@pghost:/tmp/test1$ git version
git version 2.43.0
sandy@pghost:/tmp/test1$ git ls-remote /tmp/test
0d824c175db86d9d33ca2f38b24a89d342f3ac58        HEAD
0d824c175db86d9d33ca2f38b24a89d342f3ac58        refs/heads/master
sandy@pghost:/tmp/test1$ GIT_TEST_ASSUME_DIFFERENT_OWNER=1 git ls-remote /tmp/test
0d824c175db86d9d33ca2f38b24a89d342f3ac58        HEAD
0d824c175db86d9d33ca2f38b24a89d342f3ac58        refs/heads/master

Expected behavior:
fatal: detected dubious ownership in repository at '/tmp/test/.git'
To add an exception for this directory, call:

        git config --global --add safe.directory /tmp/test/.git
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

I also tried set GIT_TEST_ASSUME_DIFFERENT_OWNER=1,  the same result.  

I am wondering is this a bug ?  Since this will make fix for CVE-2022-24765 not works.

Thanks
Sandy

---

### Post by sandy-lcq on 2024-08-15
But,   cd /tmp/test/;  git pull; will report the "fatal: detected dubious ownership".

---

