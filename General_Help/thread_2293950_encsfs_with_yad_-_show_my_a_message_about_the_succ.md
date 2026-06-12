---
title: "encsfs with yad - show my a message about the success of the command"
date: 2015-09-08
forum: General Help
---

### Post by Michael_Richardsso on 2015-09-08
hi,

i'm using this little script to mount a decrypted folder and show my a window where i can enter the password:

```
encfs ~/.decrypt ~/encrypt --extpass="yad --on-top --timeout=10 --timeout-indicator=bottom --width=300 --entry  --hide-text --center --text 'Enter Password:' --button='OK' --title Password"
```

when the password is correct the folder will be mounted, but there is not message about that, something like "done" would be enough. i couldn't find something like that in the yad manpage. but i think i have to "catch" the output thats normally shown in the terminal and show this in a window, or something like that. but i have not idea how to realize that.

---

