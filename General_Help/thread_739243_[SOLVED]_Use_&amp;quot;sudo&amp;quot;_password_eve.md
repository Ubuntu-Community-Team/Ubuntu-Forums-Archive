---
title: "[SOLVED] Use &amp;quot;sudo&amp;quot; password every time!"
date: 2008-03-29
forum: General Help
---

### Post by Bruce M. on 2008-03-29
Hi Folks,

At present when I type my password in for "sudo commands", Synaptic, etc. there is a 15 minute "grace" period to use it without having to type it again.

How do I change that so I need to type it in "every time", regardless of the time passed?

Thanks
Bruce

---

### Post by Ub1476 on 2008-03-29
You can log in with "su", which is root. But, there is a reason you have to retype your password (security).

You might have to set a custom root password in user settings.

This is only for terminal though..

---

### Post by munkyeetr on 2008-03-29
> **Ub1476 said:**
> You can log in with "su", which is root. But, there is a reason you have to retype your password (security).

You might have to set a custom root password in user settings.

This is only for terminal though..


He wants to be required to enter it **every time**, so there is no "grace period".

I don't know the answer, but I also want this, so I wanted to clarify that and now I also await help in this issue.

---

### Post by forestpixie on 2008-03-29
The attribute is called timestamp_timeout - [http://ubuntuforums.org/showthread.php?t=179048](http://ubuntuforums.org/showthread.php?t=179048)

But I'm not going any further as I've no idea what to do and really don't want to be responsible for anything else :biggrin:

---

### Post by munkyeetr on 2008-03-29
Found it:

At the terminal type:
```

sudo visudo

```

Then under the User privilege specifications section, I added the line:
```

Defaults:<username> timestamp_timeout=0

```
where obviously username is your username. **EDIT: Not sure if it matters, but I used a TAB between <username> and timestamp_timeout=0**

CTRL+X
Y
ENTER

Now when I use sudo it continuously asks for authentication.

---

### Post by Bruce M. on 2008-03-29
> **Ub1476 said:**
> You can log in with "su", which is root. But, there is a reason you have to retype your password (security).

You might have to set a custom root password in user settings.

This is only for terminal though..

Good security would also involve reading what's required and the actual question at hand.

> **munkyeetr said:**
> Found it:

At the terminal type:
```

sudo visudo

```

Then under the User privilege specifications section, I added the line:
```

Defaults:<username> timestamp_timeout=0

```
where obviously username is your username. **EDIT: Not sure if it matters, but I used a TAB between <username> and timestamp_timeout=0**

CTRL+X
Y
ENTER

Now when I use sudo it continuously asks for authentication.

YES!  That's what I want.  :)
munkyeetr, you and I must be the only two who want it "everytime", everyone else wants to "avoid" typing the password.  Oh well, to each their own.

Thanks for your post #3 "clarifying" what it was I (we) were after.  :lolflag:

---

### Post by munkyeetr on 2008-03-29
np :)

---

### Post by Bruce M. on 2008-03-29
I keep getting an error:

```

# User privilege specification
Defaults:<username>       timestamp_timeout=0

```

this worked:

```

# User privilege specification
Defaults:username       timestamp_timeout=0

```

Do you realize how many times I had to type in my password for this!

How can I set it so I don't need to type my password at all?  **{JOKING HERE!}**  :lolflag:

EDIT: Of course don't use "username" use your "log in" user name. :)

---

### Post by munkyeetr on 2008-03-29
yeah, you don't want the <> in there. sorry, i should have been specific about that.

so just confirm that you have it working now?

---

### Post by Bruce M. on 2008-03-29
> **forestpixie said:**
> The attribute is called timestamp_timeout - [http://ubuntuforums.org/showthread.php?t=179048](http://ubuntuforums.org/showthread.php?t=179048)

**Thank you kindly for this forestpixie**

> **forestpixie said:**
> But I'm not going any further as I've no idea what to do and really don't want to be responsible for anything else :biggrin:

Do you know that a coward dies a thousand deaths and a brave man but one?
Of course if you break 1000 Ubuntu computers and they may make that one death seem like ... you don't want to know.  :lolflag:

---

### Post by forestpixie on 2008-03-29
> Do you know that a coward dies a thousand deaths and a brave man but one?

maybe maybe - but think how many you live in between each death  :)

Glad I pointed in the right direction anyway. I've spent today reinstalling heron twice - which has been fun - so another 998 puts no fear in me ;)

---

### Post by Bruce M. on 2008-03-29
> **forestpixie said:**
> maybe maybe - but think how many you live in between each death  :)

Glad I pointed in the right direction anyway. I've spent today reinstalling heron twice - which has been fun - so another 998 puts no fear in me ;)

:lolflag:

998 installs to go, 998 installs to go ...
If one of those installs should happen to fail ... :guitar:
997 installs to go....

I hope all is well with you and you're last install.

---

### Post by Bruce M. on 2008-05-08
> **munkyeetr said:**
> yeah, you don't want the <> in there. sorry, i should have been specific about that.

so just confirm that you have it working now?

I've been reviewing some threads, and realized just today ( 9 May ) that I never did answer you.

Yes, I can confirm that it is working. I type my password every time. :)
Thanks for that.

Bruce

---

