---
title: "Setup chroot for ssh connection"
date: 2022-08-03
forum: General Help
---

### Post by veedub67 on 2022-08-03
Hello,

I want to implement a chroot environment for ssh connections, to make the Ubuntu host more secure from those ssh connections.

I am using Jammy

I have followed these [instructions]("https://help.ubuntu.com/community/BasicChroot") to setup the chroot environment

What I'm not clear on is how I change the SSH environment / shell for remote connections to the chroot environment.

Appreciate some advice

Thanks

VW

---

### Post by veedub67 on 2022-08-03
Hello,

There are many articles on chroot. Unfortunately most don't seem to cover what I'm trying to do.

I'm currently performing an off-site backup using Borg via ssh, and while I think my ssh config is secure, it makes sense to "lock down" ssh access to only what is needed and nothing more.

The off-site backup resides on a separate volume: /mnt/Backup

So, what I want to do is restrict the ssh session to /mnt/Backup and executing Borg commands on the off-site host.

The first answer in this [thread]("https://superuser.com/questions/149404/create-an-ssh-user-who-only-has-permission-to-access-specific-folders") seems to cover what I'm trying to do.

There is a link [here]("https://jblevins.org/log/ubuntu-chroot") on how to setup chroot.

I can follow much of this article. 

However, the article is dated 2007, so it's obviously for a much older version of Ubuntu. I'm wondering if I should still use this as a guide. 

Second, assuming that the contents are still relevant to Jammy, it's not clear to me how once I've setup chroot; how I link the chroot environment in sshd_config.

In the first answer it says
```
[FONT=var(--ff-mono)]Match user restricted_user
[/FONT][FONT=var(--ff-mono)]ChrootDirectory /restricted/directory[/FONT]
```

However, I don't follow this.

After setting up chroot, I will have another instance of Ubuntu running in a "fake root" directory. I won't just have a /restricted/directory. I will essentially have a restricted OS. 

I think what I need to do is configure sshd_config to start the chroot instance of Ubuntu for the ssh / restricted_user

But if I'm right, I don't know how to do this.

And if I'm wrong, then I'm confused.

---

### Post by HermanAB on 2022-08-04
One problem is that chroot is not really secure.  So you can configure it with great effort and it will seem to work, but what is the point, if there are ways to subvert it? 

http://unixwiz.net/techtips/mirror/chroot-break.html

It is better to configure mandatory access control (AppArmor, SElinux, Tomoyo).

---

### Post by TheFu on 2022-08-04
I use an lxd container for my backup server, which gets local access to only the backup storage.

I use "pull" backups, not "push", so the client systems which could be compromised cannot harm any of the backup storage. The downside is that for system-level backups, each remote client system needs a root-equiv backup account that gets used from the backup server (linux container) for ssh access. Probably best to draw a diagram for how the ssh authentication works, since using ssh-keys from non-user accounts on both sides isn't exactly intuitive for most people.

In not way do I use any network storage solutions for backups. Malware knows about network storage, so it needs to be avoided as a risk mitigation technique.

So, while the container does provide something like a chroot, it is definitely stronger.  I have 2 of these containers because the backup tool I'm using changed from python2 to python3 with 20.04. The 2 different versions are incompatible thanks to python's serialization changes in the 2 versions.  Not gonna say it is bad; it isn't and had to happen, but it is a hassle for my needs.  OTOH, having 2 different backup server containers really does compartmentalize each backup tool nicely.

Just for your consideration.

---

### Post by ActionParsnip on 2022-08-04
Another question, why chroot users? Surely they SSH on to resolve server-wide issues? What is the usecase here, please?

---

### Post by TheFu on 2022-08-04
> **ActionParsnip said:**
> Another question, why chroot users? Surely they SSH on to resolve server-wide issues? What is the usecase here, please?

Sometimes allowing an unknown user into a system, but nowhere else is necessary.  There are lots of example uses, perhaps sharing a screen/tmux session for training or allowing them to pull files for bug reporting. My LUG installs a fresh OS a few times each month and allows anyone to play with the system for a day or so.  These are acquaintances, not friends.  I trust them enough to let time onto a LAN segment, but not enough to give them root on the system or access to other LAN segments.

That's off the top of my head.

---

### Post by veedub67 on 2022-08-04
Thanks for the responses.

I will ditch chroot and study the alternatives

---

### Post by ActionParsnip on 2022-08-04
> **TheFu said:**
> Sometimes allowing an unknown user into a system, but nowhere else is necessary.  There are lots of example uses, perhaps sharing a screen/tmux session for training or allowing them to pull files for bug reporting. My LUG installs a fresh OS a few times each month and allows anyone to play with the system for a day or so.  These are acquaintances, not friends.  I trust them enough to let time onto a LAN segment, but not enough to give them root on the system or access to other LAN segments.

That's off the top of my head.

Oh I'm aware. Just wondering why the user was wanting to set one up. It may not have been the right solution, mooting any efforts. It could be just to set one up for the exercise of setting one up as well.

---

