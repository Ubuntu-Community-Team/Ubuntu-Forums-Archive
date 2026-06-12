---
title: "Installing from terminal, computer froze, now stuck"
date: 2012-11-20
forum: General Help
---

### Post by Aerion4 on 2012-11-20
Was trying to install openoffice from the terminal. My computer froze, now when i try to reinstall or uninstall openoffice, i get this error

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I've searched threads, and tried some of the unlocks provided, as well as killall -u, I still get nothnig...can anyone give me some advice?

---

### Post by Wim Sturkenboom on 2012-11-20
```

sudo rm /var/lib/dpkg/lock

```
The reason why you get the error is that the lockfile was not removed because of the crash. Above command will remove the lock file and everything should be OK.

You can play it a bit more safe (although to my knowledge it should not be necessary)

```

sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.x
// test now if your stuff is working; if it is run
sudo rm /var/lib/dpkg/lock.x

```
The first command moves the lock file out of the way, so you can test. The second command will remove the file permanently if you no longer need it.

---

### Post by Aerion4 on 2012-11-20
Oh man, Thank you so much. OO still wont work, but at least i can uninstall it now.

---

### Post by Wim Sturkenboom on 2012-11-21
Great; if you feel your problem is solved, please mark the thread as solved using the thread tools just above the first post.

---

