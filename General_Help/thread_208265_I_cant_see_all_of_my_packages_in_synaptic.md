---
title: "I cant see all of my packages in synaptic"
date: 2006-07-03
forum: General Help
---

### Post by slimdog360 on 2006-07-03
Something has gone wrong with ubuntu, when I use add/remove apps nothing loads up. When I use synaptic the only packages that I can see are the installed  ones. Also ubutnu does not update anymore. 
Does anyone know whats going on here and how to fix this?
thanks

---

### Post by Jagot on 2006-07-03
Could you post the results of this command:

```
cat /etc/apt/sources.list
```

---

### Post by slimdog360 on 2006-07-03
```
nick@nick-laptop:~$ cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory

```
im guessing thats not good

---

### Post by Jagot on 2006-07-03
Ok, run this command:

```
gksudo gedit /etc/apt/sources.list
```

Then copy all of this to the new text file:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```

Save the file and now run the following command:

```
sudo aptitude update
```

Or indeed load up Synaptic and hit reload or whatever it is.

---

### Post by slimdog360 on 2006-07-03
It worked, thank you very much.

---

