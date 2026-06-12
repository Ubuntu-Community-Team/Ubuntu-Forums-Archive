---
title: "Make Bootable DVD"
date: 2007-11-21
forum: General Help
---

### Post by Tsarevich on 2007-11-21
[FONT="Arial"][SIZE="2"]I have a copied Mandriva 2007.1 DVD on my hard drive. I want to burn it on a DVD. Remember, it is NOT an ISO, instead, it is like a repository. Is it possible for me to drag the files Release Notes and i586 to the CD/DVD Creator folder and burn it. Would it be bootable? Please don't tell me the wrong way because blank DVDs are costly.[/SIZE][/FONT]

---

### Post by p_quarles on 2007-11-21
I'm not exactly sure what you have, but the Mandriva DVD is available in .ISO format. 

Anyway, no, if you just put a bunch of files on a DVD, it won't be bootable. It's possible that these are the files for the DVD installer, and you could just make them into a bootable image using mkisofs, but if you're concerned about wasting a disk I wouldn't do that. 

Anyway, Mandriva's download mirrors are a bit frustrating, but here's how you can explore the directories and find the correct DVD image:
1) Go to the Mandriva download page
2) Select a country and then a server
3) *Cancel *the download
4) Right-click on the link that says "click here if your download does not begin automatically," and then select "copy link location."
5) Paste that URL into your web browser, delete the file name at the end of the URL, and hit enter.

Now you will be in the directory of all available downloads.

---

