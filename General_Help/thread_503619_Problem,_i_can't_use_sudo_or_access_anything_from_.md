---
title: "Problem, i can't use sudo or access anything from the administrative panel"
date: 2007-07-18
forum: General Help
---

### Post by sarahsilverman on 2007-07-18
this is the message i get at login for guest.

"user's $home/ .dmrc file is being ignored. this prevents the default session and language from being saved. file should be owned by user and have 644 permissions. user's $home directory must be owned by user and not writable by other users."

i am the administrator, i just wanted to see if the sudo thing worked there. sorry i am new, i just got ubuntu right out of a magazine. really cool.

the out put from ls -l .dmrc is : -rw------- 1 jonathan jonathan 26 2007-07-17 17:32 .dmrc

i think that this happened because i wanted access to a file that said i didn't have permissions. so i researched and got a little text i could paste into the terminal. sorry i can't remember what i searched or what the text was, i wish i did. the only peice of text i remeber is "chown" because it sounds like some kind of fish to me.

thank you, any help is appreciated ;)

---

### Post by sarahsilverman on 2007-07-18
why won't anyone help me T_T

---

### Post by needtolookatascreenshot on 2007-07-18
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by sarahsilverman on 2007-07-18
> **needtolookatascreenshot said:**
> chown == change owner

As the permissions on you .dmrc file look they way they should be, I think you might have changed the owner of your homedir.

Could you post the output of ls -l /home

Also, for future reference. If you are unsure about what a command does, you can most of the times get a short description with command --help. And you'll get a longer one with man command.

P.S.: As for nobody helping you. Give the people some time. I know this can be frustrating, but keep in mind that people spend their freetime here trying to help people.

the output is: total 8
drwxr-xr-x  2 jonathan jonathan 4096 2007-07-17 18:39 guest
drwxr-xr-x 30 jonathan jonathan 4096 2007-07-17 23:28 jonathan

thankyou i love you so much:popcorn:

---

### Post by needtolookatascreenshot on 2007-07-18
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by sarahsilverman on 2007-07-18
> **needtolookatascreenshot said:**
> Ah, which is the account you are having trouble with? The guest account? The permission on jonathan do look alright.

If it is your guest account, which is now also owned by jonathan, but should in fact be owned by the user guest, try the following:

sudo chown -R guest:guest /home/guest

Explanation: the command changes the owner (the first guest) and the group who own /home/guest (the second guest behind the column). The -R makes this recursive, so that all files and folders in /home/guest will now be owned by guest.

Hope this helps

i can't it says "sudo: must be setuid root"

---

### Post by sarahsilverman on 2007-07-18
here is another output that others asked me to put: ---s--x--x 1 jonathan jonathan 91508 2006-10-09 01:37 /usr/bin/sudo

---

### Post by sarahsilverman on 2007-07-18
i tried what someone else said and now when i use sudo its output is: sudo: /etc/sudoers is owned by uid 1000, should be 0

can't use sudo

what i used was chown root:root /usr/bin/sudo

i try to get into root but can't because i don't know the password and can't change the password because i can't access anything from the administrative panel. it just shows the taskbar list then disappears.

---

### Post by needtolookatascreenshot on 2007-07-19
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by sarahsilverman on 2007-07-19
> **needtolookatascreenshot said:**
> Ok.

To get root, reboot your computer and start in recovery mode. You'll now have a root shell. (Don't worry, you'll find yourself in textmode only, but that's ok).

Now, once you've done that, setuid root sudo with the following command:
chmod u+s /usr/bin/sudo

Then reboot (just type reboot) and you should be able to use sudo again.

yes its fixed wee, i love you:guitar:

---

### Post by needtolookatascreenshot on 2007-07-20
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

