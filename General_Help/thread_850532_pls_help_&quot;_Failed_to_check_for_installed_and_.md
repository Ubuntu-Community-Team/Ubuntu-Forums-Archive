---
title: "pls help &quot; Failed to check for installed and available applications   (please help."
date: 2008-07-05
forum: General Help
---

### Post by oldmanfunk on 2008-07-05
I am getting the following error message after trying to get my computer to play dvd's. I am new to Ubuntu, and i tried to type something into the terminal that one of the forums said would work and now i have an error message in my Add/Remove Applications.   Here is the message:


Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


I have also attached a screen shot.

Can anyone please help, or give me some guidance. Thank you.

---

### Post by drs305 on 2008-07-05
> **oldmanfunk said:**
> This is a major failure of your software management system. Please check for broken packages with synaptic


Open synaptic, click on the Custom tab in the lower left, and see if there are any broken packages listed. If there are, either mark for reinstallation or uninstall them.

> 
check the file permissions and correctness of the file '/etc/apt/sources.list'


Please post the results. There could be a problem with your sources.list that is causing the error. 
```
cat /etc/apt/sources.list
```

Once things are resolved, you run these commands to update the repositories and fix any problems. Make sure you close synaptic first or you will get an error message::
```

sudo apt-get update
sudo apt-get install -f

```

---

### Post by oldmanfunk on 2008-07-05
i went into synaptic and got the following error message.


An error occured

The following details are provided:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

see attached image,


thanks for replying.

---

### Post by drs305 on 2008-07-05
Reinstall the Medibuntu repository for hardy. (If you have a different version there is a different procedure):

```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bad
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by oldmanfunk on 2008-07-05
2

---

### Post by oldmanfunk on 2008-07-05
That seemed to fix it!
Thanks very much. You have been Very Helpful.

---

### Post by oldmanfunk on 2008-07-05
Hey drs305,

Do you happen to know how to get Ubuntu to play DVD's? 
that is how i messed it up in the first place trying to get them to play.

If you can share your knowledge that would be fantasic.
Thanks again.

---

### Post by drs305 on 2008-07-05
The best thing to do is to mark this thread solved via the 'thread tools' link at the top right of the first post and then either do a search or open a new thread. There is a multimedia forum which probably has a How-To.

Here is a typical beginner forum entry that might help:
[http://ubuntuforums.org/showthread.php?p=5287142#post5287142](http://ubuntuforums.org/showthread.php?p=5287142#post5287142)

Glad we solved at least one problem ;-)

---

