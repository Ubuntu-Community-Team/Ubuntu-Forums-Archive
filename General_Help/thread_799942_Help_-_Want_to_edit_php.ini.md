---
title: "Help - Want to edit php.ini"
date: 2008-05-19
forum: General Help
---

### Post by Sticky on 2008-05-19
I realize this is a really stupid question but I've been searching the forum and I can't find the answer so apologies if it's there.  How can I give myself the right to edit and save files such as php.ini in the etc/ folder.  I just get a message telling me I can't because I'm not root.  I'm assuming ther's a simple command I can put in the terminal to enable myself to do this "sudo ....." but I don't know what it is.

Help!!

---

### Post by drs305 on 2008-05-19
```
gksudo gedit /etc/php/php.ini
```

You might want to back the file up first:
```
sudo cp /etc/php/php.ini /etc/php.ini.bak
```

If you are the only one who wil access this file, you could also change the ownership to yourself:
```
sudo chown username:usergroup /etc/php.ini
```
Disclaimer: This might be convenient if you intend on editing the file often but I do not know what the php file/app is or who else might be using it.

---

### Post by Sticky on 2008-05-19
Thank you - it didn't occur to me to open gedit that way to do it.

---

### Post by cdtech on 2008-05-19
I just sudo pico /etc/php5/php.ini

Are you trying to change the max memory allowed to run scripts?

---

### Post by drs305 on 2008-05-19
I was going off the address in the original post, but I noted the address used by cdtech, which seems more likely. If the php.ini file is indeed in /etc/php/php.ini , then the command in my previous post would change. If you used the original command it would create a new file.

I have gone back and edited the previous post to make gedit open the correct file.

---

### Post by Sticky on 2008-05-19
Cheers guys - all really helpful stuff.

@drs305 - I had worked out that the path was wrong and self-corrected.  I'm not a complete noobie but I've become so Windows conditioned it takes real effort to work a different way.  I'm trying hard to ditch MS products completely at home.

I may change the file permissions permanently in the long term.  I'm installing Moodle (it's a virtual learning environment) on my laptop for development purposes and so therefore I did need to change the memory limit (@ cdtech).

---

