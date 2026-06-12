---
title: "Cannot log in"
date: 2006-10-11
forum: General Help
---

### Post by SteffJay on 2006-10-11
I am having problems logging into my usual account (not Root). When the pc reboots, i get a little window on the screen which displays:

**bash: /devs/null/: Permission denied** :confused: 

There are about 30 odd lines all displaying the same thing. If i close the window, it takes me to the log in prompt where i can access the Root with password, thats ok. What has gone wrong ? Can i resurect my normal login ? I cannot create another user with admin rights because the Root does not show **Users / Groups** :(  Any help would be greatly appreciated.

---

### Post by jimbren on 2006-10-11
I did a google search on your error and got [this]("http://forums.suselinuxsupport.de/index.php?showtopic=2180&hl=null") from the Suse forums.  It seems to mesh with what you're describing.

So you need to log in as root and do the following:
```
chmod -c 777 /dev/null
```

From there, you should be able to log out of your root session and then into your normal session.

Hope this helps,

jimbo

---

### Post by SteffJay on 2006-10-11
Thank's Jimbo. I;ll give that a bash.....  (excuse the phun)...  ;)

---

