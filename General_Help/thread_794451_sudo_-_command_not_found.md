---
title: "sudo - command not found?"
date: 2008-05-14
forum: General Help
---

### Post by subnet_rx on 2008-05-14
If I run sudo, I get some help information on the command.  If I run kdesu, I again get information.  If I run kate, it starts that program.  Trying to run kdesu or sudo kate and it says it cannot find kdesu (adept says it's installed) and sometimes says it cannot find kate.  How can I run a file editor as root so I can edit conf files?

---

### Post by badfish591 on 2008-05-14
well when i need to edit conf file i use 

```
sudo gedit /path/to/file
```

EDIT: oops i didn't see that you were running KDE maybe try

```
 sudo nano /path/to/file
```

---

### Post by geo909 on 2008-05-14
> **subnet_rx said:**
> If I run sudo, I get some help information on the command.  If I run kdesu, I again get information.  If I run kate, it starts that program.  Trying to run kdesu or sudo kate and it says it cannot find kdesu (adept says it's installed) and sometimes says it cannot find kate.  How can I run a file editor as root so I can edit conf files?

Hi, I'm not sure, but try 
```

su
<password>
kate

```

In Suse for example there are some things that you can run with su but not with sudo, don't know if that is the case for you..

---

### Post by inportb on 2008-05-14
Are you using Kubuntu-KDE4? If so, the right path is /usr/lib/kde4/bin/kate

You can also install kate (for KDE 3.5.9) for convenience.

---

