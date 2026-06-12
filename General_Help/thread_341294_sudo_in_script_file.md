---
title: "sudo in script file"
date: 2007-01-18
forum: General Help
---

### Post by Lutherian on 2007-01-18
Greetings&#12290;

I'm trying to create a script file to mount several directories on a remote windows computer.
these commands require the sudo command: sudo smbmount <etc>
The script files works well enough, but requires root password several times (for each directory mounted) 

Is there a means of entering the password in the script file ( I was unable to find this in the [man]ual sudo ... probably because it's a security risk. 
Any advice?

Thanks

---

### Post by taurus on 2007-01-18
Why not create a script (without the sudo in there), then run it with the sudo command!

---

### Post by khedron on 2007-01-18
Heh, or put [b]sudo su[\b] at the beginning of the script. That will give you sudo rights for the rest of the script.

---

### Post by moma on 2007-01-18
I agree with Taurus.  Force the user to run it as root or with sudo admin rights.
I have done the root-admin check in this (old) script: [http://www.futuredesktop.org/tmp/inst_qemu.sh](http://www.futuredesktop.org/tmp/inst_qemu.sh)

You can also test 
$ id -u 
prints 0 if root-admin

---

### Post by Lutherian on 2007-01-18
I didn't realise one could do that, maybe I'm overcomplicating things needlesly!! 
I should have at least guessed that I could do that <sigh> I feel a bit silly but thanks guys, much appreciated.

---

