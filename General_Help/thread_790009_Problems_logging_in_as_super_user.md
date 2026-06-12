---
title: "Problems logging in as super user"
date: 2008-05-11
forum: General Help
---

### Post by ali999 on 2008-05-11
Hi

This might seem kinda strange or I am just missing something here, but whenever I try to log in as a super user by using the su command in terminal, i always get an error saying authentication failure. however, if i use sudo then everything goes fine. i thought sudo and su have the same password. any ideas?

---

### Post by MaindotC on 2008-05-11
Have you set the superuser password on a previous occasion?  You would have done this by typing:
```

sudo passwd su

```

Did you ever do that?  If not, do it.

---

### Post by ali999 on 2008-05-11
definately did not know i had to do something like this...thanks

---

### Post by MaindotC on 2008-05-11
Star me :)

---

### Post by pro003 on 2008-05-11
i you didn't give a different password to root then login in as super user in terminal goes:

```
sudo -s 
```

..and password :)

---

### Post by bingoUV on 2008-05-11
The way ubuntu is set up, sudo asks for the user's own password to give root access to him. su asks for the root password. So they are possibly 2 different passwords. In ubuntu, root password is not set until you do as advised above.

---

### Post by carusoswi on 2008-05-11
> **strAlan said:**
> Have you set the superuser password on a previous occasion?  You would have done this by typing:
```

sudo passwd su

```

Did you ever do that?  If not, do it.

Pardon me, but, if the password I want to use is xxxxxxx, then, what exactly would the code to complete this procedure be?  Something like:  sudo passwd su xxxxxxx  ??

I want to make certain I don't mess things up.
Thanks.
Caruso

---

### Post by HunterThomson on 2008-05-11
when you want to become root in a bash you type

sudo su

????????
You do not have to set up a root password to log in as root in a bash with that comand. It should just ask for your password and then you type in your usr password.... You really don't want to set up a root password because someone can connect to your SSH and then run a password cracker on your root account. If you don't have a usr named root then it is a lot harder to do that because then they also have to try different usr names... at lest that is the theory as I understand it.

star me:guitar:

---

### Post by HunterThomson on 2008-05-11
If you do want to set up a root account that you do not need this is how you do it....

sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
Passwd: password updated successfully

if you decide you want to lock the root account after unlocking it gine the comand 
sudo passwd -l root

Double Star me:guitar::guitar:

---

### Post by pro003 on 2008-05-11
**

there you go!

---

### Post by HunterThomson on 2008-05-11
> **pro003 said:**
> **

there you go!

:lolflag: Thank You :lolflag:

---

### Post by pro003 on 2008-05-11
you're welcome :)

... here's one more * !

:lolflag:

---

### Post by pro003 on 2008-05-11
as gratitude you could send me visa so i could take a breath of Hawaiian air...

---

### Post by bapoumba on 2008-05-11
[Please read]("http://ubuntuforums.org/showthread.php?t=765414"), thanks.

---

### Post by wavesound on 2008-05-11
Hi All
Something that bit me hard on Ubuntu. :(

I setup a laptop for a friend at the BBC (an IBM think pad)
I used my account to run setup and install, then set up his account.

Then I deleted my account after making him an admin.

Really bad mistake as there was no admin account on the lappy.
Also I cant get his USB keys to mount as P mount gives an error.

Any ideas how I get P mount to play?

Cheers
Bob

---

### Post by HunterThomson on 2008-05-11
> **pro003 said:**
> as gratitude you could send me visa so I could take a breath of Hawaiian air...

Ya, trust me..... It is ****ing grate!!!! the air coming in on the south east of the Big Island is so clean that it is what all other air is compared to because it is so clean. 

85F all year and the clearest "blue" 75F water you will ever see.

The cheapest time to get a flight is the last couple weeks of Dismember and the first week of January from CA or Las Vegas. This is  for people her to see there families cheep for the holidays.

---

### Post by mister_pink on 2008-05-11
You probably want to start yourself a new thread. Bascially you want to go in System->Admin->Users and groups, unlock it, then select their user, properties, user priviledges and tick them all. 

However, if theyre not already an admin it wont let you do this, so youll need to boot into recovery mode and do: 
usermod -a -G admin "theirusername"

---

### Post by HunterThomson on 2008-05-11
> **bapoumba said:**
> [Please read]("http://ubuntuforums.org/showthread.php?t=765414"), thanks.

Are you people for real????????

I can't tell people how to do things on there computer and there "Open Source" OS???????? I guess seance I didn't get a warning you kind of agree with me or it was the fact that I explained that you didn't need to set up a root account and why it was a bad idea to do so. But come on isn't the whole reason FOSS and Open Source exists is because we believe in the freedom of information????????? Becoming known as restricting the freedom of information could really heart Ubuntu in the long run. Though, I admit this situation is a vary small thing... It's just the point of the thing....

---

### Post by HunterThomson on 2008-05-11
Don't make your account part of the root or administrative group with out enabling administrator log in first otherwise you will not be able to log in  to your computer. 

The way to enable the root account is in fact the way I said. There are no GUI's evolved in the mix. I have done it before. I logged out and then typed in user name root and the password I have it and I was logged in as root with isn't own desktop and all.

---

### Post by wavesound on 2008-05-11
> **mister_pink said:**
> You probably want to start yourself a new thread. Bascially you want to go in System->Admin->Users and groups, unlock it, then select their user, properties, user priviledges and tick them all. 

However, if theyre not already an admin it wont let you do this, so youll need to boot into recovery mode and do: 
usermod -a -G admin "theirusername"

Hi 
Thanks for the quick reply I thought as I'd added him to the admin users as you say, and I was all right to remove my account.
I have now been reading about the main user account in Ubuntu (and the root verses Sudo stuff)

I'll know next time!
ps I did manage to use the recovery console and set him up as the main user Just can't mount any usb stuff, must be a permission thing.

Cheers
Bob

---

### Post by mister_pink on 2008-05-11
> **HunterThomson said:**
> Don't make your account part of the root or administrative group with out enabling administrator log in first otherwise you will not be able to log in  to your computer. 

The way to enable the root account is in fact the way I said. There are no GUI's evolved in the mix. I have done it before. I logged out and then typed in user name root and the password I have it and I was logged in as root with isn't own desktop and all.

:s I was replying to the other guys question, which really was unrelated to the original question. Also putting yourself in the admin group just gives you sudo privileges. The first account you set up is in this group by default, it won't break anything. If you read that thread it also explains quite clearly why they don't want people explaining how to enable the root account, and I think its quite justified. If you don't like it you're always welcome to start your own ubuntu support forum. 

wavesound: Make sure all those boxes are ticked. If that doesn't help then I'm not really sure where to go next, as I said though, you'll probably get more attention with a new thread if you havent made one already.

---

### Post by Gina on 2008-05-11
I wholehearted agree with the Forums' policy on root/sudo.  Just because Linux lets you do anything doesn't mean you should promote bad or unsafe practices.  Various programming systems allow people to write viruses and other malware but I don't think many would advocate posting a HowTo, on these or any other forums!  (Not quite a parallel example but maybe sufficient to make the point)

---

