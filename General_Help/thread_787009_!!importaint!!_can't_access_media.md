---
title: "!!importaint!! can't access /media"
date: 2008-05-08
forum: General Help
---

### Post by foxofinfinety on 2008-05-08
any one knows why eveytime I try to go to the /media folder I only get "unable to enter **file:///media.** You do not have access rights to this lovation" even wile I'm the onwer of the PC!!!

---

### Post by TomasJancik on 2008-05-08
didn't you change the permissions anyhow?
what says the *ls -l /media*?

---

### Post by drs305 on 2008-05-08
The simple solution is probably to change the owner to the user, if others won't be using it:

```
sudo chown -R yourusername:usergroup /media
```

---

### Post by chrisccoulson on 2008-05-08
If you've played around with the permissions on /media, then to set them back to default:
```
sudo chown root:root /media
sudo chmod 755 /media
```

---

### Post by foxofinfinety on 2008-05-08
> **TomasJancik said:**
> didn't you change the permissions anyhow?
what says the *ls -l /media*?
premision denied
> **drs305 said:**
> The simple solution is probably to change the owner to the user, if others won't be using it:

```
sudo chown -R yourusername:usergroup /media
```
how do I know what use group to use (I'm new to Linux)

---

### Post by drs305 on 2008-05-08
> **foxofinfinety said:**
> premision denied

how do I know what use group to use (I'm new to Linux)

The solution presented by chrisccoulson is probably a better one as it keeps things more in line with ubuntu's hierarchy and would be better should you add other users later.

In answer to your question, if you haven't made any additional groups, you probably have one named the same as your username. Alternatively, you can just omit the colon and group name altogether if you haven't any and don't plan on having groups on the computer.

---

### Post by drs305 on 2008-05-08
deleted: double posting

---

### Post by foxofinfinety on 2008-05-08
> **chrisccoulson said:**
> If you've played around with the permissions on /media, then to set them back to default:
```
sudo chown root:root /media
sudo chmod 755 /media
```
if I have to use them with the run command action then it doesn't work withs is not to strange as I never changed a setting accept for the background (withs is also gone now)

edit: don't ask me how be to day I can access the /media folder
edit2: it seems like I can access it if I don't use a USB pen drive

---

