---
title: "Commands"
date: 2008-02-07
forum: General Help
---

### Post by upthelum on 2008-02-07
Hi all.

I have to start using red hat 7 for work purposes but i'm not sure of the commands to use in terminal. I noticed with the first command i tried (apt-get update) that it doesn't exist in red hat. Can someone point me to a relevant command list or help to ease the transition to red hat. I was told (vaguely) that it's possible to enter a command in red hat terminal and change shells or something like that. 

Any help would be great thanks.

---

### Post by kesman on 2008-02-07
Red Hat doesn't have apt, that's for sure for it's weakness. That's mostly all I know about red hat, I've always used only debian-based distros.

---

### Post by cosborn72 on 2008-02-07
I believe Red Hat uses YUM rather than APT as the command line package manager.  It also comes with a GUI manager call PUP.

You can get a quick tutorial of YUM commands here:

[http://fedoraproject.org/wiki/Docs/Drafts/SoftwareManagementGuide](http://fedoraproject.org/wiki/Docs/Drafts/SoftwareManagementGuide)

I believe the command you would use is

```
su -c 'yum update'
```

but I would read up on it to be sure.

---

### Post by upthelum on 2008-02-07
Ok guys thanks i'll look into it...

---

