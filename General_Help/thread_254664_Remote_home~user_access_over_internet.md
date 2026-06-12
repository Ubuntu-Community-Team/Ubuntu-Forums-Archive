---
title: "Remote /home/~user access over internet"
date: 2006-09-10
forum: General Help
---

### Post by mbmccormick on 2006-09-10
Hello. I have tried to get this to work many different times, and have failed. What I want to be able to do is access my home directory over the internet. However, my school blocks ssh, ftp, and vnc. I want to use a WebDAV share and be able to access my home directory over the internet. In my recent attempts to get the [http://localhost/~user](http://localhost/~user) capabilities in Apache to work, I always get a 403 error. All my permissions are correct. Anyways, not even sure if that is the road to take. But any help would be appreciated. Thanks.

---

### Post by mlind on 2006-09-10
You have probably enabled userdir module for apache httpd server?
Your $HOME directory probably needs o+x permissions.

What does /var/log/apache2/error.log contain ?

---

### Post by NiceGuy on 2006-09-10
I don't know any thing about webdav I'm afraid (never used it) but I was wondering how your school blocks ssh? Have you tried just using a different port eg. 2223 instead of the standard port 22?

---

### Post by mbmccormick on 2006-09-10
Well my school blocks SSH because the only external network ports they allow, meaning the only ports that connect to the internet, are 80 and 443. Besides, I can't be seen with an SSH client on computer even if i did change the ports.

But when and if I get userdir module to work, how would i link that to webdav?

---

### Post by NiceGuy on 2006-09-10
Hurm... I'm not so up on my networking but can't you just use port 80 then?

If there is some reason (and please tell me if there is - I'd like to know) then it might be worth trying [Hamachi]("http://www.hamachi.cc/") as people behind restrictive firewalls have had some success with it. I *think* its something to do with the fact you form a connection with the hamachi servers which then form a connection with your home pc so there is no 'incoming' connection as such and most firewalls block incoming connections not outgoing ones - but I'm not sure - I really need to do some more reading on my networking. :oops: 

However that doesn't really help you with not being seen with an ssh client... urm... so why is that exactly? Is it that you shouldn't be connecting with your home pc? If so... why?

---

### Post by Balut on 2006-09-10
Are you using Apache2?  If so, have you created a public_html directory in your home directory?  The apache2 userdir module looks for the public_html directory in all home directories for files that you wish to publish.  You will need to adjust permissions accordingly once you populate the public_html directory with files that you wish to access remotely.

---

