---
title: "Firefox 3 has gone crazy"
date: 2008-06-16
forum: General Help
---

### Post by KillaW0lf04 on 2008-06-16
Hey guys. Today i was on firefox 3 watching a video, when all of a sudden it closes on its own. Now i wasnt really worried becouse it had done it quite a few times before and all i had to do was start it again, but this time firefox seems to have gone crazy, cant really explain it, but my bookmarks are all gone, address bar doesnt seem to be functioning poporly, history doesnt work and on the error console, errors keep popping up. I tried completely removing it and installing it again from synaptic, but its remained the same! What can i do????

---

### Post by ivze on 2008-06-16
First variant - you can trash the whole firefox configs:
1)open terminal
2)execute
```

rm -rf .mozilla

```
This will nuke the whole data (bookmarks, setup...) from your current firefox, however, i strongly believe that this will help.

---

### Post by KillaW0lf04 on 2008-06-16
It worked! Thanks!

---

### Post by viciouslime on 2008-06-16
Just in case anyone else stumbles across this post, a better idea is perhaps to use the command "mv .mozilla .mozilla-old" that way, if it doesn't work, you can use the command "mv .mozilla-old .mozilla" to restore your firefox preferences.

Or, for those who prefer to do everything graphically, open your home dir in nautilus from the places menu, press ctrl + h to show hidden folders, find the .mozilla folder and rename it to something else, try firefox, if firefox still doesn't work correctly, repeat the process to rename the folder to .mozilla again.

---

### Post by chickendude1313 on 2008-08-28
Yo, I know I'm bumping an old thread but I think my solution to this is pertinent.

I had this problem and I found this thread googling around and I fixed it without nuking anything.

Basically, the problem arose when I ran an installer as sudo which changed some permissions on my firefox directory. You can check if this is your problem by running 
ls -lR ~/.mozilla | grep root and seeing if any root ownerships are flying around.

You can fix it like this:
1) Close firefox (very important)
2) Pull open a terminal. Run these commands:

[code]
cd
sudo chown -R $USER .mozilla
sudo chgrp -R $USER .mozilla
[code]
Where $USER is of course, your username.

They change the file and group ownerships of all your mozilla files back to you.

Voila, it should be better. You can check permissions to see if they are yours again.

---

