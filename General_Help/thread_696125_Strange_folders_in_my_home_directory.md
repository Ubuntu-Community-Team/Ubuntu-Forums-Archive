---
title: "Strange folders in my home directory"
date: 2008-02-13
forum: General Help
---

### Post by NotPhil on 2008-02-13
I just found a directory called file: in my home folder. It contains /home/[username]/Desktop. I've trashed it, but it reappears when I reboot.

When I select >View >Show Hidden Files in my home directory, I see the usual gunk, along with three folders named .fr-[six random numbers and letters]. Each of these contains ~/Documents/[one of several subdirectories]/[all of the contents of that directory].

The file: folder is just irritating, but the .fr-* folders appear to be complete copies of other directories, and they're chewing up disk space for no reason I can see.

Does anyone know what these folders are and how I can get rid of them?

---

### Post by nemilar on 2008-02-13
That's strange, I've never heard of that... Do the files reappear when you login, or only when you reboot?

---

### Post by NotPhil on 2008-02-13
> **nemilar said:**
> That's strange, I've never heard of that... Do the files reappear when you login, or only when you reboot?The file: folder didn't reappear after just logging out and logging back in. But I have trashed it before, and it, eventually, shows up again.

---

### Post by Shazaam on 2008-02-13
Re the "file:" folder,  that is also on my Gutsy system so I wouldn't worry. As far as the ff files I haven't a clue.

---

### Post by Trail on 2008-02-14
I don't have any such files. 

Check the owner/group and creation date of those files, maybe they give a clue.

My initial thought is that some sort of script or application might not be configured correctly or misbehaves. Try to 'grep' for the '.fr-' part or something?

---

### Post by NotPhil on 2008-02-14
I've trashed the .fr* files. They haven't come back yet and their absence hasn't caused any problems that I've noticed.

My best guess is that they were temporary files created by File Roller while I was trying — unsuccessfully, at first — to unpack some large archives. They may have been left behind after File Rolled stopped processing the tarballs. 

(Or not.)

---

### Post by stevejesus on 2008-02-14
I have this too.
For the sake of burying my head in the sand...  What is it?

---

### Post by NotPhil on 2008-02-15
> **stevejesus said:**
> IWhat is it?Just a bug, I'm guessing. Getting rid of them doesn't seem to hurt.

---

### Post by pPrdrm on 2008-02-15
Have you used **File Roller** to **unzip/untar** compressed files? I thing this happens when you open compressed files from within **Firefox**. I'm not saying this for sure. It's just an observation. It's not happening all the time also. Maybe it happens only when **Firefox** crash and it doesn't have time to erase this temporary folders. See inside them. Does their content remind you something?

---

### Post by jespdj on 2008-02-15
I've also noticed a "file:" folder sometimes and deleted it.

I think it comes from a bug in some program, which doesn't handle URLs correctly - it seems that it incorrectly uses an URL where it should have used a directory or filename. But I have no idea which program is doing this.

---

