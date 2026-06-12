---
title: "Solved"
date: 2023-04-04
forum: General Help
---

### Post by jimninja on 2023-04-04
YOU can Delete

Hi, 

when I try to updare (apt update) I got an error, I use brave browser-nightly:

```
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://brave-browser-apt-nightly.s3.brave.com stable InRelease' doesn't support architecture 'i386'
```

My sources :   ```
deb [signed-by=/usr/share/keyrings/brave-browser-nightly-archive-keyring.gpg] https://brave-browser-apt-nightly.s3.brave.com/ stable main
```

So I tried to add ```
[COLOR=var(--black-800)][FONT=var(--ff-mono)][arch=amd64][/FONT][/COLOR]
``` but it does not work, cause I have ```
[signed-by=/usr/share/keyrings/brave-browser-nightly-archive-keyring.gpg
``` before the ```
https://
```

what do you think?

---

### Post by deadflowr on 2023-04-04
Add it to the end like
```
deb [signed-by=/usr/share/keyrings/brave-browser-nightly-archive-keyring.gpg **arch=amd64**] https://brave-browser-apt-nightly.s3.brave.com/ stable main
```

---

