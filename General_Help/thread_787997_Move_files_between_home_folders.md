---
title: "Move files between home folders"
date: 2008-05-09
forum: General Help
---

### Post by JohanSwe on 2008-05-09
*I got files in an old user's home folder that I need to move to my new users home folder, but I get "permission denied".*

I'm logged in as my new user. And I can open files in my old users home folder and I can move them to another folder in the same home folder, but when I try to move a file to my new users home folder I get a message saying "permission denied". 

I also open Nautilus with gksudo but still get "permission denied"

How can I move files between users' home folders?

---

### Post by vdawg on 2008-05-09
Use a terminal to take ownership of the olduser's folder and files.

sudo chown -R you:yourgroup /home/olduser

where you is your username, yourgroup is the group you belong to, and /home/olduser is the path of the oldusers home folder.

---

### Post by JohanSwe on 2008-05-10
After changing ownership on the old users home folder with containing files I could move the files to my new users home filder, thanks.

What I cant understand though is that I could not move the files as user root (gksudo) in nautilus that should have all permissions..

---

### Post by vdawg on 2008-05-16
Agreed, it is a little bizzare... however it may be a safety feature as you really shouldn't be working as root, imagine if you deleted /usr or something like that :p

Cheers!

---

