---
title: "Can't Log In :("
date: 2007-05-18
forum: General Help
---

### Post by polkaishot on 2007-05-18
So everything installed fine, I had to change the virtual disc size to 4gb.. no probs...

Now when I get to the login screen... it won't let me!

It tells me that my password is incorrect. I tried the username and password I setup during the installation process and I also tried username: ubuntu and pw: ubuntu and neither worked.

Any suggestions? I really want to get this set up asap :(

---

### Post by dans595 on 2007-05-18
I may repost this but here is my experience so far, and how I got WUBI installed, and how I ended up having the same problem as you (or similar):

1) Got stuck at 33% formatting virtual disk overnight

2) Reinstalled, ran jkdefrag, stalls at 33% again

3) Uninstalled, reinstalled with 4gb / 1gb / .5gb

4) Ran jkDefrag, system hangs while I am trying to open a word processor

5) Powered off and booted into ubuntu, before 'formatting' or finishing the installation, it simply goes to a command prompt and does nothing

6) Reinstalled with 3gb / 1gb / .5gb

7) Restarted and made it through formatting.  Got a red error about DHCP (wasn't hooked up at that moment).  Continued, it finished, restarted.  Chose ubuntu from the boot screen, went to the ubuntu splash screen / loading screen.  Waited a few minutes and it went to command prompt with error "apt-get: command not found"

8) Pressed Ctrl+Alt+Delete in hopes of restarting the machine from prompt at which the above error occured, and it loads into ubuntu?

9) Username and password that I selected do not work (I figure I must have typed it wrong or something)

10) Reinstalled with 3gb / 1gb / .5gb

11) Reperform steps 7, 8, and 9


So now it is 'installed' (I think?) but I can't log in.

---

### Post by logan1441 on 2007-05-19
Originally Posted by ecology2007  View Post
You do not need to manually edit menu.lst, boot.ini or anything like that.
You do not need to type any command.
I assume you have only one disk. The best thing for you is to uninstall and reinstall.
1 ) locate c:\wubi folder.
2 ) copy paste /wubi/install/ubuntu-7.04-alternate-i386.iso, put it in the same folder than wubi-test-1.exe
3) run wubi-test-1.exe, do full uninstall.
4) run wubi-test-1.exe, do install with default setting
Do not use spaces or weird characters in your username and passwords.
5) reboot.
6) select ubuntu.

If that does not work, come here and give exact error messages and a description of your computer and hard disks.

---

### Post by logan1441 on 2007-05-19
i had same problem but now it works perfectly

---

### Post by ago on 2007-05-20
> **dans595 said:**
> Waited a few minutes and it went to command prompt with error "apt-get: command not found"
hmm that can be a new bug... Anyone else with that?

---

### Post by polkaishot on 2007-05-28
should've posted this sooner, but id been busy so i didnt retry anything until a few days ago...

so, i uninstalled and reinstalled and it worked fine. dont really know why it wouldnt let me login, i probably typed something wrong when i created my password, i guess?

i also used the same specs as before.

---

