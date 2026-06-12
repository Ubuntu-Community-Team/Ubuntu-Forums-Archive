---
title: "Having problem as root using su"
date: 2007-09-04
forum: General Help
---

### Post by zamie on 2007-09-04
Hi there

       While I was trying to add a new user in my laptop(ubantu 7.04) I changed the mode to all of the files belongs to /home ( zamie1 and user1 ) using " chmod 644 .* " .Later on I found my self unable to login as zamie.Then again I logged in as root in to the text mode and type the following command  “chamod 777 -R /home/zamie”. Now I can login in a dektop mode but I am having two problems which are below

1. when I log in as zamie it shows me an error
   
  $HOMME ./dmrc should be owned by the user ..... use 644

2. I can not login as root from user zamie using su( from the command prompt in the ubantu desktop) 

   zamie:$ su 
   password:
   invaliad  login

Any body has any idea how to solve those problems

Thanks

Regards
zamie

---

### Post by Warren Watts on 2007-09-04
Ubuntu does not allow users to log in as root or su to root.

Instead, prefix your command with "sudo", annd enter your user password when prompted.

example:

```
sudo chmod 755 myfile.ext
```

---

