---
title: "particulars about the .gvfs entry"
date: 2018-11-17
forum: General Help
---

### Post by Skaperen on 2018-11-17
i do know that the .gvfs directory entry i related to the Gnome Virtual File System. i have questions about it, mostly the directory entry itself.  it shows up in ls with many question marks and no information except it name and that it is a directory, information it can get from reading its entry in the parent (user home) directory.  the stat() or lstat() syscall fails for it, which probably explains all those question marks in the output line for it. particularly odd is that there is no inode which is also substituted with a question mark in the ls output (it could get this from the directory entry, but maybe it has an invalid value like maybe -1. 

1. why does Gnome need this?
2. what program creates this?  is it part of Gnome or something else?
3. what kernel syscall is used to create this?
4. does the kernel syscall need root permission or can an ordinary user do it?
5. i have read that userspace filesystems are mounted in this directory ... so why can't it be an ordinary directory entry?
6. will it appear different when a virtual filesystem is mounted there?
7. i have read that root cannot access this, which may be appropriate, but the user can't, either.  why is that?

---

### Post by TheFu on 2018-11-18
Google found this: [https://wiki.gnome.org/Projects/gvfs/doc](https://wiki.gnome.org/Projects/gvfs/doc)

Please realize that you can avoid using GVFS by manually mounting storage - i.e. don't use a GUI for the initial access.  After the manual mount, or fstab or autofs, then using a GUI is 100% fine.

---

### Post by Skaperen on 2018-11-19
that document didn't really answer my questions.  i have been reading more that i have since found and been trying a few things.

1.  how is it that the Gnome project got involved in virtual file systems?  is it the case that Gnome needed it and since things to support virtual file systems had not been done, they decided to do it.  how is it that i am seeing the effect of this as a Unity user?  is it the case that Unity uses enough of Gnome that the virtual file system stuff comes into play?  or it it the case that virtual file system stuff was included in Ubuntu and this was the best way to include it?

2.  i am wanting to know what program does this to perhaps understand why this gets set up for some users and not others and why the set of users changes.

3. i still have not gotten any lead on what kernel syscall creates the .gvfs entry in the user home directory.

4. knowing what syscall it is should probably tell me how it is called.  one aspect of this that i have read about is that root should not have permission to access filesystems that a user mounts.  to achieve this, the syscall should be callable by an ordinary user or else the security is flawed.

5. the answer to this is that the purpose is to not give root permission to access a filesystem mounted this way.  however, it is my opinion that this is at least a poor, and like a wrong, way to achieve this.

6. i do not have test case to answer this.  i have not encountered any examples that go this far.

7. my test of this was in error or something changed for me.  i first ran into this a couple years ago trying to scan all my files on my primary user that i do development on.  so back then it was the case that a user could not access the .gvfs in their home directory.  but this user no longer has a .gvfs entry.  since then, i found another user that does (and this user may have had it all along).  this user can access their .gvfs entry and see that it is empty.  and root cannot access it.

for comparison, i set up a directory in one user's home that could not be accessed by other users.  trying to access it from another user failed as expected, but the stat() syscall succeeded.  for the .gvfs entry the stat() syscall fails and that is what i think is wrong about that.

incidentally, IMHO, not allowing root to have access is incorrect.  but even assuming that it is correct, the way this is is done is wrong and is causing breakage for many other programs, such as backup programs that depend on POSIX correct behavior.

---

### Post by Skaperen on 2018-11-19
> **TheFu said:**
> Please realize that you can avoid using GVFS by manually mounting storage - i.e. don't use a GUI for the initial access.  After the manual mount, or fstab or autofs, then using a GUI is 100% fine.

i'm not mounting anything.  it's not a case of using GVFS. it is a case of the .gvfs entry in the home directory of some users causing problems.  it appears to be incorrect semantics used to prevent root from accessing user mounted file systems.

---

