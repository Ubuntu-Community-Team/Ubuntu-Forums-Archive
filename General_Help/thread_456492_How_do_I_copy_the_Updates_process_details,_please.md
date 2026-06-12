---
title: "How do I copy the Updates process details, please?"
date: 2007-05-27
forum: General Help
---

### Post by dryder on 2007-05-27
Hi,

How do I copy the details of what happens during the Updates proces, please? I can see them but attempts to copy (and paste) don'r work.

I need to because all the updates I am currently being offered  tell me the are bugs in the packages and I want to be able to post those details for help.

Many thanks,

David

---

### Post by bung33 on 2007-05-28
You can't use Ctrl+C in the terminal because that is a reserved command. You'll have to select the text you want, then right-click and select copy...

---

### Post by dryder on 2007-05-28
> You can't use Ctrl+C in the terminal because that is a reserved command. You'll have to select the text you want, then right-click and select copy...

I have tried your suggestion but no menu comes up so I can copy.

I'm in the Details box showing the process of the update installation (or failure! :-( ) and those details just seem uncopyable.

Is there a way of getting the update via the terminal? I should be able to copy that if there is.

Many thanks,
David

---

### Post by bung33 on 2007-05-29
Type this command...

```
apt-get update
```

That will start the update procedure for all applicable packages...

---

### Post by Bigdog60 on 2007-05-29
Dude I dont think you can copy them into the terminal trying looking it up on google how to copy  update and then what your linux system is.

---

### Post by dryder on 2007-05-29
> Type this command...
Code:
apt-get update
Thanks bung33 but that only refreshes the repositories.

My Updates icon says there are 7 updates available and it is these I want to do via terminal so I can copy and paste the errors in all of them (for posting/help in this forum).

Bigdog60 - thanks.

Is there a log of the update process anywhere?
David

---

### Post by bung33 on 2007-05-29
Oops! I was behind Windows box at home when I posted last. I tested the command below on my Linux box at work...

```
apt-get upgrade
```

I get the two mixed up sometimes...

---

### Post by dryder on 2007-05-29
Thanks bung33,

Is it possible to nominate individual packages to upgrade?

I tried sudo apt-get upgrade [name of package] but no luck.

Sorry to be a pain but I really want to copy the error messages for each package.

Many thanks,

David

---

### Post by bung33 on 2007-05-30
Simply type the command...

```
sudo apt-get install <package>
```

If the package doesn't exist, then it gets installed. However, if the package exists, then it gets updated if an update is available...

---

### Post by louieb on 2007-05-30
```
sudo aptitude dist-upgrade 
```

Theres also  a way to redirect output  to a file similar to   
```
sudo aptitiude dist-upgrade  > update.listing
```

but I seem to remember there is something odd about using sudo and pipeing  can't remember if it applies to redirection also.

---

