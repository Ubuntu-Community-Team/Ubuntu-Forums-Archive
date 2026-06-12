---
title: "Is it possible to change my username?"
date: 2014-12-11
forum: General Help
---

### Post by Jakesploder on 2014-12-11
If there is an admin that could do it, i would like to change my name to Jakesploder. Thanks!

---

### Post by TheFu on 2014-12-11
Sure, but usernames in linux need to be lowercase, no spaces, no special characters.

Just edit the /etc/passwd, /etc/shadow, /etc/group and use visudo to change the sudoers file.

Is it best to do each of these from a root terminal, so the changes don't screw with the login.

If you change the location of the HOME for a user to match the new userid, be certain to move that directory to the new name too.

Because almost everything is based off the HOME and userid, this should cover almost everything necessary.

---

### Post by papibe on 2014-12-11
Hi space core.

Is this a request for your forum's username?

Regards.

---

### Post by slickymaster on 2014-12-11
> **TheFu said:**
> Sure, but usernames in linux need to be lowercase, no spaces, no special characters.

Just edit the /etc/passwd, /etc/shadow, /etc/group and use visudo to change the sudoers file.

Is it best to do each of these from a root terminal, so the changes don't screw with the login.

If you change the location of the HOME for a user to match the new userid, be certain to move that directory to the new name too.

Because almost everything is based off the HOME and userid, this should cover almost everything necessary.

I think the OP his referring to his forum username. ;)

@space core:
If you want to change your username just start a new thread in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") sub-forum and name the thread "**Username change**".

When you'll do it, please take in consideration the following:
[LIST]
[*]Make sure that any change you request is what you want - we will only change it ONCE.
[*]Make sure to give us 3 alternatives, we will not look without there being 3.
[/LIST]

---

### Post by Jakesploder on 2014-12-20
Yes it is i want to change my fourm name

---

### Post by bapoumba on 2014-12-20
@space core : please post a thread in the Resolution Centre as Slickymaster has advised, thanks.
Please read : [http://ubuntuforums.org/showthread.php?t=2234107](http://ubuntuforums.org/showthread.php?t=2234107)

---

