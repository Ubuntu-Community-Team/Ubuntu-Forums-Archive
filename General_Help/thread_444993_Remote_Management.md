---
title: "Remote Management"
date: 2007-05-15
forum: General Help
---

### Post by Toukejin on 2007-05-15
Ok, this is a bit of an unusual request, I think.  Basically, I want to be able to log into a xubuntu box from vista (or ubuntu if it would make things easier, its just not installed yet) and forceably change passwords and lock things.  Here's the situation:

Roommate has chores.  Roomate 'forgets' to do chores.  Roommate sits on her computer all day wasting time and complaining about how much work sucks (when the rest of us have jobs + schoolwork and are far more stressed than she is...)  I want to be able to log into an admin account remotely and change her password, then hold it for chore-ransom / blackmail.  Don't take out the trash and we lock you out.  I know it's harsh, but its getting to the point that we're either going to kick her out altogether, or move and not tell her.  

Anyway, if anyone knows how to do this, please advise.

---

### Post by prozacgod on 2007-05-15
Wow you sound like me about 1 year ago.  If you have stress remove it, don't entertain it.  Get rid of the bum you'll feel better about it in the long run.  Second to that, is she running (any prefix)ubuntu, if so well you'll need to get her password.

short of having her password, you'll need to root the box.  There are instructions on google for this, lookup recovering root password, changing lost root password or some combination of that.  You'll find you need to boot the computer on a boot disc (CD, or thumb drive) and then change the root password from there, not sure what you'll have to do at that point.

when you reboot into the computer you can then use your new password, and install ssh via sudo apt-get install ssh

then use putty to ssh into the box and do whatever.

But really this will cause more stress than its worth.

If Someone tried to lock me out of my computer no matter how right they percieved they were, their computer would coincidently happen to spawn zeros in their BIOS flash rom.

-Prozacgod

---

### Post by Toukejin on 2007-05-15
Oh, I set the computer up, I can set her as user and myself as admin no problem.  She's agreed to do the chores, I just want to be able to change her password without entering her room.

---

