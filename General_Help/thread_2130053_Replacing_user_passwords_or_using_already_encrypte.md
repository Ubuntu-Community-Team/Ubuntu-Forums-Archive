---
title: "Replacing user passwords or using already encrypted passwords"
date: 2013-03-28
forum: General Help
---

### Post by cbillson on 2013-03-28
I posted this under security, though i fear it was the wrong place..

[INDENT][I]If i had two boxes, i added a user to one and set a password.

I then add the user to the second box using useradd.

How can i take the encrypted password from box 1 for input into box 2 - ideally something i can use in a shell script.

I've tried so far, searching and replacing, but the passwords contain  "/$." etc, I've also tried fully replacing the shadow file and cat  >> shadow, but this has mixed results usually ending with a blank  shadow file.

I can use passwd "user" but this required the typing of the unencrypted password.

I've noticed some of the user creation commands have the ability to take  an encrypted password, however i'm struggling with the syntax of this.

Ideally i'd like to be able to take the encrypted data from one box and  have a command such as - "command" "user" "encrypted data"

Any thoughts on how i can achieve this?

Cheers
chris[/I]
[/INDENT]

to simplify the question, is there any way i can take the already encrypted user password from one box and use it to reset the same users password on another box..?

[INDENT][/INDENT]
[INDENT][/INDENT]

---

### Post by hectorgrebbell on 2013-03-28
I presume you don't have root access to the second machine? It either sounds like you have forgotten a root password, or are trying to access something you shouldn't!
If the passwords are "common" then a lookup service is the simplest solution. I believe SHA-512 is in use.
You could script it, although it wouldnt be the simplest of things.

Im no expert but I find it unlikely you would be able to log in with the hash. Kind of removes the point of encrypting it if you could just lift the data off the disk..

If you have physical access to the machine then you could either boot into single-user mode or use a live-usb and modify the passwords file.

---

### Post by cbillson on 2013-03-28
Sorry, I've explained this really badly, mostly because i've tried a few ways of achieving this and they're sort of mashed up in my head.


The main goal is never having a plain text password stored anywhere.

I need to keep multiple servers user passwords in sync and unfortunately central management isnt going to work due to the layout.

Easy i thought.. change the passwords on one server (passwd 'user' 'password') and take the shadow file to replace the other box(es) - this didnt work for some reason, two issues:
[INDENT]upon using "mv shadow /etc" no users could log in, 
I also noticed that if i then used 'passwd user password' that i had a shadow file with a single entry :s
[/INDENT]

So then i thought, ok the format of shadow is user: x :hashofpassword: x : x : x <- replace either the entire line, or just the password with the new data (didnt work, mostly because the hash value contained !$/ etc)

So my last option is i have "hashofapassword" which i know resolves to 'blah' from manually updating box 1 (passwd user blah) - can i update the passwords on the other boxes using the encrypted data from a command - such as "'passwd' 'user' 'hashofapassword'"

my intent is the user always logs on with the unencrypted 'blah'

I notice that, useradd and some other commands have an encrypted switch, but i'm struggling to get these to accept this data.

---

### Post by hectorgrebbell on 2013-03-28
Well the first issue I can see with that is you would need the shadow, *gshadow,* passwd & group files.
Im pretty sure they are somewhat dependent on each other.
Give that a try, and if it still doesnt work i'll take a proper look.

It may also be worth looking into this if you aim to do it with the machines running
[http://www.cs.vassar.edu/cgi-bin/man/man2html?cppw+8](http://www.cs.vassar.edu/cgi-bin/man/man2html?cppw+8)

---

### Post by cbillson on 2013-03-28
I had shadow, passwd and groups, wasnt aware of gshadow so i'll take a look, thanks

---

### Post by hectorgrebbell on 2013-03-28
No Worries. Another consideration is are they all running the same OS? ie You haven't got a case of several different hash functions in use?

---

### Post by cbillson on 2013-03-28
All from the same base image, so same OS, configuration and patch level

---

### Post by hectorgrebbell on 2013-03-28
Well then as far as im aware if you have successfully copied all those files from one machine to the next it *should* work.

The smarter move would be to filter out system accounts (ie only copy user accounts with UID >= 500 and not 65534) then check for duplicates at the remote end and remove them before concatenating the new file to the old.
But if the configuration is identical that isn't strictly necessary.

---

### Post by cbillson on 2013-03-28
Ok, here are my steps..

adduser myuser

cat /etc/shadow
cat /etc/gshadow
cat /etc/group
cat /etc/passwd

(save each to a text file named the same, and used dos2unix.exe to change the formatting from MSDOS)

wget [http://mypc/shadow](http://mypc/shadow)
wget [http://mypc/gshadow](http://mypc/gshadow)
wget [http://mypc/group](http://mypc/group)
wget [http://mypc/passwd](http://mypc/passwd)

# capture to screen current ownership and file permissions

ls -l /etc/shadow
ls -l /etc/gshadow
ls -l /etc/group
ls -l /etc/passwd

chown xxx:xxx shadow (repeat for other three)
chmod xxx shadow (repeat for other three

mv * /etc



and now i cannot log on to the box :(

---

### Post by cbillson on 2013-03-28
I found my mistake - the dos2unix.exe command hadnt ran, these steps work!

Thanks for all the guidance

---

### Post by hectorgrebbell on 2013-03-28
Glad to have helped.

---

