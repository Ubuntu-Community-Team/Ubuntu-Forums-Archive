---
title: "Have to enter password twice"
date: 2008-06-03
forum: General Help
---

### Post by ManaWannabe on 2008-06-03
I am having problem when entering my password to log in, as well as when I use "sudo" commands. I also can't seem to open Synaptic Package Manager; after I type in my password nothing happens. What is happening?

---

### Post by mali2297 on 2008-06-03
Hi.

To be able to troubleshoot, we need more information...

Do you mean that sudo asks for your password twice? After that, it works?
When did the problem first appear? 
Have you created any new users or groups? ...or edited the sudoers file?

---

### Post by georgeclooneylookalike on 2008-06-03
I have to enter my username and password twice when I log on and when I try to install anything Synaptic won't ask me for the admin password and hangs. I am running 8.04 on this PC and 7.10 on another and right now I am thinking 8.04 is as bigger mess as 7.04 was...

---

### Post by mali2297 on 2008-06-03
It is still not much to go by...

Open a terminal and try
```

sudo whoami

```
What are the results? Any error messages?

---

### Post by cariboo on 2008-06-03
Make sure you computer is named in /etc/hosts

eg:

```
jimk@intrepid:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	intrepid
```

The name of my computer is **intrepid** in the above code

To add your hostname to /etc/hosts, just use your favorite text editor as root and edit the file.

```
sudo gedit /etc/hosts
```

edit, save and exit and you should be ok.

Jim

---

### Post by ManaWannabe on 2008-06-03
> **mali2297 said:**
> Hi.

To be able to troubleshoot, we need more information...

Do you mean that sudo asks for your password twice? After that, it works?
When did the problem first appear? 
Have you created any new users or groups? ...or edited the sudoers file?
Whenever I work in Terminal, the password prompt reappear after I am absolutely sure I typed the correct password. Usually when I type the wrong password it says so, but now it just asks for the password again.
Also, at the login screen when I turn on the computer, similar thing happens. I typed my username, pressed enter, it goes to the password screen; I enter the correct password, pressed enter, nothing happens. I enter the password again and it logs in.
The problem is occuring at my home computer, I will provide more information when I get home tonight.

---

### Post by antiOST on 2008-07-25
Hi

I'm experiencing the same problem, I also have to type password twice, at the window login screen (username once, and prompts me for password twice), when I do a sudo (the application opens correctly) and when I do it from GUI I only get to type the password once and the application doesn't open (shortly I can see "starting administration..." and the nothing happens)

This happens *every* time and I'm positive that I type the correct password (or else I wouldn't be able to open applications with sudo)

I haven't changed the sudoers file and haven't added any new users or groups.
sudo whoami gives me root
whoami gives me zaphod (thats the name of my user)

My computer is in the etc/hosts file.

Recently I installed btnx (for customizing mouse input) but I'll suspect this happened when I change my login window but I don't know how to change it back through CLI and I cannot start the GUI System->administration->Login Window because of this "password twice" problem.

I also installed ubuntu updates recently but can't recall whether this problem came before or after.

Edit: I'm running Gutsy, output from uname -a: Linux Arrakis 2.6.22-15-generic #1 SMP Fri Jul 11 19:25:33 UTC 2008 i686 GNU/Linux

-Kim

---

### Post by antiOST on 2008-07-28
Hi

Solved my problem, I noticed that on my login window, it said "enter password or swipe finger" the first time I entered the password and that it didn't matter if I typed the wrong password the first time.

I've been playing around with thinkfinger a couple of months ago but couldn't get it to work.
It seems that somehow its enabled correctly now and the reason it asks me twice is because I get the option of swipe my finger first, if this fails I can type my password correctly and login in (it actually works by swiping my finger now and then I won't have to type my password twice).

anyway here's what I did to disable thinkfinger again

```
sudo gedit /etc/pam.d/common-auth
```

and commented out this line

```
#auth   sufficient      pam_thinkfinger.so
```

I found the solution here:
[http://ubuntuforums.org/showthread.php?p=4878510](http://ubuntuforums.org/showthread.php?p=4878510)

-Kim

---

### Post by mistofeles on 2009-10-21
WARNING: READ THIS THROUGH BEFORE YOU DO ANYTHING
- you can lock yourself out of your system !

in /etc/pam.d/common-auth you might have two lines of 'auth sufficient '.
Mark as comment another of them and test on terminal.
I marked another of those lines, and it helps. Now I have to find a way around this.
It seems that you can collect all these parameters on the same line, BUT you have to test and read a bit further. The order of the parameters seems crucial !!!

If you comment this line:
'auth sufficient pam_unix.so nullok_secure use_first_pass'
you will lock yourself out of your system and have to use rescue disk.
A good way is to connect to your system with SSH from another PC with root privilegs and keep it open all the time. Now you can open two or more virtual screens (black no-GUI login screen)  with root privilegs. 
When you change your settings and logout from one screen, you can rechange the settings in another screen, if you lock yourself out.

Don't know what happends, but it worked for me. Still testing and trying to find why.

---

### Post by Breber on 2012-07-18
In /etc/pam.d/common-auth I had 

```
auth	[optional]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
```

and replaced it with

```
auth	[optional]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login use_first_pass
```

seemed to work for the two password entry issue.

Make sure you don't have any other modules conflicting or wanting pw confirmation.

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

