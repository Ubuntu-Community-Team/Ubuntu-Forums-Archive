---
title: "how do i make install form my hard drive"
date: 2007-07-16
forum: General Help
---

### Post by dragonwings on 2007-07-16
i would like to make a copy of my hard drive which has 7.04 ubuntu  on it .
iv finally got everything working again after THE BIG CRASH 
when i had to reinstall everything using 56k dail up ,i was gutted

so i want to make an install dvd9 disk  that i can just pop into my computer and click install.
my current set up is 8.3 gb i could uninstall a few games if i had to make it smaller

is this possible???

---

### Post by Vajra Vrtti on 2007-07-16
I think your main concern is about the software you've installed from the repositories. Although I haven't used it yet, it seems to me that [APTonCD]("http://aptoncd.sourceforge.net/") is what you need.

---

### Post by Vajra Vrtti on 2007-07-16
APTonCD is in the Ubuntu repository.

---

### Post by Motoxrdude on 2007-07-16
Yes, use [remastersys]("http://www.linuxmint.com/wiki/index.php/Remastersys")
Once you have that installed, run
```
sudo remastersys backup
```

---

### Post by dragonwings on 2007-07-16
thanks for your help guys i will let you know how i get on

---

### Post by dragonwings on 2007-07-16
i made 2disks with remastersys  1/bacup
                                                           2/dir
both of these boot as a live disk
                        
but when i click install it askes for password my password does not work 

why is this??

---

### Post by dragonwings on 2007-07-31
ok made custom iso with remasrersys it boots as live cd with all my stuff on it 
it installs to hard drive fine 
but when i try to boot hard drive it loads grub then gos to next stage (loading bar) and stops there .

as i have just found out these files appear to be empty 
when installed to hard drive.

root
proc
opt
sys
srv
tmp
lost+found
initrd

---

