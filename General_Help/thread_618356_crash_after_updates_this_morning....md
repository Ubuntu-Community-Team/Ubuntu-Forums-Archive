---
title: "crash after updates this morning..."
date: 2007-11-20
forum: General Help
---

### Post by ginnie6 on 2007-11-20
I had about 10 updates this morning...and I didn't pay attention to what they were. After I did them I could no longer access my home folder or any other folder. Like a dummy I shut down and restarted......only now I cannot get into ubuntu at all. it just hangs after login. I have so much stuff on there that is not backed up that I really need to save. Can anyone help?

---

### Post by taurus on 2007-11-20
See if you can boot into recovery mode from GRUB menu and post the outputs of these commands.

```
df -h
ls -la /home
```

---

### Post by ginnie6 on 2007-11-20
I can access them but any tips on how to post them here since I have to boot into windows to get online? short of typing it all by hand that is.

---

### Post by taurus on 2007-11-20
You can access Ubuntu partition with this app, [http://www.fs-driver.org/](http://www.fs-driver.org/).  However, the first command needs to be run while booting in Ubuntu.  Just want to check your space to make sure you don't fill it all up.

```
df -h
```

p.s.  But if up have an USB thumbdrive, you can just save the outputs into a file and copy it to a thumbdrive.  Then, paste it here when you boot into windows.

---

### Post by ginnie6 on 2007-11-20
> **taurus said:**
> You can access Ubuntu partition with this app, [http://www.fs-driver.org/](http://www.fs-driver.org/).  However, the first command needs to be run while booting in Ubuntu.  Just want to check your space to make sure you don't fill it all up.

```
df -h
```

p.s.  But if up have an USB thumbdrive, you can just save the outputs into a file and copy it to a thumbdrive.  Then, paste it here when you boot into windows.

Thank you! that just enabled me to get into ubuntu and back up the things I didn't have backed up. Now I'm just going to do a clean install since the last few days the system has been kinda flakey anyway.

---

