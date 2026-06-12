---
title: "[SOLVED] Shell to identify the account user logged into?"
date: 2007-07-06
forum: General Help
---

### Post by stchman on 2007-07-06
Hello all, I am wanting to know if there is a shell script variable that identifies which user account you are using.

Lets say you login as bob, I would like to have a shell script variable that would return bob.

Thanks

---

### Post by stchman on 2007-07-06
I think I found the solution:

Use the whoami variable.

Does anyone concur?

Also in shell would you use the command as follows:

sudo chown -R `whoami`:`whoami` ~/.evolution

or

sudo chown -R $whoami:$whoami ~/.evolution

Thanks

---

### Post by Ayuthia on 2007-07-06
That is what I use!

---

### Post by mbeierl on 2007-07-06
shell variable:  $USER
shell command: whoami

The difference is you can use $USER directly in a script, vs.  having to do something like ME=`whoami`.

Hope this helps!

To see list of currently exported vars:  env

---

### Post by Ayuthia on 2007-07-06
I missed your edit.  What I have used in scripts is usually $USER.  As for using $whoami, that will not work because you are now using that as a variable, not a command.  The `whoami` should work though.

---

### Post by stchman on 2007-07-06
So what I should do is the following:

sudo chown -R $USER:$USER ~/.evolution

Anyone concur?

Thanks

---

### Post by mbeierl on 2007-07-06
"I knew I should have concurred!" [Catch me if you can]

So, what you want to do is take ownership of the .evolution directory as the currently logged in user?  In that case, yes.

---

### Post by stchman on 2007-07-06
> **mbeierl said:**
> "I knew I should have concurred!" [Catch me if you can]

So, what you want to do is take ownership of the .evolution directory as the currently logged in user?  In that case, yes.

It is just an example, but yes I want to be able to implement a command like this in a script that will change ownership of a folder recursively to the currently logged in user.

Thanks a bunch.

Can you recommend a good text for bash programming?

---

### Post by mbeierl on 2007-07-06
Definitely not
```
man bash
```
When it comes to programming, there are very few that are written from scratch.  Most of them are copied from somewhere else then modified to suit needs.  I'd start with google.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

