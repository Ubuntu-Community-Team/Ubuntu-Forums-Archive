---
title: "[SOLVED] I Forgot how"
date: 2008-05-19
forum: General Help
---

### Post by Kilroth on 2008-05-19
OK I had to format and reinstall Ubuntu 8.04 I backed up my music as MP3 CD and tried to move it onto the new install and now all the folders have a padlock on them so I need the code to fix my permissions I'm really new at this and last time this happened I had some one do this for me and I really didn't learn from it

---

### Post by aysiu on 2008-05-19
> **Kilroth said:**
> Ok I had to format and reinstall Ubuntu 8.04 I backed up my music as MP3 CD and tryed to move it onto the new install and now all the folders have a padlock on them so I need to I installed thunar but I forgot what I had to do to change the permisons so I can keep the files but lose the padlock if someone can help that would be great
Type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R kilroth:kilroth /path/to/moved/mp3/files/
``` assuming *kilroth* is your username and substituting in your actual path to the moved files instead of /path/to/moved/mp3/files.

For example, if your username were *rothkil* and your MP3s were in a folder called *music* on your desktop, the command would be ```
sudo chown -R rothkil:rothkil ~/Desktop/music/
```

---

### Post by Kilroth on 2008-05-19
Why THank you

---

