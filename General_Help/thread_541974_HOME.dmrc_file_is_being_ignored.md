---
title: "HOME/.dmrc file is being ignored"
date: 2007-09-03
forum: General Help
---

### Post by paulem on 2007-09-03
On boot up I get a message saying HOME/.dmrc file is being ignored. On pressing ok the bootup continues successfully. What can I do to correct this apparent anomaly ? I have looked at advice on this fault on your forums and tried some suggestions but none of them work so it does seem to be a not uncommon fault. 

Would it be wise to upgrade my edition 6.06 of Ubuntu, and would this upgrading actually cure the problem ?

As I now am not able to transfer files to my USB memory stick, nor can I copy files to my DVD writer are these problems related to the first one ?

---

### Post by taurus on 2007-09-03
_Assuming_ your login name is **paul** (replace it with the right now if it is not), boot into recovery mode and do

```
chmod -R 755 /home/**paul**
chown -R **paul**:**paul** /home/**paul**
chmod 644 /home/**paul**/.dmrc
```
Reboot and you shouldn't see that error message about your $HOME/.dmrc again.

```
shutdown -r now
```

---

### Post by paulem on 2007-09-03
Thanks 'Taurus'

I have tried and failed yet again. I booted into recovery mode and managed to stop it scrolling by typing 'e' and then had four options that I don't know what to do with.
they were 
         root..........etc.....
         kernel..........etc.....
         inittrd.........etc.......
         boot..........etc   .....
where do I go from here ? I did try typing in the first line but it was not recognised.

I have also tried typing the code in 'terminal' but again it is not recognised, nor can I type in more thaan one line at a time. 

As you can see I am not familiar with code at all. 
Incidentally what is my login name. I know my password and paulem is the name of one of my home directories but as far as I know I dont have another name called login. Sorry.

Thanks again

Paulem

---

### Post by taurus on 2007-09-03
When you first turn on your machine, you will get to a GRUB screen and you have 3 seconds to press a key.  Press the Esc key to bring up the menu.  Then, use the down arrow key to move to the second option (usually) to highlight the recovery mode.  Hit Return to boot from it.

If you see text passing by in the screen, it means that you didn't press the Esc key fast enough.

---

