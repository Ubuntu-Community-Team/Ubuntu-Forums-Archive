---
title: "expect spawn sshfs does not mount!"
date: 2013-08-27
forum: General Help
---

### Post by marisdembovskis on 2013-08-27
Hi. 
Have my-expect file in home. 
#my-expect
#!/usr/bin/expect -f
spawn sshfs [email]my-user@my-site.com[/email]:/ /home/jeeeee/ftp/
expect "my-user@my-site.com's password:"
send "my-pasword\n"
#end of my expect

I do ./my-expect file

and it does not mount directory, however it 100% mounts dir if I do 
sshfs [email]my-user@my-site.com[/email]:/ /home/jeeeee/ftp/
and type password and hit enter!


Any ideas, what is wrong?

---

