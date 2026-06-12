---
title: "sort of lab setup"
date: 2008-06-24
forum: General Help
---

### Post by catonano on 2008-06-24
Hello people,

I'd like to use Ubuntu on  4 workstations in my office instead of Vista.

I'd like to able to control those machines from mine one, since the employees are not able to do themselves.

I'd need to control:

[LIST=1]
[*]which apps are installed
[*]how conf files are edited
[/LIST]

I'm new at this, so I'm not sure about how to proceed. Is there any software solution or some method I could use ?

Thanks so much for any hint
Bye
Cato

P.S: maybe this is not the right place to post this. I'm sorry I couldn't find any better

---

### Post by fsmithred on 2008-06-24
If you install ubuntu on all the machines, your user will be the administrator. Create user accounts for your employees and don't give them admin powers. Do some reading on users, groups, and permissions, in case you want to arrange it in some special way. (e.g. workgroups with common permissions.)

You can administer all machines from yours through ssh. You'll need to install openssh-server on any machine you want to log into from another. So far, what you're asking for is not difficult at all.

---

