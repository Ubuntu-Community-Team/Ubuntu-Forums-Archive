---
title: "[SOLVED] amarok won't open"
date: 2007-06-25
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-06-25
Some times I use amarok on my Feisty machine. Today it does not want to open. i tried typing it in terminal and nothing happens.
Any one have a clue as to what else I should try? I've uninstalled and reinstalled it and same thing.
Thanks, Sally:)

---

### Post by r0ck80y on 2007-06-25
Type amarok in console and send the output to a file```

amarok 2> file
```
You can look for errors in the file. Post the file here or relevant sections if still in doubt

---

### Post by AndyCooll on 2007-06-25
Another option is to delete the Amarok folder in your profile. Its a hidden file under /home/yourname/.kde/apps/amarok ...I think. CTRL+H will unhide the hidden files. Backup the folder first (just in case you've got any playlists, artwork etc that you might want to retrieve).

:cool:

---

### Post by IusedTObeSOMEONEelse on 2007-06-25
> **r0ck80y said:**
> Type amarok in console and send the output to a file```

amarok 2> file
```
You can look for errors in the file. Post the file here or relevant sections if still in doubt

Thanks for responding:)
I have typed amarok in console and nothing comes out as I sat and waited for over 15 minutes

---

### Post by r0ck80y on 2007-06-25
Did you type the command exactly as i posted? What errors/warnings did you see in "file" ? Also you can follow andycooll's suggestion.

---

### Post by IusedTObeSOMEONEelse on 2007-06-25
> **AndyCooll said:**
> Another option is to delete the Amarok folder in your profile. Its a hidden file under /home/yourname/.kde/apps/amarok ...I think. CTRL+H will unhide the hidden files. Backup the folder first (just in case you've got any playlists, artwork etc that you might want to retrieve).

:cool:

Ok, so I deleted that and reinstalled and still it won't work. Just a quick flash on desktop and no amarok.
thanks for reply, Sally

---

### Post by IusedTObeSOMEONEelse on 2007-06-25
> **r0ck80y said:**
> Did you type the command exactly as i posted? What errors/warnings did you see in "file" ? Also you can follow andycooll's suggestion.

Yes I did and still nothing. 
I'm stumped:(

---

### Post by r0ck80y on 2007-06-25
Can you post the contents of that file? Right now i can't think of anything that might explain your problem.

---

### Post by IusedTObeSOMEONEelse on 2007-06-25
Ok, I deleted the amarok file and rebooted machine, reinstalled amarok and BINGO!!!
Got it going. I still not sure what the trauma was but thanks for help/suggestions as I'm sure one of them did the trick.

Sally

---

