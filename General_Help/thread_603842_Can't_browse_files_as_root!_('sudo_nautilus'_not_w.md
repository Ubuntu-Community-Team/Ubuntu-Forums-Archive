---
title: "Can't browse files as root?! ('sudo nautilus' not working anymore??)"
date: 2007-11-05
forum: General Help
---

### Post by Fireblend on 2007-11-05
Hey, I'm having some trouble here, seems like Nautilus won't work for root anymore. I've tried gksudo nautilus, sudo nautilus and all that and the output is always:

> (nautilus:7288): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Help!

---

### Post by mali2297 on 2007-11-05
Is it just Nautilus or more general? Try
```

gksudo gedit

```

---

### Post by kellemes on 2007-11-05
> **Fireblend said:**
> Hey, I'm having some trouble here, seems like Nautilus won't work for root anymore. I've tried gksudo nautilus, sudo nautilus and all that and the output is always:



Help!

You're running these from the run-dialog?
If so.. can you please try from a terminal?
By the way.. sudo nautilus is not suppose to work.
Try gksu or gksudo.

---

### Post by #Reistlehr- on 2007-11-05
when you are accessing a gtk app with root privledges, you're supposed to use gksudo. 

ex:

gksudo nautilus

Will work. If you use sudo nautilus, the kernel will implode and destroy your harddrive by turning down the hdparm. 

(lol) :D

---

### Post by Eliwood on 2007-11-16
D:

I get the same thing!
When I try runing anything gksudo I get the same message!

It's starting to annoy me.

"gksudo nautilus" doesn't work.
Anyone have an explanation as to why?

---

### Post by mali2297 on 2007-11-16
There exists a bug report:
[https://launchpad.net/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/ubuntu/+source/gksu/+bug/23917)

From the only one that seemed to have solved the problem:
> 
I was having this same issue. It seems to be related to the Keyring Manager... maybe because all my passwords (root, user, and keyring) were the same. I just deleted the keyring and that solved the problem.


I had a similar issue when .Xauthority was missing. I don't think it is related, but you could check this anyhow:
```

ls -l ~/.Xauthority

```

---

### Post by Eliwood on 2007-11-16
This is really frustrating me because I have an mp3 player which I can't put songs onto because the .trash file on it is taking up too much space.
The only solution I found to this would be going in as root and deleting the files as I don't have permission as is.

---

### Post by mali2297 on 2007-11-16
> **Eliwood said:**
> This is really frustrating me because I have an mp3 player which I can't put songs onto because the .trash file on it is taking up too much space.
The only solution I found to this would be going in as root and deleting the files as I don't have permission as is.

Well, then use **sudo rm** from the terminal:
```

sudo rm -irv /path/to/.Trash

```
The chosen options are here
> 
      -i, --interactive
              prompt before any removal
      -r, -R, --recursive
              remove directories and their contents recursively
      -v, --verbose
              explain what is being done

The -i option is precautionary, you can omit it if you don't want to confirm every removal.

---

### Post by mali2297 on 2007-11-16
> **Eliwood said:**
> D:

I get the same thing!
When I try runing anything gksudo I get the same message!

It's starting to annoy me.

"gksudo nautilus" doesn't work.
Anyone have an explanation as to why?

This would mean that you can't use Synaptic either, is this the case?
I understand your frustration.

EDIT:
The bug is labeled low priority since gksudo usually works despite the warning message. It might be that the error that you are experiencing here isn't related to the warning in the output.

Does sudo still work? If not, check this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by alnhntr29 on 2007-11-16
Have the same problem, my solution was this(a little aggr.- but it worked)
In your right click menu, choose open with, then custom command. Then for your custom command type "gksudo". It will  ask for your pass, then do nothing. Right click again and open with custom command "Sudo", then it will open the file in nautilus as root. You have to click on gksudo first and input your pass and then click open with sudo every time, but it works on my system, may work on yours, worth a try, just a few extra mouse clicks. This was the only way I could get nautilus to open as root.

---

### Post by K.Mandla on 2007-11-16
A more barbaric solution might be to reboot into recovery mode and hand-delete those files from the command line. ... See, I told you it was barbaric. ;)

---

### Post by Eliwood on 2007-11-16
> **alnhntr29 said:**
> Have the same problem, my solution was this(a little aggr.- but it worked)
In your right click menu, choose open with, then custom command. Then for your custom command type "gksudo". It will  ask for your pass, then do nothing. Right click again and open with custom command "Sudo", then it will open the file in nautilus as root. You have to click on gksudo first and input your pass and then click open with sudo every time, but it works on my system, may work on yours, worth a try, just a few extra mouse clicks. This was the only way I could get nautilus to open as root.

Well.
This worked.
sort of.

It worked for the first couple of files.
But then like.
It went back to saying "Error - read only disk"
-sigh-

This bug is getting annoying.
When I did what Mali said, the Terminal gave me a message that said it couldn't delete the file as it was read-only.

I guess I'll just log out, then in and try deleting the files again.

Although, Alnhntr, your way seems to work the best so far.

You know. >_>
Exculding the barbaric method.

---

### Post by skymera on 2007-11-16
try

sudo /etc/init.d/dbus restart

then try and see if it works:

sudo nautilus

---

### Post by Eliwood on 2007-11-16
> **skymera said:**
> try

sudo /etc/init.d/dbus restart

then try and see if it works:

sudo nautilus

Well.
Again, sort of.

D:

It let me into the Nautilus (looked like it was going to work for a second), but still wouldn't let me delete the files only send them to the garbage bin. 

I guess It's time for the final resort.
Boot up windows on my other computer and delete it through that. T___T
Then NEVER send any files to the garabage bin again on that mp3 player.

---

