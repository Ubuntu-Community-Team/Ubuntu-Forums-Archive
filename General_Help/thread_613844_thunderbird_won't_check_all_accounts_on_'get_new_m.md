---
title: "thunderbird won't check all accounts on 'get new messages'. how do i fix this?"
date: 2007-11-15
forum: General Help
---

### Post by antiplex on 2007-11-15
hi there!

i'Ve migrated my account settings and emails for like 3 times now (winXP -> edgy -> feisty -> gutsy) and basically everythings is still working fine with one exception:
when i click on the 'get mails' button and then input the correct password on the prompt only one of my 5 accounts gets checked (always the same)! even if i choose 'check all accounts' from the buttons submenu only this specific account is checked.
i've set up my accounts to check automatically every x minutes (using different values) and this mechanism still works (without having to enter any more passwords or error messages), but i would also want thunderbird to check all my accounts if i choose this option.
anybody had this? solutions? suggestions?

regards, anti

---

### Post by NT4usB on 2007-11-15
POP accounts, or IMAP, or both?
Why are you getting a password request? By choice? 
Put the password in, and save it. Lets get it to fetch mail without asking for the password(s)
What happens if you hit:
Ctrl+Shift+t

---

### Post by antiplex on 2007-11-17
oooups, seems i forgot to give some more details...
its thunderbird 2.0.0.6 and there are 4 pop accounts specified which all dont get checked automatically no more and one imap account that still does.
the password request comes because i have enabled the set-masterpassword-to-encrypt-stored-account-passwords-option, but the matter is the same even when i disable this feature (just checked it).

the effect of ctrl+shift+t is also that only the imap-account gets checked.

i took a look at the about:config dialog and found that some of the *mail.server.server<number>* entries appear a bit weird so i guess i have to try to set up thunderbird from scratch and integrate my existing folderstructure and emails then.
somewhere i read something about an entry *mail.server.server1.defer_get_new_mail* that should be set to true but i can't find this field at all in my config. 
so i wonder if this was referring to a prior version of thunderbird or if i should add these  entries... hmmm

any ideas?

---

