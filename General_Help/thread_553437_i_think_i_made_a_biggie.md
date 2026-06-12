---
title: "i think i made a biggie"
date: 2007-09-17
forum: General Help
---

### Post by aimran on 2007-09-17
I did this... 

sudo chmod -x /usr/bin 

:P... Now most system files can't run... any help? :(

PS: Don't ask me why I did that...

---

### Post by southernman on 2007-09-17
Your avatar is what I look like (other than being a gal) resisting the urge to ask.... errr!

Why did you do that? Sorry couldn't help it!

You'll need to boot off of a live cd of some sort, mount the / partition and fix the permissions.

---

### Post by bettlebrox on 2007-09-17
This should fix it:
chmod 755 /usr/bin

If you can't run the command, boot to fail-safe mode and try it.

---

### Post by rsambuca on 2007-09-17
Mind if I ask why you did that? :)

---

### Post by southernman on 2007-09-17
> **bettlebrox said:**
> This should fix it:
chmod 755 /usr/bin

If you can't run the command, boot to fail-safe mode and try it.

Can you clarify why you would change the permissions from 644 to 755? 

It isn't that the permissions themselves where changed, in as much as the executing of the programs were removed. I know, in my original post I said *fix the permissions*, but what I should have said was fix the execution removal.

---

### Post by adamjs on 2007-09-17
try

sudo chmod a+x /usr/bin

---

### Post by aimran on 2007-09-18
thanks for the help(s) :) 

yes I was silly and did it while sleepy... thats why hehe :P

---

### Post by exile on 2007-09-18
aimran, I feel your pain. I once wrote 0 bits over my entire entertainment media disk and had to re-rip my entire CD/DVD collection. It was a cut and paste job from a chunk of sample code form the web.. I accidentally hit the middle mouse button paste into an opened root shell and it had the trailing carriage return in it. :(

SUDO is your friend. So are backups. Hell of a way to learn it though.

Good luck.

---

### Post by bettlebrox on 2007-09-18
> **southernman said:**
> Can you clarify why you would change the permissions from 644 to 755? 

It isn't that the permissions themselves where changed, in as much as the executing of the programs were removed. I know, in my original post I said *fix the permissions*, but what I should have said was fix the execution removal.
You need execute permissions on the directory so you can access or execute the files in the directory.

---

### Post by southernman on 2007-09-18
> **bettlebrox said:**
> You need execute permissions on the directory so you can access or execute the files in the directory.

I understand that part, but looking at my /usr/bin it's of course owned by root, and the perms are set at 644. Looking further at the individual scripts inside this directory, the perms are the same, but the execute box is checked enabling them to be run as a program.

That's all the OP did, was remove the allowing of them to be run as programs.

I'm not understand the reason for doing 755 on the directory... just seems like it's only effectively opening up a hole for crackers. <--- *shrugs*

---

### Post by bettlebrox on 2007-09-19
Google is your friend. ;)

From [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

[INDENT]x - Execute permission. Whether the file may be executed. [I]In the case of a
directory, this attribute decides whether you have permission to enter,
run a search through that directory or execute some program from that
directory.
[/I][/INDENT]

So without the execute bit set on the directory, you *cannot* cd to the directory, read the contents of the directory, nor see what is in the directory. 

>I'm not understand the reason for doing 755 on the directory... just seems like it's only effectively opening up a hole for crackers. <--- *shrugs*

If you did 777 it would! 755 is the default setting for that directory. Look at the permissions on the directory:

[INDENT] ls -ld /usr/bin
drwxr-xr-x 2 root root 68K 2007-09-18 02:14 /usr/bin/[/INDENT]

The *d* means it's a directory.  The first *rwx,* represents the permission for the *owner* of the directory, in this case root, has full rights over the directory.  Then the next 3 bits, *r-x* means anyone in the group that the directory is in, can read and execute in the directory.  The last 3 bits, *r-x* are the settings for *everyone* else in the directory. This only mean they can look in the directory and run any executable files in the directory. It does not mean they can create or edit any of the files in the directory.

Whew! Sorry for the long paragraph, I hope it make sense. It does take some time to get used to how Linux/UNIX permissions work.

---

### Post by southernman on 2007-09-19
> **bettlebrox said:**
> 
Google is your friend. ;)
Ok.. I had that coming! :)
> So without the execute bit set on the directory, you *cannot* cd to the directory, read the contents of the directory, nor see what is in the directory. 

If you did 777 it would! 755 is the default setting for that directory. Look at the permissions on the directory:


ls -ld /usr/bin
drwxr-xr-x 2 root root 68K 2007-09-18 02:14 /usr/bin/
and if the terminal shows it as *drwxrwxrwx 2 root root 68K 2007-09-18 02:14 /usr/bin/* would be the same as 777
I'll blame the confusion on the different way that the nautilus dialogue properties window, showed the permissions! ;) That's my story and I'm sticking to it... 



> The *d* means it's a directory.  The first *rwx,* represents the permission for the *owner* of the directory, in this case root, has full rights over the directory.  Then the next 3 bits, *r-x* means anyone in the group that the directory is in, can read and execute in the directory.  The last 3 bits, *r-x* are the settings for *everyone* else in the directory. This only mean they can look in the directory and run any executable files in the directory. It does not mean they can create or edit any of the files in the directory.

Whew! Sorry for the long paragraph, I hope it make sense. It does take some time to get used to how Linux/UNIX permissions work.


bettlebrox, I really appreciate you taking the time to explain it to me like a two year old! Had I looked at the perms via the terminal in the first place, I'd have known. (Forest meet Trees)

Again, Thanks!

---

### Post by bettlebrox on 2007-09-19
> **southernman said:**
> 
and if the terminal shows it as *drwxrwxrwx 2 root root 68K 2007-09-18 02:14 /usr/bin/* would be the same as 777

Absolutely correct!

> **southernman said:**
> 
bettlebrox, I really appreciate you taking the time to explain it to me like a two year old! Had I looked at the perms via the terminal in the first place, I'd have known. (Forest meet Trees)

Again, Thanks!
Your most very welcome! :guitar:

---

