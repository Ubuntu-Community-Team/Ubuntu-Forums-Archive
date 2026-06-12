---
title: "[SOLVED] Simplest Dual Boot Solution"
date: 2008-06-11
forum: General Help
---

### Post by BUSHYBOB on 2008-06-11
I have a spare computer that I use for testing and general mucking about with.

I have two drives, one with xp and the other with hardy. At the moment I use them separately, unplugging one and plugging in the other.

I want to leave both connected i.e. one as master, the other as slave.

I've decided that there two ways I can accomplish this

1. Make hardy master and xp slave and edit the menu.lst file on hardy to add xp to the grub menu

2. Make xp master and hardy slave and use a live cd to create a new grub menu.

Which would be the simplest solution?

---

### Post by fooman on 2008-06-11
heres how i did mine when i first installed linux (suse)....  i did not want to mess up my xp install so i disconnected it during the suse install and reattached it afterwards.  i then used the bios to choose which os to boot from.  when i got tired of going into the bios each boot to change between the 2...i then edited my menu.lst file to include the xp drive.  when i installed ubuntu on a third drive,  i repeated the same procedure and now have the choice of 3 os when i boot up (using ubuntu's grub).

btw,  it should not matter which is master or slave as your bios can determine which drive to boot from in the boot order.  on my setup,  suse is on the master drive,  ubuntu on the slave, xp is on a sata raid array.  i have the bios set to boot from the primary ide's slave drive.

the advantage to this setup is that all my os's were installed independently of each other,  so i can disconnect any of them (or if one should fail) and still boot from the others.

---

### Post by BUSHYBOB on 2008-06-11
Went with option 1. which didn't work until Iadded these two lines to the xp entry in menu.lst

map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by Shobuz99 on 2008-06-11
Bushybob,
Exactly what I did. One thing I messed up was the syntax of the map strings.
I didn't space them properly and got "error 13 unrecognized device string" 
Here's the reason:

map (hd0,hd1) (hd1,hd0)   -wrong-

map (hd0,hd1) [COLOR="White"].[/COLOR](hd1,hd0)  -right-

Other than that, it worked fine.

Shobuz99

---

