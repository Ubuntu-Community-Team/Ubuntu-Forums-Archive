---
title: "Customize Default Directories?"
date: 2023-10-26
forum: General Help
---

### Post by blahboybaz on 2023-10-26
[SIZE=2]For the set of directories that come with a base install of Ubuntu 22.04 ([/SIZE][I][SIZE=2]the default directories)..[/SIZE]

[/I]**Is it possible to customize them in any of the following ways such that the result is permanent and persistent, appears all places a default directory or name does, and behaves in all ways a default directory behaves, and in all features that access or incorporate them?**

- Remove a default directory (and from everywhere and way it appears - think of the word "omission" here - as if it had never existed at all)
- Add a default directory (as in - a directory that performs in every way identical as if it had come with the base install - exactly as if it were a default directory)
- Re-order a default directory (eg: make it a sibling of another directory such that the parent or containing directory takes the exact attributes of a default directory as well as its sibling retaining its attributes that a default directory would have.
- Rename a default directory (such that it is deeply renamed down to its core as well as the new name being recognized and displayed in every feature and function that a default directory is integrated into the system (eg: not just renamed on the sidebar of nautilus but show up under the old name on the tab name of nautilus but to in every way be the new name - eg: use the new name in searches and whatever other ways default dirs are incorporated into the system.

[B]Use Case:

[/B]CRUD (create, read, update, delete) directories on an equal level of system incorporation as default directories. Include both user created as well as default directories in the objective.

[B]User Story:

[/B][I]I want to make my directory system my own. There are some directories I wish to COMPLETELY remove, there are some I wish to change the name, and there are some I wish to organize differently. I was to do this at a deep system level (not the same as just crudding new directories but actually changing the existing base system).


[/I]&#8203;

---

### Post by yancek on 2023-10-26
I don't know if I understand exactly what it is you want to do but it seems as if you want to create an entirely new operating system, particularly if you want to rename system directories/files.

---

### Post by tea for one on 2023-10-26
> **yancek said:**
> I don't know if I understand exactly what it is you want to do but it seems as if you want to create an entirely new operating system, particularly if you want to rename system directories/files.
I'm also struggling to understand the objective.

@blahboybaz
Is this any help? [https://www.linuxfromscratch.org/](https://www.linuxfromscratch.org/)

---

### Post by Impavidus on 2023-10-26
Is this about your ~/Documents, ~/Downloads etc. directories? In that case, modify your ~/.config/user-dirs.dirs.

---

### Post by dragonfly41 on 2023-10-26
Idle thoughts are ..
use Cubic to customise your OS to your style
use Ansible and other scripting/automation
use rEFInd to create a custom boot script 
use aliases/links to/from real <-> virtual directories (not deleting default names as you suggest but just another addressing layer)

---

### Post by TheFu on 2023-10-26
You can do anything you like, if you have the time and skill.  Say you want all OS files to be under /OS/, no exceptions.  This is a non-trivial task, but I don't see why someone with sufficient desire couldn't do it. You'll be rebuilding most of the OS and every other file, so if you think there's 1 setting somewhere that will magically control the top level directory and let all packages "just work", you are wrong.  

Now if you just want to change where your HOME directory is located, that's 1 change in 1 place, then moving the HOME to the new location.  There are some programs that will break if you do this.  For example, all snap packages will cease to work.  That could be a "feature" to some.

It won't be easy with any distro to accomplish this. You can try using LFS [https://linuxfromscratch.org/lfs/](https://linuxfromscratch.org/lfs/)

> CRUD (create, read, update, delete) directories on an equal level of system incorporation as default directories. Include both user created as well as default directories in the objective.

Huh? You need to define what equal level means. You need to define what a "system incorporation" is and what you consider "default directories".  I suspect that quoted line is being translated because a native English speaker wouldn't have a sentence constructed that way.

---

