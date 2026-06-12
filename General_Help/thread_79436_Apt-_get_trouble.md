---
title: "Apt- get trouble"
date: 2005-10-20
forum: General Help
---

### Post by Minyaliel on 2005-10-20
It won't work! I discovered the ubuntu guide and tried some of the stuff described there (dearly missed my LimeWire, for instance), but it wouldn't work. This happened some days ago, was too intimidated to try again (8-[  ) but it wouldn't surprise me if it refused to work again. I can't even install breezy...

---

### Post by Jenda on 2005-10-20
Could you be a little more specific? We can't help you if all you tell us is that it don't work.
What doesn't work? What commands did you issue? What were the error messages?
Don't give up. Most problems get solved, All it takes is patience.

---

### Post by Minyaliel on 2005-10-20
[http://www.ubuntuguide.org/#limewire](http://www.ubuntuguide.org/#limewire) this is one of those things I tried to do. As I'm on a Windows XP school computer right now, can't quote the error messages I got on my laptop (that's where I installed Ubuntu)... :P But it wouldn't install it. I tried several of the commands listed in the giude apart from this, with no better results. Then I tried upgrading to Breezy, but I'm still on Hoary. Err... this is as close as I can describe it right now...

---

### Post by Jenda on 2005-10-20
Did you enable the repositories? If you haven't added the universe and multiverse repos, this will help you: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Now, AFAIK, you shouldn't really need these for LimeWire. If you followed the guide, then you would first try to install Java Rentime Environment. The guide won't help you there, because it has been removed from the repos for legal reasons (damm'em lawyers). You will have to follow this guide here: [http://www.ubuntuforums.org/showpost.php?p=315094&postcount=10](http://www.ubuntuforums.org/showpost.php?p=315094&postcount=10)
That should work. If not, search the fora - I know I found the solution here.

The next step downloads a package. If you had trouble here, the server or your connection was down, IMO.
Then comes
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
After these two steps, LimeWire is already installed, all that is left is a symbolic link. I NEED to know which step fails.

---

### Post by Minyaliel on 2005-10-21
minyaliel@minyaliel:~$ sudo mkdir /usr/local/java
Password:
minyaliel@minyaliel:~$ cd /usr/local/java
minyaliel@minyaliel:/usr/local/java$ sudo chmod +x /home/%username%/jre-1_5_0_04-linux-i586.bin
chmod: cannot access `/home/%username%/jre-1_5_0_04-linux-i586.bin': Ingen slik fil eller filkatalog
minyaliel@minyaliel:/usr/local/java$


It won't recognise the package, for one thing :P strange.

---

### Post by gbusse on 2005-10-21
Are you typing the command exactly as you have shown. If you are, I don't think you should be typeing the:

%username%

But instead should be typing your username instead...

Also, I just checked and the latest file you will download from Sun per the link above is not:

jre-1_5_0_04-linux-i586.bin

but is:

jre-1_5_0_05-linux-i586.bin

So, first of all check to make sure you can see the file in your home directory by typing:

ls -l ~

Then where ever it says:

/home/%username%

I would type:

~

Instead as it is the shortcut for your home directory.

Good Luck,
Gordo

---

### Post by Jenda on 2005-10-21
That is:
```
/usr/local/java$ sudo chmod +x /home/minyaliel/jre-1_5_0_04-linux-i586.bin
```

---

### Post by Minyaliel on 2005-10-21
It just keeps telling me there is "no such file or catalogue"... (bad translation, but anyway) I've tried what both of you suggested. It's weird, but...

Self edit: 

I tried installing with apt- get again, but got the same error messages as last time... look:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: You may want to run apt-get update to correct these problems

Only trouble here again is that I get the same error message in a bigger scale when typing apt-get update.

---

### Post by Jenda on 2005-10-22
Whoa... No more Mirrormax. Why do you have those repos in your sources.list? They are outdated:
```
sudo gedit /etc/apt/sources.list
```
delete the line that contains both "mirrormax" and "backports". Save & exit.

Now try whatever you had trouble with again.

---

### Post by Minyaliel on 2005-10-22
Right, that seemed to do the trick :) Thanks a lot ;)

---

### Post by Minyaliel on 2005-10-22
No - wait... again, an error message when trying to install java. What is wrong?

minyaliel@minyaliel:/usr/local/java$ sudo /home/minyaliel/jre-1_5_0_05-linux-i586.bin
sudo: /home/minyaliel/jre-1_5_0_05-linux-i586.bin: command not found

---

### Post by Jenda on 2005-10-22
did you "sudo chmod +x /home/minyaliel/jre-1_5_0_04-linux-i586.bin"?

---

### Post by Minyaliel on 2005-10-22
Yeah, I did. Well, anyway I managed to work it out and have LimeWire installed on my laptop (FINALLY! lol). Thanks for your help :)

---

### Post by Jenda on 2005-10-22
You're welcome. Glad it works, in the end.

---

