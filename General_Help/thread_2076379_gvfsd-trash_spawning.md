---
title: "gvfsd-trash spawning"
date: 2012-10-25
forum: General Help
---

### Post by Ego-X on 2012-10-25
Looking in task manager right now there are 16 gvfsd-trash processes running using over 60MBs of memory.

Does anybody know what is this process is? and if it shouldn't be spawning, how can I stop it?

---

### Post by hwttdz on 2012-10-25
First what I'm suggesting might be risky, that said it worked for me.

It's gnome virtual filesystem.  I believe that the trash one makes the "trash" folder behave specially.  I also ran into issues with this (I think due to having autofs mount numerous drives through sshfs in fuse), anyways this confuzed gvfs-trash, so I ended up taking away its execute permissions and now I manage the trash myself (I don't really use the trash much in the conventional sense). 

So, taking away the execute bit will cause it to not run, however it may have side effects, but it doesn't cause any annoying side effects to me.

I see you're a newbie.  I read a well formulated question and figured you'd been around the block for a few times. 
Execute bit - when you do "ls -l" in a directory you will see the permissions of each file/directory, generally in the form of
drwxrwxrwx, the d or lack thereof identifies directories, the first rwx is read/write/execute for the file owner, the second is for the group owner, the third is for everyone else.  If a bit is not set it appears as a dash, so a file which only I can read and write and no one else can access is
-rw-------
changing permissions bits is done with the chmod command (change mode I believe).

To take away permissions you can do "chmod -rwx filename", so here because you only want to take away execute you do
"chmod -x `which gvfs-trash`", and you need sudo powers to do it, so "sudo chmod -x `which gvfs-trash`".

---

### Post by Ego-X on 2012-10-25
Thank you for the excellent information. 

I think you're correct about the cause. I have a NAS device with numerous shares  that I have mounted in the default Ubuntu user folders (music, pictures etc).

Been around the block haha you know you're getting old when people on the internet can tell :)

---

