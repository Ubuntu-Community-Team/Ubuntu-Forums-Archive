---
title: "Could not open the file /home/ddarnell/Desktop/i…-prerelease-6.0.0beta2.sh."
date: 2006-11-04
forum: General Help
---

### Post by UchihanoKonoha on 2006-11-04
I had downloaded crossover and tried to install it and an error came up as i have shown in the title the following message also came with the error 

"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I don't know what i need to do to get it working can someone please help me im in a bind.

---

### Post by Kateikyoushi on 2006-11-04
Try to use this command but replace the install file with the one you downloaded.

```
sh install-crossover-pro-5.0.3.sh
```

Crossover install guide. [LINK]("http://www.codeweavers.com/support/docs/crossover-pro/install")

---

### Post by UchihanoKonoha on 2006-11-04
I still can't seem to get it working it keeps saying "can't find file or directory"

---

### Post by ~LoKe on 2006-11-04
> **UchihanoKonoha said:**
> I still can't seem to get it working it keeps saying "can't find file or directory"

```
cd ~/Desktop && sudo sh *-prerelease*.sh
```

---

### Post by UchihanoKonoha on 2006-11-04
OK got it i just had to give it permissions to execute.

---

