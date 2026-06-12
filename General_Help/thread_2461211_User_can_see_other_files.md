---
title: "User can see other files"
date: 2021-04-26
forum: General Help
---

### Post by billyh717 on 2021-04-26
When running adduser (name) and following the process, They can see all files in user/ (including root) and the whole files when They should only see their user folder?


How can I solve this issue?

(User account: OPR)


[http://panel.justbillyh.xyz:2005/729d9f.png](http://panel.justbillyh.xyz:2005/729d9f.png)
[IMG]http://panel.justbillyh.xyz:2005/729d9f.png[/IMG]

---

### Post by scorp123 on 2021-04-26
> **billyh717 said:**
> 
[http://panel.justbillyh.xyz:2005/729d9f.png](http://panel.justbillyh.xyz:2005/729d9f.png)
[IMG]http://panel.justbillyh.xyz:2005/729d9f.png[/IMG]

Looks perfectly normal to me. If you restrict a user too much then they would not be able to login, not be able to run any program or use the system at all.

What's really important are locations such as 
[LIST]
[*]/etc:  User can read but not write there.
[*]/home/otheruser :  User can maybe read (this could be further locked down if needed) but definitely not write there
[*]/root :  normal users should not be able to access this at all
[/LIST]

---

### Post by billyh717 on 2021-04-26
On my other vps ive owned they cant access any users files at all or see root unlike this, So how would i go about this "locking permissions more"

---

### Post by ActionParsnip on 2021-04-26
If a user cannot access files in "/" how are they supposed to use the system? They wouldn't be able to run ANY commands at all without at least some access......wouldn't they

---

### Post by billyh717 on 2021-04-26
On the old provider i was on you could only use /user/opr and that was it, Im trying to not allow the user to see other users files

---

### Post by deadflowr on 2021-04-26
The vps probably has a chroot setup.

---

### Post by The Cog on 2021-04-26
There is no folder called /user in a normal Ubuntu install. There is a folder called /usr, which contains system resources that you need to be able to read in order to operate.
The user's personal folders are under /home, such as /home/user1, /home/user2, /home/opr. Users very likely cannot access the contents of each other's home folders. I.e. user1 cannot see the files or folders inside /home/user2 or /home/opr. All you have posted here is that user opr can see the system folders.
Here is an intro into the layout of files and folders in Linux: [https://linuxhandbook.com/linux-directory-structure/](https://linuxhandbook.com/linux-directory-structure/)

---

### Post by scorp123 on 2021-04-26
> **billyh717 said:**
> On the old provider i was on you could only use /user/opr

That's a non-standard folder location. I guess they were locking you into a Docker container or some kind of "chroot" jail environment?

May I ask why you feel the need you need to lock down your system so much? I feel it's like overkill. If you don't trust that other user ... then why even let them login into your system in the first place?

---

### Post by TheFu on 2021-04-26
Could be
[LIST]
[*]chroot
[*]linux container of some sort (docker, lxd, etc)
[*]restricted shell
[*]firejail or other "sandboxed" environment
[/LIST]

Feel free to read up about those.  None of those are normally used on typical installations, but they are possible should a shared hosting setup want to use them.  Many of those tools aren't 100% perfect, in that there are known techniques to "break out" of the restricted environment - at least an expert can do it.

---

