---
title: "SSH Client connection failure"
date: 2012-10-30
forum: General Help
---

### Post by souar on 2012-10-30
Hey

Using PuTTy to connect to my Openssh server worked fine for a while but has now stopped allowing me to connect. Instead I get the error 'No supported Authentication methods available (server sent: publickey)' 

Now I understand roughly what this means, Either the server or more likely my PC doesn't have the required key to be given access to the server but how do I fix this? I'm completely lost! 

Thanks

---

### Post by greenpeace on 2012-10-30
Hi!

Seems strange that the policy would have changed on the server without your knowledge... does someone else have access to it?

Have you used keys before?  Basically you make 2 of them, one is private and you NEVER share it with anyone.  Then there is a corresponding Public key which you install on all the servers you want to access.

So, you'll need to first [generate a public/private pair of keys]("http://kb.siteground.com/article/How_to_generate_an_SSH_key_on_Windows_using_PuTTY.html") 

Then, install and run pageant on windows, and add your private key to it.

Then, you'll need to find a way to include your public key on the server... normally in a file at ```
/home/<your user on server>/.ssh/authorized_keys
```.  It's just a text file, with one key per line and normally the lines are in the format:

ssh-rsa <long string of random characters> name@server

This last part may be tricky if you can't access the server... do you have another way to gain access to it?  Or a friend that can install your public key on it for you?

---

