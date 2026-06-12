---
title: "[SOLVED] Deleted stuff, what to do"
date: 2008-02-05
forum: General Help
---

### Post by Cullen on 2008-02-05
I was trying to remove a user profile, and I was going to re-add it.  So, I opened the user management tool, and deleter that user. It told me that the folders would be left on the drive. 

So, I hopped in to bash and typed

```
sudo rm /home/user -d -f -v 
```

Next thing I know the terminal is listing off a bunch of files sotred on a nother computer on my "shared drive"

So I'm confronted with more then one problem. 

1.) Is all of that stuff just gone?  Is there no kind of file recovery utility for Ubuntu?

2.) Why would that command have deleted stuff not on this computer, hell to my knowledge that user didn't even have access to that shared drive I don't get it.

Please can someone, ANYONE help me?

---

### Post by sigmarhophi on 2008-02-05
What would possess you to add all the other flags to the rm command?  well anyways the extra stuff you saw fly by was from the -d or unlink command.  Did this user have any or many link symbolic or otherwise in the home directory?  Based on which type of link was used, your files should still be there.

In the future, I recommend using the command:

sudo deluser --remove-home


As for your question regarding file recovery, yes.  To help, what formate type are you using? ext, reiser, etc.

---

### Post by bodhi.zazen on 2008-02-05
no, there is no "undo" for that command.

Best thing is to STOP using the hard drive ASAP. Boot a live CD and mount the partition ro.

You can then look at this :

Deleted File/directory : [https://answers.launchpad.net/ubuntu/+question/2178](https://answers.launchpad.net/ubuntu/+question/2178)

In terms on deleting files on another computer, the only way I can see this happening is is they were mounted in /home/user. Do you run any network protocols ? nfs, samba, sshfs, ftp ????

---

### Post by Cullen on 2008-02-05
Long story short I reverted back to windows knowledge and it would seem that by using "Ontrack" I am being able to recover everything.

So the next step is to IDIOT proof my shared drive. And that brings a few questions

1.) Can a drive that is non-"fat", non-samba, can it be shared with a windows machine?

2.) How do I prevent things like this from happening again.  (obviously don't type that command) This is not the first time I have had trouble like this.

---

