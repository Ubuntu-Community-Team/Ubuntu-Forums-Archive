---
title: "It is highly recommended NOT to allow root to login graphically!"
date: 2006-09-08
forum: General Help
---

### Post by danielfretto on 2006-09-08
i think i may have done this.  now my passwords, root or user, are not recognized in any way at any point.

any suggestions?

](*,)

---

### Post by Wolki on 2006-09-08
Well, it is not recommended, but it shouldn't break things in this way.

What exactly are the symptoms?

When you press ctrl-alt-f1 you should get to a text console. can you login there? Does it give you any error messages?

Do you think of anything you could have done that caused this?

If you select failsafe at the start prompt, it will ask you for your root password (after you have set one). Does it work there?

---

### Post by danielfretto on 2006-09-08
i got password incorrect for either user or root in that mode.  also i got stuck there.  how do you get out of that console mode?  i had to cold reboot.

---

### Post by danielfretto on 2006-09-08
the details are:

i altered startup options recently to bypass the need for a password for user and root for convenience sake.

since then the system does not recognize either password at any point...starting synaptic, manually installing apps in terminal, etc...

no other known symptoms.

---

### Post by Wolki on 2006-09-08
To get out of the text terminals, press ctrl-alt-f7.

Oh, socan still log into your box, only you can't use su or sudo nor login as root?

hmm...

one thing you could try is setting a new password for root.

Do this:

- Boot from a live-cd
- mount your / partition into a folder inside your home directory on the live cd (using system -> settings -> disks or the terminal), I'll assume the folder is callem temp
- Open a terminal in your home, do "sudo chroot temp"
- wait until you get a prompt again, the do "passwd root"

---

### Post by danielfretto on 2006-09-08
man this site really takes a while to load.  you still out there?

i'm finally on live cd and rather clueless as to the next step.

---

### Post by danielfretto on 2006-09-08
how do i mount my partition?

how do i create temp folder?

---

### Post by Anonii on 2006-09-08
mkdir temp
mount / temp
sudo chroot temp

---

### Post by danielfretto on 2006-09-08
thanks...not sure what's next

ubuntu@ubuntu:~$ mkdir temp
ubuntu@ubuntu:~$ mount / temp
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount / temp
mount: / is not a block device
ubuntu@ubuntu:~$

---

### Post by Wolki on 2006-09-08
Yeah, the forums are really slow today :-/

ok, the first part was correct "mkdir temp"

second part, first you need a sudo in front, but thats not all, you need to know the device name of your ubuntu partition. Usually they look like /dev/hdxy or /dev/sdxy, depending on whether you have ide or sata i think, where x is a letter and y is a number. eg, first partition on the first hdd is hda1, second on the first partition is hda2 and more or less so on. The graphical tool I mentioned might make this easier for you, on the command line pressing the tab key will try to autocomplete it for you, and if it cant, pressing it twice will show you the possibilities. try /dev/hd<tab, tab> to see what you have.

So, if you only have ubuntu istalled on the first drive (ide), the command would be "sudo mount /dev/hda1 temp". But, if you're on a 6.06 live cd, try the graphical tool first.

Third sommand (sudo chroot temp) was correct again.

---

### Post by danielfretto on 2006-09-08
:-D 

it worked.

Now how do i change things so i know my own passwords?

---

### Post by Wolki on 2006-09-08
Are you still in the chroot? Then do "passwd danielfretto", or what your username is.

---

### Post by danielfretto on 2006-09-08
thanks a billion.

changed user and root.

i am back in regular user mode and one more step away from xp...thanks to all ya'll.  :D

---

