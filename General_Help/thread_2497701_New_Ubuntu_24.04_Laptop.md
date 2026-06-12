---
title: "New Ubuntu 24.04 Laptop"
date: 2024-05-15
forum: General Help
---

### Post by billywyatt2 on 2024-05-15
Really hope that someone can help me out here.

My Niece bought a new "Juno" laptop with Ubuntu 24.04 pre-installed and she immediately got busy configuring the laptop the way she wanted.
That i suppose was alright but i know for a fact she didn't make a back up disk and now Firefox won't start neither will Thunderbird or Rhythmbox
And when she tried to look in the Home folder a message appeared on the screen stating that a fatal error had occurred something about 
the address for the Home folder was wrong. 

I do not know enough about Linux or Ubuntu myself to help her. So can someone help please.

---

### Post by howefield on 2024-05-15
You could try creating a new user ?

Settings > System > Add User

Might give you a clean working account to work from.

If there are no factory reset options then I'd probably re-install and add the juno ppa to quickly get back to a fresh working state (assuming that there is no critical user data to recover).

---

### Post by billywyatt2 on 2024-05-15
Hello there howefield
I did as you suggested and created a new user and that certainly did the trick!
But when i tried to delete/remove the username using the new user account i was informed that
the new user did not have sudo rights? How do you give a user sudo rights?

But a very big thank you for coming to my rescue when you did.
For a time i thought i'd be stuck with an expensive door stop lol.

---

### Post by dragonfly41 on 2024-05-15
> [COLOR=#000000] How do you give a user sudo rights?
That might be rewritten .. [/COLOR][COLOR=#000000] How do you give a raw user sudo rights?[/COLOR]

This could be a good test case for mentoring a new user in the arts.

Start by running this command in terminal to begin to understand.

```
man sudo
```

More resources abound.

---

### Post by yancek on 2024-05-15
The original user created during the install has sudo right so you could log in to a terminal as the original user and add the newly created user to the sudo group.  There are literally, thousand of sites explaining this process such as the one below.  You will need to scroll down the page a bit to get past the creating user part which you have already done.

[https://www.digitalocean.com/community/tutorials/how-to-create-a-new-sudo-enabled-user-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-sudo-enabled-user-on-ubuntu)

---

### Post by grahammechanical on 2024-05-15
Or, on 24.04 open System Settings>System>Users. To add a new user you will have already got this far and know how to unlock this part of the utility with the password set when the system was first installed. When you added the new user you would have seen a slider that would have given the new user administrator or sudo privileges. Find that slider for the new user and move it across.

Regards

---

### Post by dragonfly41 on 2024-05-15
Perhaps this old link better explains deleting the original user which I understand OP wants

[https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-18-04)

---

### Post by pantazi on 2024-05-18
@OP, for interest, has this query anything to do with your post -showthread.php?t=2497396?
New Laptop in General help?

---

