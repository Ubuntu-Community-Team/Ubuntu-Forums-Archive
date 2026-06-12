---
title: "Can not restore old password"
date: 2007-11-18
forum: General Help
---

### Post by dryder on 2007-11-18
HI,
I accidentally changed my password from what I entered when I installed Feisty.

I am trying to restore it as per the post [[COLOR="Blue"]**_here_**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3509262&postcount=2") .

Using Recovery mode, the loading process eventually comes to a prompt at which point I type:

passwd root
and then enter the password (twice) I used on installation.

The prompt then returns. 

But when I reboot the old password has not been set and the one I don't want remains.

My thoughts are that I may not be continuing the Recovery Mode process properly when it returns to the prompt. How am I supposed to continue so I reboot please? (I type 'reboot')

Or, am I using the wrong method?

Many thanks,

David

---

### Post by nick_h on 2007-11-19
The post you were following is useful if you have forgotten your old password.  In this case you have to boot into recovery mode and then use the command:
```
passwd *username*
```
If you know your old password login and in a terminal type:
```
passwd
```
or go to System->Administration->Users and Groups

(Don't use "passwd root" this changes the password for the account called "root" which is not enabled by default.)

---

### Post by dryder on 2007-11-19
Thanks for your reply

I think I may have messed things up then:> Don't use "passwd root" this changes the password for the account called "root" which is not enabled by default.I did type "passwd root", during the Revovery Mode boot process I mentioned. 

This may seem a silly question but how do I test if root now *has* a password?  If root does now have a password, how can I undo this so the password is not enabled for root, please?




(Before doing it in the terminal, I did try, for my user password, the method
> go to System->Administration->Users and Groups but it insists on 6 characters or more. Mine is (now, again) 5 and is unique enough to be secure for me.
Using the terminal after logging on (passwd myname) enabled me to change it back to the 5 character original password.
I wonder why the gui method insists on 6 characters or more?)

---

### Post by nick_h on 2007-11-19
> **dryder said:**
> This may seem a silly question but how do I test if root now *has* a password?  If root does now have a password, how can I undo this so the password is not enabled for root, please?

To check if the account has a password type:
```
sudo cat /etc/shadow | grep root
```
This file contains ":" separated fields.  Field 1 is the username. Field 2 is the password which will contain "!" for a locked account or an encrypted password.

To lock it again type:
```
sudo passwd -l root
```

---

### Post by dryder on 2007-11-19
I'm sorry to be a nuisance but this part of linux/Ubuntu is new to me. I would rather learn and understand than simply 'copy and paste' _(No offence intended)_. It returned:
> david@ubuntu-server:~$ sudo cat /etc/shadow | grep root
Password:
root:$1$sEGp.76h$fjNiK9bYdTMUSWl56/5Bm1:13835:0:99999:7:::
david@ubuntu-server:~$ 


How do I know from this (if I am I correct):
> Field 1 is the username '$1$sEGp' translates to  'root'> Field 2 is the password which will contain "!" for a locked account or an encrypted password what the readable password '76h$fjNiK9bYdTMUSWl56/5Bm1:13835:0:99999:7:::' is?
Presumably this password is *not* locked as there is no "!" in it?

I can't tell from this what the password is, i.e. did I actually change it or is it the original disabled password Ubuntu created?
Does it matter if I changed it from the one originally created at install by Ubuntu?

I find this confusing because if root has a password created by Ubuntu but not enabled and the user / system administrator does not know what it is from the encrypted response above, why does Ubuntu set a password for root?

I know users shouldn't 'play around' with root access - so when is it ever used as admin privileges can be gained by gksudo?

Many thanks for your patience and help.

---

### Post by nick_h on 2007-11-19
You need to understand what you are doing.  I never just paste something that I don't understand.

In your output the fields are:
1-  root
2 - $1$sxxxxxxxxxxxxxxxxxxxxBm1
3 - 13835
4 - 0
5 - 99999
6 - 7
7 -
8 -
9 -

User root has a password (that you set) which when encrypted looks like field 2.

For details on the /etc/shadow file type:
```
man shadow
```
for the manual page and/or look [here](http://www.cyberciti.biz/faq/understanding-etcshadow-file/).

To look at the whole file (for interest) type:
```
sudo cat /etc/shadow
```

In my file field 2 was an exclamation mark.

To lock the account again use the command I suggested.  Look at the manual page first by typing:
```
man passwd
```

After locking the account have another look at the file.

Ubuntu does not set a password for root, the account is locked by default, and it is best to keep it locked.

Note:  As an afterthought I have changed part of your encrypted password to xxxxxx
This is because anyone could run a password cracking program on it to obtain your password.  Probably not too much of a risk but I thought I would xxxx it out.

---

### Post by dryder on 2007-11-19
:)Thank you nick_h, I learned a lot from your post and link.> You need to understand what you are doing. I never just paste something that I don't understand.
I wholly agree. Unfortunately, although everybody's intent is to help and provide answers, it is often the case where the answer just consists of "copy this and paste this". It is very easy to offend by asking for explanations or extra pointers to guides.

Often, googling and using search just doesn't provide the (correct) answers as the question, phrase or keywords are missing a vital word.

Your extra help in me understanding the process is greatly appreciated.
David

---

