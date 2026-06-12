---
title: "Need help retrieving Firefox password"
date: 2008-06-26
forum: General Help
---

### Post by rouge568 on 2008-06-26
Ok, so I have completely forgot my ubuntu brainstorm password and I am wondering if anyone here can help me in my quest to get it back.
I tried emailing myself a new password, but -doh!- I must have used a throwaway address because neither of my two main ones worked. also, none of my frequent passwords that I use, (~7 of them) worked either. It was not saved in firefox because I recently did a complete reinstall for hardy and just never went on brainstorm since then. So I was sitting here, considering emailing the brainstorm guys to try and convince them that it was really I trying to get my password back when I remembered that I had it saved on firefox at my school. I checked, and sure enough they hadn't yet wiped the servers for the summer. I was able to retrieve the key3.db and signons2.txt files, the latter of which had a brainstorm password listing. Unfortunately, it is encrypted. Through Google, I found that the key3.db file was used by firefox to decrypt it, but I am not sure how, short of overriding my currently saved passwords. Any advice on how to decrypt it? They all start with MDoEEPgAAAAAAAAAAAAAAAAAAAEwFAYIKoZIhvcNAwcEC.

If it is of importance, my school use FF2 on Windows while I use FF3rc1 on Ubuntu.

Thanks!

---

### Post by ryanhaigh on 2008-06-26
If you can access your school profile why not just grab it all (should be pretty small), temporarily move your current profile to a different location, copy the school profile to the default location, firefox 3 will then import everything and you should be able to get to your old passwords.

---

### Post by rouge568 on 2008-06-27
Cool - it worked! I can't believe I didn't think about that before hand.

However, my password/login still doesn't work - I'm gonna go ask the brainstorm admins.

---

### Post by hackerb9 on 2009-09-30
Just a quick tip for anyone else who finds this thread via Google: you don't need to move files around at all or even quit Firefox to quickly check the passwords. You can change the HOME directory for a single process by setting the HOME environment variable from the command line like so:

[FONT="Courier New"]
machine:~$  **ls /path/to/backup/directory/.mozilla**
appreg  extensions  firefox
machine:~$  **HOME=/path/to/backup/directory firefox -no-remote**
[/FONT]

Check the passwords in the new web browser that pops up as usual (from Edit -> Preferences -> Security -> Saved Passwords).

Since the HOME environment variable was set from the command line just for that one firefox process, you don't have to do anything to undo it.

--b9

---

