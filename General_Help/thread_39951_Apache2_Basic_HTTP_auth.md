---
title: "Apache2 Basic HTTP auth"
date: 2005-06-07
forum: General Help
---

### Post by Sandomaphone on 2005-06-07
Hi!

I'm having a tad bit of trouble with Hoary's Basic HTTP Authentication with Apache2.

The web authentication dialogue in FireFox \ IE  appears, but no matter what account i put in to the Username \ Password box, none work, despite the fact that my .htpasswd is setup properly.  I am not sure, but I can't find any of the auth programs like ncsa_auth, smb_auth, etc.  Aren't those needed for proper HTTP Authentication?

Also, I've opted for not having a .htaccess file in the to-be password protected directory, instead placing the authentication syntax in the <Directory> tags in /etc/apache2/sites-avaliable/default.  And that works fine, however, is it OK to do that?


Any ideas?

Thanks,

Sandomaphone

---

### Post by Mez on 2005-06-07
shouldnt be a probelm

have you create dthe .htpasswd file manbaully r what

Are you referencing the file properly>

remember usernames/passwords are CASE SENSITIVE so this may be why

---

### Post by Sandomaphone on 2005-06-07
Don't worry.  Got it working.

I think the password encrytion wasn't MD5 or something weird.  So I fell back on htpasswd (command)...  Now to my PHP sockets and stuff....isn't PHP such an awesome language! \\:D/

---

