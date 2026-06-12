---
title: "[SOLVED] arguments in bash aliases"
date: 2008-05-24
forum: General Help
---

### Post by moep on 2008-05-24
Howdy, I'm trying to make two bash aliases that allow me to encrypt and decrypt different filetypes in the terminal, but I can't quite get them to work:


alias enc='openssl enc -aes-256-cbc -salt -in $1 -out $1.enc'
alias dec='openssl dec -aes-256-cbc -salt -in $1.enc -out $1'

My experience with bash-scripting is very limited, but shouldn't the first alias allow me to type "enc file.txt", prompt me for a password and then save the aes-256 encrypted file as "file.txt.enc" while "dec file.txt" would decrypt it?
Using the two aliases just prints a list of all openssl options, as if I supplied an invalid argument. :confused:

---

### Post by omababy on 2008-05-24
You can't use arguments in alias's in this way, you need to make a bash function. Like this:

function enc {
 openssl enc -aes-256-cbc -salt -in $1 -out $1.enc
}

function dec {
 openssl dec -aes-256-cbc -salt -in $1.enc -out $1
}

---

### Post by unutbu on 2008-05-24
You can make an executable shell script:
```
#!/bin/bash
openssl enc -aes-256-cbc -salt -in $1 -out $1.enc
```

Save it in a file called 'enc'. Make it executable:
```
chmod 755 enc
```

---

### Post by moep on 2008-05-24
thanks a lot both of you. this is why I love the ubuntu community! :wink:

for completeness, these are the correct (working) commands — not sure why I invented the non-existing "dec" argument in the OP:

```
openssl enc -aes-256-cbc -salt -in $1 -out $1.enc
openssl enc -d -aes-256-cbc -salt -in $1.enc -out $1
```

---

