---
title: "Xubuntu-Noble engrampa won't open .7z archive."
date: 2024-06-01
forum: General Help
---

### Post by ajgreeny on 2024-06-01
Xubuntu-Noble engrampa won't open a simple password protected .7z archive of files needing low security simply to hide the contents of them away from others for a while.
This worked fine in 22.04 but in 24.04 it fails telling me there is no application available.  I have all the same archiver and unarchiver packages as I had in 22.04 and create the 7z archive by right clicking the original .txt file.

I know there are other archive filetypes that work in this way which I can use but I'm just interested to find out why this no longer works with 7z archives in 24.04.
I'm baffled; any thoughts or ideas?

---

### Post by &amp;KyT$0P# on 2024-06-02
Can you open them any other way?
Do you have package [FONT=monospace]7zip[/FONT] installed?

---

### Post by ajgreeny on 2024-06-02
> **halogen2 said:**
> Can you open them any other way?
Do you have package [FONT=monospace]7zip[/FONT] installed?
Yes, I do and I have also tried adding p7zip-full and p7zip-rar but it doesn't help.

My workaround has been to create a** .war** archive which behaves as I want and expect, but I'm still baffled.

---

### Post by Yellow Pasque on 2024-06-02
I can't reproduce it (works for me). Is there something different I should have tried?

Open caja, right click on a text file and select Compress...
Choose 7z as the format and add a password
Right click the new file and open with engrampa

---

