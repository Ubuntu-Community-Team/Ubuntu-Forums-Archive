---
title: "Update downloads fail"
date: 2014-10-02
forum: General Help
---

### Post by rbmoler on 2014-10-02
This computer (my wife's) failed to download the updates when I started the update program from the Icon on the desktop.  It gave me the message to check the internet connection.

But so far as I can determine the internet connection is working fine.

I searched for a thread and actually hit one that seemed likely to be an answer, but I lost it before I could read it and I can't locate it again.  It was about a year old.

Any advice or help would be appreciated

---

### Post by Bucky Ball on 2014-10-02
Please open a terminal and issue this command:

```
sudo apt-get update
```

Please post back exactly what the error message is at the end of the output. Cheers. ;)

As you've posted here, I'm presuming you are correct and your internet connection seems to work just fine apart from this?

---

### Post by rbmoler on 2014-10-03
My email, firefox, accessing the ubuntu store, etc all work.

I just ran sudo apt-get update and there was no error message and, apparently, the entire update was downloaded.  I presume there is a way for me to tell something to proceed with the updates.

---

### Post by grahammechanical on 2014-10-03
The apt-get update command updates the lists of software sources and helps to determine what can be updated or to be more accurate, upgraded. It proves that you have a connection to the Ubuntu servers/repositories.

You do not say what version of Ubuntu is being used. We are having to assume that it is Ubuntu that is being used. A version that has reached end of life will get this error and there will be error messages when we run apt-get update. But not in your case.

To actually upgrade what can be upgraded run

```
sudo apt-get upgrade
```

You may get error messages at this point. And those messages will help to diagnose the problem. To put it simply, Update Manager runs both commands for us when we give it permission to do so.

Regards.

---

### Post by rbmoler on 2014-10-03
Sorry.  I knew I should have given the Ubuntu version.  Just forgot to do it.
I'm running Ubuntu 14.04 LTS. 
Does the upgrade command just update that version?  I thought an upgrade gave you a newer version - Ubuntu 15.?? or something like.  I upgraded this computer from 12.04 LTS to 14.04 LTS a couple of months ago.

---

### Post by Bashing-om on 2014-10-03
rbmoler; Hi !

The terminal command:
```

sudo apt-get upgrade

``` compares data bases on your system, with databases on the mirror server and then it tries to update (upgrade in the sense only installed packages on your system) installed packages.
It is a different command to do a release upgrade ( as in "do-release-upgrade" )
As a 1st approximation post back to us the results of the 'upgrade' command.

[INDENT][INDENT]The longest journey begins
[INDENT][INDENT][INDENT]with that first step
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rbmoler on 2014-10-03
Boy Howdy!.  I just initiated the updater for the third time and it ran!  So I'm guessing that there was something about my Verizon DSL running too slow that caused the problem.  So now this computer is up to date after I restart it.

Thanks very much for the advice.  I learned some things along the way too.

I'll mark this as solved, but I think there should be something else to indicate that the problem actually resolved itself.

---

