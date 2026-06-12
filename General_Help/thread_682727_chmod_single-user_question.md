---
title: "chmod single-user question"
date: 2008-01-30
forum: General Help
---

### Post by orbish on 2008-01-30
I want to password protect my "apple" folder, which contains a lot of video and picture files if you catch my drift.  I want to be able to browse to the directory from a non-root nautilus, and have it ask for a password when I try to access the folder.

I've tried researching this, and can't find a solution for my specific problem.  I only have one user on my machine.  With ubuntu, this is usually the user that's in the admin group or whatever... so it has the ability to use sudo... etc.

i have set the user/group to root, used many different chmod variants.  I am just having problems grasping chmod in general.  Any help on this would keep me out of the doghouse with the girlfriend and would be greatly appreciated.

---

### Post by dgray_from_dc on 2008-01-30
First off, create an account for her.  Use the excuse that you've got things set up just the way you like.  I don't think that a single user machine can easily be set up to restrict access for its only user.

Then use

```
 chmod 0700 apple
```

to make it readable by you and you only.  Then add a "." to the front of the file name e.g.

```
 mv apple .apple
```

thereby making it hidden to a normal browser.

She won't see it and if she does find it, she'll get a "permission denied" error.

---

### Post by orbish on 2008-01-30
> **dgray_from_dc said:**
> First off, create an account for her.

Then use

```
 chmod 0700 apple
```

to make it readable by you and you only.  Then add a "." to the front of the file name e.g.

```
 mv apple .apple
```

thereby making it hidden to a normal browser.

She won't see it and if she does find it, she'll get a "permission denied" error.

Creating another user is what I'm avoiding, which is why I put single-user in the thread title.  I want just a desktop.  I know linux file permissions are set up for separate users.  I've changed permissions to 700, 600, 400 on apple with all the same results.  As far as the hidden folder method, this hosed me while switching from ntfs > ext3... forgot to unhide my old apple folder and lost it.

The only other methods I've seen are encryption.  I just want nautilus to ask for a password, this doesn't seem possible in this situation though.  Thanks for your timely response though!

---

