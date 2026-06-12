---
title: "Help! Repository Problems!!!"
date: 2007-04-21
forum: General Help
---

### Post by blfer on 2007-04-21
Thanks in advance for any help offered.
Last night I tried to add to my repository list and I have now locked out any updates.

I am using Ubuntu L6.06 on an old Dell Optiplex.
This particular system runs really well with Ubuntu and I'd really like to fix it. I have read alot of posts, but not been able to find any definitive answers to the problem(s). 

Again, thanks in advance.

---

### Post by blfer on 2007-04-21
O.K. just tried to use the terminal to fix the problem. Here is what it came back with:

E: Type 'sudo' is not known on line 42 in source list /etc/apt/sources.list
E: Type 'sudo' is not known on line 42 in source list /etc/apt/sources.list
E: The list of sources could not be read.

How do I fix this?
Thanks.

---

### Post by eyelessfade on 2007-04-21
Please post your /etc/source.list

looks that you have something bad stuff in there.

---

### Post by Famicommie on 2007-04-21
Yes, please post your sources.lst as it seems like you actually have the word "sudo" in one of the lines pointing to a repository. My guess is that you simply need to remove the word sudo from the offending line and it should start working again. However, post your sources.lst so we can be sure.

---

### Post by blfer on 2007-04-21
O.K. Thanks again. Here is the Sources list:




## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.




#AUTOMATIX REPOS START








#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/dapper.list](http://medibuntu.sos-sts.com/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/medibuntu.list


I went searching for this last night and tried to edit it several times --- to no avail.

---

### Post by eyelessfade on 2007-04-21
remove last line: "sudo..." and you are good to go again :)

update:
Next time you post a config file, you don't have to post the lines starts with a "#" since that is only a comment.
I say this because some config files can be thousands of lines ;)

---

### Post by blfer on 2007-04-21
Thank you.

Alright, how do I do that? I know that I have to edit this line --- How do I do it?

---

### Post by Famicommie on 2007-04-22
sudo gedit /etc/sources.list

By using sudo, you should give yourself permission to edit sources.list

---

### Post by blfer on 2007-04-22
O.K. That works!!!! Thanks again, I learned something new and helpful,
Thanks again to all who helped.
Blfer

---

