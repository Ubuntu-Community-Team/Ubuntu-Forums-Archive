---
title: "Renaming user, without new home directory / moving home directory"
date: 2007-12-10
forum: General Help
---

### Post by BSSPenfold on 2007-12-10
Hi all - I'm pretty new here. I've been using ubuntu for about 6 months now, but mainly through GUI, not much terminal.

I recently bought a PC that will be functioning as a mythbuntu/mythtv server. The pre-installation of mythbuntu was part of the package, which is fine. Before I was going to get everything setup, I decided to change the username from 'user' to 'myth'. I did this using the 'System > Administration > Users and Goups' panel. I changed all instances of 'user' to 'myth', including the home directory field.

You can probably tell what is coming...

I logged out, ready to login as 'myth' with my new password, but now I can't login because I didn't create a home directory for 'myth' (or leave it as '/home/user'). Instead I get two errors (one after the other):

```
User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
```

...followed by

```
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see of you can fix this problem.
```

There are some additional detailed errors her about "cannot create directory '/home/myth' " (and all the default sub directories like Documents, Video etc are listed here, along with other hidden directories.

I thought I'd try to be clever and use the fail-safe terminal to create a directory for 'myth' using

```
sudo mkdir /home/myth
```

which seemed to go ok. I then attempted to copy the whole of '/home/user' to '/home/myth' using:

```
cd /home/user
```
```
sudo cp -r * /home/myth
```

(^ If my memory serves me correctly)

This seemed to have copied at least some files, so I was hopeful that things would work, but they didn't.

One noticable point though, is that not as many errors now show. For instance, only the '.config', '.cache' and '.ICEauthority' directories seem to be a problem.

Nevertheless, I don't want to create a fresh home directory - I still want to use exactly the same preferences I had before for 'user', but just with a different username/login.

This is really embarrassing, and I now realize what a stupid mistake this was to make. :(

If anyone can help me to either get the new '/home/myth' directory working (with all my existing preferences from '/home/user'), OR to just get things back as they were with a 'user' login it would be unbelievably helpful. Even if I can just tell the 'myth' account to use '/home/user' as it's home directory, I presume everything would resort to normalness?

Many thanks in advance for any help you might be able to give.

If any of what I have said is unclear, or if more info/details are required, please say.

---

### Post by Vadi on 2007-12-10
> usermod -l newname oldname

:)

(it might need a sudo in front)

---

### Post by mdurham on 2007-12-10
Vadi wrote:
> usermod -l newname oldname
from man usermod:
> -l, --login NEW_LOGIN
    The name of the user will be changed from  LOGIN to  NEW_LOGIN. Nothing else is changed. In particular, the user's home directory name should probably be changed to reflect the new login name.

---

### Post by BSSPenfold on 2007-12-11
Thanks guys. So once this is done, is there a way to change the account's home directory back to the original '/home/user'?

---

### Post by BSSPenfold on 2007-12-12
> **mdurham said:**
> Vadi wrote:

from man usermod:

Thanks mdurham. How do I change the account to use a different home folder? (via the terminal)

---

