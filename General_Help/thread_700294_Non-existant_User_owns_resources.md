---
title: "Non-existant User owns resources"
date: 2008-02-18
forum: General Help
---

### Post by mcdirt on 2008-02-18
Hi, I hope you can help. I'm using Ubuntu 7.10 and it has been great so far but today I made an account for my wife which she said she wouldn't use so I deleted the user again, let's call it UserX.

Later on, I rebooted the machine and it wouldn't boot into the Graphic Desktop, just left me in the command line if you like. I got that fixed after reading lots of forum postings and then it booted into the graphic desktop OK but then it said that HALfailed to initialise and it wouldn't connect to the net, read USB drives etc.

So back onto the forums to read more. Upshot is that I was looking at the file system in the Terminal using ls -l and noticed that instead of everything being Owner:root and Group:root everything is Owner:root Group:UserX - yes, the deleted user! Don't know how I managed it but how do I get myself out of this pickle without having to reinstall the whole OS. Please help.


rgds McDirt[

---

### Post by danwood76 on 2008-02-18
well not everything in your filesystem will have the same permissions.
Though I think that all the directories bar the /home are owned by root solely.

You could try doing

```

sudo chown -R root:root *

```

then you would need to go into home and re own your home folder
```

cd /home
sudo chown -R YOURUSERNAME:YOURUSERNAME YOURUSERNAME

```

There is a possibility that this might break something else.
But you would probably have already done a similar command to the first one to break it in the first place.

The only real way to fix a permission problem like this is to re install, but I would try this first as what do you have to loose?

---

