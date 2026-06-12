---
title: "How do I get rid of Ubuntu security?"
date: 2007-07-31
forum: General Help
---

### Post by rubperezt on 2007-07-31
my computer is now NASA SECURE i cannot even create a folder because I DONT HAVE Permits however my acc is the only acc in the system and is the main acc (su) still it wont ask for any password. i would like to know how can i get rid of all that unnecessary security that is only making it all worse.
I just tried to install a program and the installer coulndt create the directory (could not create a directory called seamonkey in the parent directory /usr/local so i tried to make it manually, but i couldnt, i had to go to terminal and write sudo mkdir...... and enter password just to create a directory, then the installer couldnt install the program because i had no permits. I wonder who has? after all i created it futhermore im the only with access to this pc :)
thanks, any help would be greatly appreciated!

---

### Post by Nekiruhs on 2007-07-31
As far as I know, you cant. Just run the install as sudo (sudo /path/to/installer). The way *Nix based OSes work is that, even though you may be the only user, your not admin. That is reserved for root. Root is the user you cant login as. You can use sudo from the CLI and gksudo for the GUI to act as it. This is so that if you get a malicious virus/trogan/thing it cant harm your entire computer. Use sudo for anything that needs root permission.

---

### Post by rubperezt on 2007-07-31
doesnt work.  it says. bash command doesnt exist or something like that. I checked the name fore typos etc and was fine, I even run command dir to check the file was there.

---

### Post by Nekiruhs on 2007-07-31
> **rubperezt said:**
> doesnt work.  it says. bash command doesnt exist or something like that. I checked the name fore typos etc and was fine, I even run command dir to check the file was there.what and where is the installer?

---

### Post by rubperezt on 2007-07-31
I just run a dir command and it returned this:

[I]me@me-desktop:~/Desktop/seamonkey-installer$ dir
config.ini     MPL-1.1.txt  seamonkey-installer      xpi
installer.ini  README       seamonkey-installer-bin
me@me-desktop:~/Desktop/seamonkey-installer$ [/I]

[I]then i run
me@me-desktop:~/Desktop/seamonkey-installer$ seamonkey-installer
bash: seamonkey-installer:[COLOR="Red"] command not found[/COLOR][/I]
or
[I]me@me-desktop:~/Desktop/seamonkey-installer$ sudo seamonkey-installer
Password:
sudo: seamonkey-installer: [COLOR="Red"]command not found[/COLOR][/I]3

Also i did the same two steps with the file seamonkey-installer-bin just in case. they por perfectly in the GUI until it ask to create the folder, im guessing that if I chose another folder, maybe withing my user folder i wont have any trouble but i rather leave it in the default one.

---

### Post by aysiu on 2007-07-31
```
cd ~/Desktop/seamonkey-installer
gksudo ./seamonkey-installer
``` More details on SeaMonkey installation:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

Read more about permissions here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Your Ubuntu is not NASA secure. If you wanted it to be NASA secure, you'd use SELinux:
[http://en.wikipedia.org/wiki/SELinux](http://en.wikipedia.org/wiki/SELinux)

---

### Post by rubperezt on 2007-07-31
ok thanks that worked! i cannot believe i was missing ./! :lolflag:
im new into linux and i was getting frustrated already. BTW im actually installing seamonkey because my firefox is more like a wetkitty instead, it will crash without any apparent reason whenever there is any flash page, no error nothing, i have browsed for help on forums but i havent found anything that actually works. do anyone have any suggestion what to do?

---

### Post by aysiu on 2007-07-31
> **rubperezt said:**
> ok thanks that worked! i cannot believe i was missing ./! :lolflag:
im new into linux and i was getting frustrated already. BTW im actually installing seamonkey because my firefox is more like a wetkitty instead, it will crash without any apparent reason whenever there is any flash page, no error nothing, i have browsed for help on forums but i havent found anything that actually works. do anyone have any suggestion what to do?
Maybe one of these might help?
[Solution to flash-related Firefox 2 crash in Edgy](http://ubuntuforums.org/showthread.php?p=1672572#post1672572)
[flash making firefox crash !](http://ubuntuforums.org/showthread.php?p=1263006#post1263006)

---

### Post by rubperezt on 2007-07-31
> **aysiu said:**
> ```
cd ~/Desktop/seamonkey-installer
gksudo ./seamonkey-installer
``` More details on SeaMonkey installation:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

Read more about permissions here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Your Ubuntu is not NASA secure. If you wanted it to be NASA secure, you'd use SELinux:
[http://en.wikipedia.org/wiki/SELinux](http://en.wikipedia.org/wiki/SELinux)

actually i kinda hate so much insecure security. how secure is my home if i cannot enter to it?

---

### Post by aysiu on 2007-07-31
> **rubperezt said:**
> actually i kinda hate so much insecure security. how secure is my home if i cannot enter to it?
Well, you can enter it... you just need a key. Think of it more like your bank account. You need proper identification or an ATM card and PIN number. Otherwise, you're just walking around with wads of cash, ready to be mugged.

---

### Post by rubperezt on 2007-08-01
i just think that this Paranoic-like security without the option to reject it can be as bad as no security at all, especially in an OS designed for desktop usage. after all who will ever want to steal my homework? or my last year vacation? u might say Credit Card information but there are thousands of places where people could obtain CC# easier than a home pc.
problem resolved, not with firefox yet but im on it, thanks for your help!

---

