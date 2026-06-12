---
title: "Partition Permissions? How do I get this to work?"
date: 2007-05-30
forum: General Help
---

### Post by NikoKun on 2007-05-30
Ok, so I'm really new to Ubuntu, and Linux in general... I've got practically no technical knowledge of anything besides windows under my belt here, sadly... lol

Anyway, My problem is, for my parent's PC... (my parents have completely moved to Ubuntu, cause they hate the way windows kept getting these bad malwares... But they are NOT technical users, they only need it for web browsing and email, and Work Documents).

Anyway, I have setup Linux in it's own partition, and after install created another partition for personal files, thus to not confuse my parents.  I want to make that their Home directory...  (this is also so, if we need to reinstall linux, because i screw something up, their files will still be in that partition.)

The Main problem is, that we can not move files into that partition, or write to it, or create anything...  So even if I could make that their Home, I can't even write to it yet.

My friend says that it's a User permissions issue, something about it belonging to Root... so how do I change that... and keep it permanent?  This needs to always be setup so it works whenever my parents boot up.  So is there some file I can add something to that keeps that partition under normal user permissions?

The only other question I have is, how do I make that partition Permanently mounted and as their Home?

---

### Post by vayde on 2007-05-30
The usual way to do what you want is to set it up that way when you install Ubuntu.

Probably the simplest way to fix it is to reinstall, and choose 'manual' when it comes time to partition the disk.  While partitioning the disk, you can set one for / (that's your main partition), and one for /home (that's where the user's home directories and data files go).

There is also this guide: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Barring that, I suggest you get on freenode and come to #ubuntuforums-beginners .  There's lots of folks there waiting to help you.

Cheers.

---

### Post by NikoKun on 2007-05-30
Well, it took me a whole 2 days to set it up to the customized point that it is now for my parents...... it would be a shame and a waste of time to re-install...

So how could I just plain, fix the problem, without re-installing?  My permissions problem I mean...

---

### Post by vayde on 2007-05-30
check out this link: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I haven't done it on an existing system, but it can be done.

Good luck.  Holler back if you have trouble, or look us up on freenode.

---

### Post by NikoKun on 2007-05-30
ah ok, so do you think making the new partition into the home, in fstab using that guide, will fix my permissions problem and keep it mounted?

If so, dam I think that solves my problem, and nothing in that guide looks like it can't be done on an existing system.  I dont need to change partition sizes... although I might... lol

Thanks... I'll see if this will work... after that I just have to figure out why it works. XD

---

### Post by confused57 on 2007-05-30
> **NikoKun said:**
> ah ok, so do you think making the new partition into the home, in fstab using that guide, will fix my permissions problem and keep it mounted?

If so, dam I think that solves my problem, and nothing in that guide looks like it can't be done on an existing system.  I dont need to change partition sizes... although I might... lol

Thanks... I'll see if this will work... after that I just have to figure out why it works. XD

You can just set it up as a separate data partition, without setting up a separate /home:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

---

### Post by NikoKun on 2007-05-30
thanks confused, that link will help as well!

So um, a friend of mine mentioned using "Chmod 777"... I have no idea what that means or if that's what I would need for my situation or not... lol

---

### Post by confused57 on 2007-05-30
> **NikoKun said:**
> thanks confused, that link will help as well!

So um, a friend of mine mentioned using "Chmod 777"... I have no idea what that means or if that's what I would need for my situation or not... lol
If you set it up according to the link's example fstab entry:
```
#/dev/hdb4       
UUID=237f0cef-9905-41fb-82ba-bc360fb43a25 /media/datapartition ext3 rw,user  0    1
```

You shouldn't have to chmod(the "rw,user" should take care of permissions)... Here's another link for setting up a data partition a different way that does use chmod:
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by NikoKun on 2007-05-31
Hi again,

Well, I've added the new partition into the fstab as:

```
UUID=c5e86f91-ac51-49db-8af2-bd56ab0a9513 /media/storage ext3 rw,user  0    1
```

Now it is mounted properly after I boot up... but I still can't create files there (pasting or making a folder from the graphical file managers)  Unless of course, I use sudo in order to do what I want...

But in my situation, my parents can't use sudo any time they want to do something with their files... They don't have, nor do they need any command line knowledge... lol

So how do I make that drive more easily accessible for them... how do I give that partition normal user permissions???  So that sudo is unneeded in this case, and so that they (parents) can use that partition from the graphical file managers?

I'm trying my best to describe this problem... lol

---

### Post by confused57 on 2007-05-31
Maybe you do need to manually give the partition proper permissions:
```
sudo chown -R niko:niko /media/storage
sudo chmod -R 755 /media/storage
```

Just substitute your parent's username for niko.

---

### Post by NikoKun on 2007-05-31
> **confused57 said:**
> Maybe you do need to manually give the partition proper permissions:
```
sudo chown -R niko:niko /media/storage
sudo chmod -R 755 /media/storage
```

Just substitute your parent's username for niko.

Yah I've thought about that... but doesn't that reset after reboot?  Maybe I'm wrong? lol

Am I asking too much? XD  Is there a place I can enter custom commands to run for boot maybe, that i could add this command to? lol

I'm sorry I'm asking so many questions, but I'm just so new to this... =/

EDIT:  I just found something
[http://doc.gwos.org/index.php/Understanding_fstab#Permissions_2](http://doc.gwos.org/index.php/Understanding_fstab#Permissions_2)
Do I need to do anything with that?  I'm just not sure about the syntax of things, and if it will stay for my parents after reboots... lol i think it will

I'll run a test on my personal PC... =/

---

### Post by NikoKun on 2007-05-31
Thanks everyone ^_^; I've pretty much solved my problem, at least for now. XD

*feels so noob*

---

