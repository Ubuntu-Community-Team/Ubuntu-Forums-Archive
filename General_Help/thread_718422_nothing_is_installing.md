---
title: "nothing is installing"
date: 2008-03-08
forum: General Help
---

### Post by pidgeon on 2008-03-08
i've been trying to install automatix2 for almost 5 hours. it's not working. i don't understand what's going wrong. this is what i get:

leapfrog@lilypad:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
--02:21:43--  [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
           => `automatix2.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 64.69.36.51
Connecting to www.getautomatix.com|64.69.36.51|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [application/pgp-keys]

100%[====================================>] 1,706         --.--K/s

02:21:43 (29.58 MB/s) - `automatix2.key' saved [1706/1706]

leapfrog@lilypad:~$ gpg --import automatix2.key
gpg: directory `/home/leapfrog/.gnupg' created
gpg: new configuration file `/home/leapfrog/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/leapfrog/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/leapfrog/.gnupg/secring.gpg' created
gpg: keyring `/home/leapfrog/.gnupg/pubring.gpg' created
gpg: /home/leapfrog/.gnupg/trustdb.gpg: trustdb created
gpg: key E23C5FC3: public key "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
leapfrog@lilypad:~$ pg --export --armor E23C5FC3 | sudo apt-key add -
pg: illegal option -- -export
pg: Usage: pg [-number] [-p string] [-cefnrs] [+line] [+/pattern/] [files]
gpg: no valid OpenPGP data found.
leapfrog@lilypad:~$ gpg --keyserver subkeys.pgp.net --recv CC919A31E23C5FC3
gpg: requesting key E23C5FC3 from hkp server subkeys.pgp.net
gpg: key E23C5FC3: "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" 8 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 8
leapfrog@lilypad:~$ gpg --export --armor CC919A31E23C5FC3 | sudo apt-key add -
gpg: no ultimately trusted keys found
OK
leapfrog@lilypad:~$
leapfrog@lilypad:~$ sudo aptitude update
E: Type 'Automatix' is not known on line 38 in source list /etc/apt/sources.listE: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Type 'Automatix' is not known on line 38 in source list /etc/apt/sources.listE: The list of sources could not be read.
leapfrog@lilypad:~$ sudo aptitude install automatix2
E: Type 'Automatix' is not known on line 38 in source list /etc/apt/sources.listE: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Type 'Automatix' is not known on line 38 in source list /etc/apt/sources.listE: The list of sources could not be read.
leapfrog@lilypad:~$



help...

---

### Post by 3rdalbum on 2008-03-08
The first error message is saying that you have an error in the file "/etc/apt/sources.list".

In the terminal, type this:

```
sudo gedit /etc/apt/sources.list
```

It opens the gedit text editor as administrator, and displays the file.

On line 38 of your file, it looks like you've put the word "Automatix" in. All legitimate lines in this file start with the word "deb", or "deb-src", or a hash "#". Put a # symbol before the line that begins "Automatix".

Save your changes and close Gedit. Now you can run the command "sudo aptitude update" without problems.

EXPLANATION:
Any line beginning with a hash symbol is designated to be a comment, and is not read by the package management system. Therefore, by putting a hash before the line that is giving Aptitude the error, you are "commenting out" the offending line so it is not read.

---

### Post by pidgeon on 2008-03-08
when i do that it says application finalized called

---

### Post by boeing777 on 2008-03-08
Ubuntu 7.10 (Gutsy AMD64)

[http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb)
Ubuntu 7.10 (Gutsy i386)

[http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb)
Ubuntu 7.04 (Feisty i386)

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb)
Ubuntu 7.04 (Feisty AMD64)

[http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/automatix2_1.1-4.6-7.04feisty_amd64.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/automatix2_1.1-4.6-7.04feisty_amd64.deb) 

download one of these depending on your pc, then run the installer

---

### Post by pidgeon on 2008-03-08
how do i do that?

---

### Post by boeing777 on 2008-03-08
download it and open it

---

### Post by pidgeon on 2008-03-08
i did that and something opened and closed right away.

---

### Post by pidgeon on 2008-03-08
i got into the source list, but, now, when i try to update it says 

E: Malformed line 37 in source list /etc/apt/sources.list (dist parse)

what's that mean?

---

### Post by unutbu on 2008-03-08
It probably means you have more bad lines in your sources.list.
If you post the output to
```

cat /etc/apt/sources.list

```
we will probably be able to clear up the problem faster.

---

### Post by pidgeon on 2008-03-08
this is what came up

leapfrog@lilypad:~$ cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal
 
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) b

leapfrog@lilypad:~$

---

### Post by unutbu on 2008-03-08
Comment out the very last line (the 37th) in your sources.list.
Or, if you need it, you need to fix the last word. 'b' is not proper.

---

### Post by unutbu on 2008-03-08
Perhaps you meant:
```

deb http://www.albertomilone.com/drivers/edgy/latest/3 2bit binary/

```

Notice there is a space between the 3 and the 2.

The above was mentioned here:
[http://ubuntuforums.org/archive/index.php/t-326592.html](http://ubuntuforums.org/archive/index.php/t-326592.html)

---

### Post by pidgeon on 2008-03-08
thanks!!!! it worked ^.^

---

