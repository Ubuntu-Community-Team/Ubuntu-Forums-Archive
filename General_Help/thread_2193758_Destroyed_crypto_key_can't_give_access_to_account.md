---
title: "Destroyed crypto key can't give access to account"
date: 2013-12-14
forum: General Help
---

### Post by tootmis on 2013-12-14
I am not sure it is so but I tried to check disk under recovery console and it said 0.8% of that disk (non-contiguous) where the crypto key is (i think so because under gparted it has cprypto sign). 

Ubuntu starts up and welcome screen is there but I tried to use my password and it is not work. 

Change password under Root from Recovery console is not functional. It says Authentication token manipulation error pass unchanged. Root console can't start x-window as well
It is strange that I can't make fsck under Recovery console... I cant see just Black screen!!! But I did it under root console.
More strange that i can't change password for Root. It returns me same Authentication token manipulation error... 

About disk... Disk drive is not ready for /dev/mapper/cryptoswap1 ... 

May be I am not right and it is something other but not disk destroing



QUEST login is functional without any problems. but I can't use su in Terminal
The case happened after last update about 3month agou... I did not have time before. But now I am really need my account back.

Questions... 
I can't see nothing interesting in logs but i can put it here... 
How it works with crypto account i am not realaly understand what I must do to recover... ( I did not copy key to external USB or somewhere else) 


Can I return back somehow the systems state 4 month ago or 2?

 HEEEEELP! 


How can I fix this ?

---

### Post by tootmis on 2013-12-15
I just check how can I work in root shell and was shocked.  Under root shell i can't set for example User Permissiions... or even delete some files ??? Must be so????????????

 mount -rw -o remount is not functional.... 

funktional with slash / 

ok now is onother story.... I can't login anyway... it blinks after password entering and then drops to login windows again

---

### Post by tootmis on 2013-12-15
more information... 
I tried to use CTRL-ALT-F1 and can login as user but still can't access to my files..  If i use ecryptfs-mount-private and try to use my passphrase it said me the it is incorrect... but I did not change it... Where I can find this passphrase else? Is anywhere some backup for this passphrase or not?

I just read that it is possible to compare .sid inside .private directory and new passphrases or it is something wrong?

---

