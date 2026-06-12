---
title: "Accidently changed the group of * to my login! OOPS (help)"
date: 2007-04-07
forum: General Help
---

### Post by closer9 on 2007-04-07
Okay... so I just upgraded to feisty and my mounted drives permissions were changed to root. So I went into the /mnt directory, and did a chown username:username * -R. Nothing to serious right?

The thing is... I _wasnt_ in the /mnt directory, I was in /

Fantastic. After I realized what I did, I changed /usr/bin and /usr/sbin to root:root, got sudo working again... but stuff is still messed up. So basically I'm asking you guys... how bad did I mess up Ubuntu? Networking is busted and I cant use any gui tool that requires root.

-Closer

BTW.. I know what I did was stupid, no need to remind me :-P

---

### Post by iammeagain on 2007-04-07
it sounds similar to a problem i had before. I think you took yourself off the root group so that it won't even let you put a password in to run a program that requires root. I believe you need to boot into something like recovery mode from grub, my comp is packed away so i can't check what it is called exactly. Im checking older posts of mine to see if i can figure out how i fixed this in the past.  I dont seem to be having any luck finding it. 

The recovery mode or whatever it is called will drop you into a command line interface, which i believe you have root permissions. From there you will need to know what commands will allow you to change a user's groups. At least i hope thats what the problem is, because its not too hard of a fix once you know what it is to type.

Hope that helps some.

---

### Post by closer9 on 2007-04-07
Thanks for the reply. Yeah i logged into single user mode and that gives me root. What I think is wrong is some (alot?) of the files in the distro need to be owned by root to work correctly, and I messed that up by making everything owned by me. 

This is what I'm thinking I need to do:
Boot into single user mode
chown everything as root (chown root:root / -R)
chown my home directory to myself (chown closer:closer /home/closer -R)
chown any directories that should be owned by a service (chown mysql:mysql /path/to/mysql -R)

But thats what I'll try as a last attempt. I don't want to break it anymore then it already is :-) I'm basically just wondering if there is a better way. Like a debian tool or something (dpkg-reconfigure all_packages?)

-Closer

---

### Post by iammeagain on 2007-04-07
oh ok i see now. crud i dont know of any other way. I would tell you some of the folders and what they are owned by but i don't know becuase like i said i don't have access to my linux computers right now. well if you have to end up doing that you should definately back up before just to be careful. Sorry i can't be of more help.

---

### Post by closer9 on 2007-04-07
Okay... Maybe this is a bug with feisty or something. This is what I've discovered:

I actually was NOT in the root directory. For some reason when I do this:

chown closer:closer /mnt/storage/ -R

It was the same as doing:

chown closer:closer / -R

Now looking into it... /mnt/storage/ is assigned to sdc1 and ubuntu is installed on sda1. BUT for some reason when i mount /mnt/storage/ it actually mounts sda1 there. Looking at fstab shows the that /mnt/storage/ is sdc1, i just dont get it. mtab shows /dev/sdc1 as /mnt/storage/ but that is just not the case :-P

I'll keep looking into it and report what I find.

-Closer

---

### Post by closer9 on 2007-04-07
OKay guys.. i cant figure it out. I cant seem to get networking back up and running (permission errors). The mount problem isn't there anymore though :-\

So, before I give up, is there any way I can reset the owner/group of the installed files back to the way they were? dpkg-reconfigure -a didn't work. Basically, is there a tool to reinstall all the packages and fix the permissions? Or can I "reinstall" using the live CD without resetting all my information?

Thanks for any help.

-Closer

---

### Post by closer9 on 2007-04-08
Bump before I reinstall... :-|

---

### Post by closer9 on 2007-04-09
Guess I'll just reinstall.

These forums are 0 for 5 so far with my questions :-\

---

