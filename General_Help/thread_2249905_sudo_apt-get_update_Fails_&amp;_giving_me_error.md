---
title: "sudo apt-get update: Fails &amp; giving me error"
date: 2014-10-25
forum: General Help
---

### Post by christoph5 on 2014-10-25
ater i run a long shell script to install alot of apps and programs it crashed right inmidle of the whole instalation and i had nothing else to do than stop it 
and after that many programs which should have ben installed are not finished and fails to open 

when i try sudo apt-get update now i just get a error saying something like: 
```
E: Type ' deb ' eh unknown at line 1 in source list /etc/apt/sources.list.d/libdvdcss.list

```
saying something because this error above was translated to english from my norwegian language system in google translator

also adding the shell script file here if can be to some help,[SIZE=5][FONT=comic sans ms]
[ATTACH]257483[/ATTACH][/FONT][/SIZE]
thank you[SIZE=5]  [FONT=comic sans ms] [/FONT][/SIZE]

---

### Post by mc4man on 2014-10-25
1. your script is adding ' to the start & end of the videolan source entries, get rid of them, improper & not needed in script
2. there apparently is no public key available
3. the package builds are currently the same as what is acquired thru the /usr/share/doc/libdvdread4/install-css.sh script so no current advantage to adding the videolan repo

---

### Post by christoph5 on 2014-10-25
are you telling me to remove ever &#8217; signs in the entire script and run it again in terminal ?
will the sudo apt-get update  be fixed then also?

---

### Post by mc4man on 2014-10-25
Didn't run your script - 
This is what that section should be - 
```
echo deb http://download.videolan.org/pub/debian/stable/ / | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
echo deb-src http://download.videolan.org/pub/debian/stable/ / | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list
```

Overall I'm saying why bother, earlier in your script you ran - 
sudo /usr/share/doc/libdvdread4/install-css.sh
So libdvdcss2 should have been installed & the videolan repo does not offer a later package

Personally I'd edit /etc/apt/sources.list.d/libdvdcss.list with a root text editor to remove the 4 ', then open software sources & remove the repo altogether (or just delete /etc/apt/sources.list.d/libdvdcss.list itself

---

### Post by christoph5 on 2014-10-26
sudo apt-get update works now better as i removed the dots ', but i am still getting this at the end off sudo apt-get update
> W : GPG - Error : [http://download.videolan.org](http://download.videolan.org) Release: The following signatures could not be verified because the public key is not eh loan: NO_PUBKEY 6BCA5E4DB84288D9

---

### Post by mc4man on 2014-10-26
> but i am still getting this at the end off sudo apt-get update

> **mc4man said:**
> 1. ...
2. there apparently is no public key available
3. .....
As mentioned..

---

### Post by christoph5 on 2014-10-26
ok so i deleted the libdvdcss.list file and not getting any errors anymore, what was that file for anyway?

---

### Post by mc4man on 2014-10-26
> **christoph5 said:**
> ok so i deleted the libdvdcss.list file and not getting any errors anymore, what was that file for anyway?

That's where ppa  or other repos source info is stored when you add them

---

### Post by oldos2er on 2014-10-26
Add the key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6BCA5E4DB84288D9

sudo apt-get update
```

---

### Post by christoph5 on 2014-10-28
> **oldos2er said:**
> Add the key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6BCA5E4DB84288D9

sudo apt-get update
```

can i ask why should i add the key now as i have deleted the libdvdcss.list file?

---

### Post by oldos2er on 2014-10-28
If you no longer use the repository, the key is superfluous. In case you ever add it back to your sources though, it would be handy to have.

---

