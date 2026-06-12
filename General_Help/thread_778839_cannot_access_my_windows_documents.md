---
title: "cannot access my windows documents"
date: 2008-05-02
forum: General Help
---

### Post by grandoud on 2008-05-02
i have installed Hardy with Wubi under WXP. In the /host folder I can see all the folders of my hard disk including Documents and Settings, but my personal user folder does not appear in Docs+settings. I have given the same user name and password on both  systems, thinking the problem might come from those being different at first, but it still does not work.

---

### Post by ago on 2008-05-02
Do you have any special char in the folder name? Like accented letters and such?

---

### Post by shortee on 2008-05-02
Same problem here, no special chars.

---

### Post by grandoud on 2008-05-02
no special chars either in user name or password.
but there are accented letters in the folder name, and so far Windows refuses to rename it.
I will keep trying - that must be the cause for the problem

---

### Post by ago on 2008-05-02
Try to access them as root (watch what you do as root under Linux though).

Open a terminal and type

sudo -s
ls -al /host/path/to/your/documents

---

### Post by charlieddayton on 2008-05-02
The problem is the security setting on your My documents folder in windows.

You have to go to windows right click on the folder and select sharing, now enable sharing and you should be able to see your files from Ubuntu.

---

### Post by grandoud on 2008-05-03
no, it is due to the presence of accented letters in the folder and file names.
see [https://bugs.launchpad.net/wubi/+bug/136682](https://bugs.launchpad.net/wubi/+bug/136682)

I found that info via ubuntu-fr.org

---

