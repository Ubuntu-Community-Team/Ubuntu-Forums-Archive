---
title: "Security, ACLs"
date: 2007-06-21
forum: General Help
---

### Post by weblordpepe on 2007-06-21
Hi there.

In Windows one can set groups and nested groups for security and pin them right down into the files/folders.

Now I know that there are groups in linux but how do you set permissions for say a group of 10 users so they can't access /foo/bar folder?

Is there anything like local users & groups, or active directory?

---

### Post by weblordpepe on 2007-06-22
Bump!

---

### Post by Brucevdk on 2007-06-23
I don't have any hands-on experience with this, though the subject does interest me. Here's what I've found out so far.

> **weblordpepe said:**
> In Windows one can set groups and nested groups for security

Apparently there doesn't seem to be such a thing as nested groups in GNU/Linux.

> **weblordpepe said:**
> and pin them right down into the files/folders.

This however seems possible using ACLs, I looked around a little bit and immediately came across a paper entitled [POSIX Access Control Lists on Linux]("http://www.suse.de/~agruen/acl/linux-acls/online/") by Andreas Grünbacher of SUSE. [Here's a simple article describing how to set it up]("http://tlug.dnho.net/?q=node/171"), note that there's also a GUI called Eiciel which integrates with Nautilus. 

You can install the utilities necessary for assigning these ACLs using *sudo apt-get install acl eiciel*.  You'll also have to modify */etc/fstab* and add the option acl for the mounts you wish to use ACLs with. See the article mentioned above for more details. Make sure you quit nautilus using *nautilus -q* to enable integration with Eiciel.

You might also want to take a look at [SELinux]("https://wiki.ubuntu.com/SELinux"), I'm not quite sure how well it's been integrated with Ubuntu but it seems the packages are available trough the repositories.

> **weblordpepe said:**
> Now I know that there are groups in linux but how do you set permissions for say a group of 10 users so they can't access /foo/bar folder?

Here's an example using the command line tools instead of the eiciel GUI. I created a group *foonotbar* and added the user *foo*. The following is the procedure for preventing any user from the group *foonotbar* from accessing /tmp/foo/bar, the default permissions apply to users from other groups.

```

bruce@bruce-laptop:/tmp/foo$ mkdir bar
bruce@bruce-laptop:/tmp/foo$ getfacl bar
# file: bar
# owner: bruce
# group: bruce
user::rwx
group::r-x
other::r-x

bruce@bruce-laptop:/tmp/foo$ setfacl -m g:foonotbar:--- bar/
bruce@bruce-laptop:/tmp/foo$ getfacl bar/
# file: bar
# owner: bruce
# group: bruce
user::rwx
group::r-x
group:foonotbar:---
mask::r-x
other::r-x

```

What happens when user *foo* tries to access */tmp/foo/bar*:
```

foo@bruce-laptop:/tmp/foo$ grep "foonotbar" /etc/group 
foonotbar:x:1004:foo
foo@bruce-laptop:/tmp/foo$ cd bar
-bash: cd: bar: Permission denied

```

That's what you wanted right?

> **weblordpepe said:**
> Is there anything like local users & groups, or active directory?

You'll have to explain these terms to me since I'm not familiar with them, go easy on me :)

---

### Post by weblordpepe on 2007-06-23
Holy cow. Thats heaps. Thats alot for me to swallow - but even more for you to offer to type out. Thanks.
Oh Active Directory is Microsoft's answer to a virtual tree structure of everything, everyone, every device in an entire organisation broken down into sub-areas, groups etc... everything with its own GUID & SUID. Very good stuff.
And local users & groups is used when your computer isn't part of a domain, but you want to fiddle with hierachial security on your local machine.

Thanks heaps for the link. Yeah at the moment my primary computer (houses my 100's of GB and shared videos etc) runs Windows and I have some complex security rules set up.
When I boot that into Ubuntu I couldnt figure out how to set up any security with samba & just bleh...yeah wasn't good.

---

### Post by Brucevdk on 2007-06-23
I was just reading the Eiciel manual and found out it integrates nicely with Nautilus, I just had to restart it (*nautilus -q*). I updated the post above with this information.

> **weblordpepe said:**
> Oh Active Directory is Microsoft's answer to a virtual tree structure of everything, everyone, every device in an entire organisation broken down into sub-areas, groups etc... everything with its own GUID & SUID. Very good stuff. And local users & groups is used when your computer isn't part of a domain, but you want to fiddle with hierachial security on your local machine.

That does give me an overall impression of what it does but I guess I'll have to research it a little bit further to find out how it impacts security etc. I bet there's probably something similar on GNU/Linux but at the moment I've gotten my daily portion of Googling :) 

> **weblordpepe said:**
> When I boot that into Ubuntu I couldnt figure out how to set up any security with samba & just bleh...yeah wasn't good.

I'm not sure how this affects Samba shares, I haven't really ever used it. But it sounds quite interesting, would be great if you could keep me informed trough this thread.

---

### Post by weblordpepe on 2007-06-25
Well I did a course in Active Directory on Windows 2000.
Its basically the most impressive thing Microsoft has ever farted out. All organisational policies, administration, printers, users, computers, for a company are all in a tree structure.

And you can join that to other active directories. And have huge collections of them all heirachial. Corporate networks can get very large & complex, and Active Directory is like a GUI and organisational structure for everything. 

Of course it only runs on Windows, and its slow and there's quirks. But its amazing software really.

---

