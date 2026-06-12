---
title: "ssh-key based authetication"
date: 2008-04-02
forum: General Help
---

### Post by santhosh23 on 2008-04-02
Hi,


I use key-based authentication to login into remote servers from the linux terminal. i use ssh-agent and then add the keys with ssh-add everything looks fine however if i want to login into more than one server then i will have open many terminal and following the same procedure on all the terminal i.e by starting ssh-agent and then adding keys with ssh-add in each terminal.

i would like to is there a way to export your keys and the ssh-agent process from one terminal to another or any script which i can execute which might start the ssh-agent and add the keys.

your assistance in this regards is much appreciated.

---

### Post by bodhi.zazen on 2008-04-02
have you looked at keychain ?

[http://www.penguin-soft.com/penguin/man/1/keychain.html](http://www.penguin-soft.com/penguin/man/1/keychain.html)

[http://www.ibm.com/developerworks/library/l-keyc2/](http://www.ibm.com/developerworks/library/l-keyc2/)

Scroll down a little on that second link.

Note: keychain is in the repos

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=keychain&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=keychain&searchon=name&subword=1&version=all&release=all)

---

### Post by santhosh23 on 2008-04-03
Thanks for the reply.

I installed and keychain and with the help of a small script i tried loading it however it doesn't load the keys because i generated the keys with puttygen which is in .ppk format, i guess i will have to convert this to .pub for openssh to read. could please advise me on how to convert .ppk to .pub format.

---

### Post by bodhi.zazen on 2008-04-03
Only way I know of is with puttygen.exe

Download it here :

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Run it, upload your putty key, enter your password, then convert the key (save it as) to the open-ssh format  (should be an option on the menu, conversion perhaps).

---

### Post by santhosh23 on 2008-04-08
After i load the keys in the puttygen .......i click on conversion and export openssh option is greyed out...i get this option only when i generate a new key but not when i load the key.


is there any other way to convert ?

---

### Post by bodhi.zazen on 2008-04-08
Just ran puttygen

I generated a putty key

I can import the putty key and save it as an openssh key

Import the key go to Conversions -> export open ssh key

I can do the same with an openssh key (ie import it and save it as either a putty key or openssh key).

---

### Post by santhosh23 on 2008-04-10
i am actually looking for a script which can load my keys into when i execute the script. i did look for some open-sources like keychain but that will not work.

To brief the issue again, i have keys created public/private keys from puttygen which is ssh1 format with .ppk extension. i will not able convert the ssh-1 keys to ssh-2 the way openssh understands or for a matter any other open source.

My problem is i will have to upload these keys everytime i open a terminal by starting ssh-agent andn use ssh add to add the keys now i am looking for a srcipt which can do this for me

---

### Post by bodhi.zazen on 2008-04-10
> **santhosh23 said:**
> i am actually looking for a script which can load my keys into when i execute the script. i did look for some open-sources like keychain but that will not work.> 


[quote]To brief the issue again, i have keys created public/private keys from puttygen which is ssh1 format with .ppk extension. i will not able convert the ssh-1 keys to ssh-2 the way openssh understands or for a matter any other open source.

If the key is a putty key, first convert it to an openssh key. You can then try to convert it to an openssk2 key :

[http://www.ssh.com/support/documentation/online/ssh/adminguide/53/ssh-keygen-g3.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/53/ssh-keygen-g3.html)

[quote]-1 file

    Converts a key file from the SSH1 format to the SSH2 format.

Or this :

[http://docs.ocf.berkeley.edu/wiki/SSH_key_management](http://docs.ocf.berkeley.edu/wiki/SSH_key_management)

> **santhosh23 said:**
> My problem is i will have to upload these keys everytime i open a terminal by starting ssh-agent andn use ssh add to add the keys now i am looking for a srcipt which can do this for me

Your best bet would be expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

