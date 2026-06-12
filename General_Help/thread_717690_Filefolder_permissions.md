---
title: "File/folder permissions"
date: 2008-03-07
forum: General Help
---

### Post by miloske on 2008-03-07
I know few things about linux, but I'm still a noob. This isn't a real problem, it's just something that I've been thinking about.

Let's say that we have one computer (maybe a file server of some kind) with few folder on it that contain thousands of files. Access permissions to that folders are granted to GroupA that contains few hundred users. GroupA has write access to FolderA, but no one else must be able to read files from that folder (660). GroupA also has write access to FolderB, and read-only access to FolderC (440 - FolderC must also be protected from users that are not members of GroupA).

A member of GroupA, User12, has done something bad and now we need to "punish" him. We must prevent him from modifying files in FolderA, we must not interfere with any other permissions, other users must be able to write to FolderA, and User12 must be able to write to FolderB, and have read access to FolderC, and he must have read-only access to FolderA.

I know how this can be done on windows system, you just add his user acc. to ACL and deny modify or write (depending on what you want to do).

Is there a way to do this with linux file permissions (chmod), and how? And what if User12 must be able to write new files in FolderA (we must only prevent him from modifying existing files)?

---

### Post by Front187 on 2008-03-07
Just remove his name from the group that has the priveleges to rwx

---

### Post by murataht on 2008-03-07
same here,

create another GroupX, with the specific read/write access restrictions, and remove the user12 from the GroupA and add it to GroupX. voilà

---

