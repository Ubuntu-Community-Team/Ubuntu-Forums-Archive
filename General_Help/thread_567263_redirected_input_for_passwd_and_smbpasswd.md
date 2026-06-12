---
title: "redirected input for passwd and smbpasswd"
date: 2007-10-04
forum: General Help
---

### Post by SteveHillier on 2007-10-04
Hi folks,
Maybe I am just trying to get too clever.
I want to set up a script so that I can set up domain users in one go.
So
I set up the script to get the username and password from the keyboard and store them in variables in the script file.
I then want to run useradd giving the username.

I would then like to call passwd using redirected input.  
sudo passwd $uname <pwdfile
I have tried echoing the password to a text file 'pwdfile'  (complete with trailing new lines) and then using <pwdfile for input.  No result - I cannot log on with that user.

I then tried cutting out the middle man and tried to use output from echo and pipe it into passwd.  
echo $pwd | sudo passwd $uname
I cannot log on with that user either

This is a process that I should surely be able to automate without too much aggravation.  Any hints would be useful.

Here is the script I have been using.  Please use your imagination to add and subtract hashes to make it work.

echo -n "please enter username: "
read uname
echo -n "please enter password: "
read pwd
#echo $pwd\\n >pwdfile

#echo -n "username is: "
#echo -n $uname
#echo -n ", password is: "
#echo $pwd
#echo -n "this will add the user: "
sudo useradd -m  $uname
#echo -n "this will add the password: "
#sudo passwd $uname
#sudo passwd $uname <pwdfile
echo $pwd $pwd | passwd $uname

#echo -n "this will add the samba password: "
#sudo smbpasswd -a $uname 

I once spent 3 months programming DOS batch files - maybe that sent me crazy and it's only just surfaced!!
Thanks

---

