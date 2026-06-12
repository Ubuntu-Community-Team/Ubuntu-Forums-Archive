---
title: "leafpad stopped reading files?"
date: 2019-07-06
forum: General Help
---

### Post by iamtheeggman2 on 2019-07-06
Hi,

I had a file that had text in it and leafpad would usually be the editor of choice to opent he file allow me to make notes and save them, however, for smoe weird reason, it only showed me the letter "p" which lead me to believe while happy in the haze of a drunken hour, i had accidentally copied and pasted the letter p over my entire lot of note-taking, this meant i ended up taking a backup copy of the text file and replacing the one that had recent notes so now i lost a lot of notes! Anyhow, abiword i just discovered will open the file and show me the contents properly. Whats going on with this then? i just reinstalled leafpad via synaptic however i still just see the letter p!

---

### Post by Impavidus on 2019-07-06
Is it still a plain text file? Abiword may save it as something different, that leafpad cannot read. Try```
file path/to/file
```to find out the filetype. And are leafpad and abiword opening the same file?

It seems rather implausible that leafpad would show the wrong contents of a plain text file.

---

### Post by iamtheeggman2 on 2019-07-07
when i right click view properties it says "plain text document" - cant be a permisions thing if abiword opens it either. file extension is .txt

```
home@home-System-Product-Name:/media/home/7474-2B26$ file Important\ Details.txt 
Important Details.txt: ASCII text, with CRLF line terminators


```

---

### Post by iamtheeggman2 on 2019-07-09
ok well i copied and pasted the file to another usb drive as i believed the usb drive might have been faulty however leafpad still just presents the letter p in the newly copied file yet abiword opens it up.

anyway i have opened up t in abiword, copied and pasted to a new leafpad file and saved over the original file and it opens up in leafpad again. shame i didnt think to open with a new program such as abiword before i overwrote it with an old backp of the file.

---

