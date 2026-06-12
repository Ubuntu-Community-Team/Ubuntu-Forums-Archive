---
title: "How can I free space?"
date: 2007-04-11
forum: General Help
---

### Post by KIAaze on 2007-04-11
Hi,

I have separate "/", "/home" and "/usr" partitions.
Unfortunately, I am running out of space on my "/" partition now. (I only assigned it 2GB, which was not enough apparently).
Now I can't login normally anymore and have to use a special mode similar to the windows safe-mode.

How can I free some space on my root partition?
Can I delete the contents of "/tmp" and "/var/tmp"?

Is it possible to safely move "/var" onto my home partition? And if so, how?

---

### Post by ffxr on 2007-04-11
2gb is enough for a minimal install, but u probably need 10-15gb at least to give your system some space to breathe...

are you sure your / /home & /usr are really on different partitions?
what size are each of these?

you can delete the files in /tmp & /var/tmp safely enough as you have suggested, but i a would be tempted to back up and reinstall into a much larger partition now... ( i have a 40-gb / partition) before you go any further,, as this problem will not go away... and its better to resolve it now and not be constantly nagged by it in the future..

---

### Post by pointone on 2007-04-11
localepurge can free up a good 50 to 100 MB of space on some systems.

```
sudo apt-get install localepurge
```

Also, clean up your apt!

```
sudo apt-get clean

sudo apt-get autoremove
```

---

### Post by Kizilbas on 2007-04-11
Thank you very much pointone, these commands r great and very useful !

---

