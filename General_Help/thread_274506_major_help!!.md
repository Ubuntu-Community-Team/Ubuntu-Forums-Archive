---
title: "major help!!"
date: 2006-10-09
forum: General Help
---

### Post by kickenchicken on 2006-10-09
how do i chang emy slef back to adminsitrator o was messing arround with settings and dont know  ow to make my slef the owener admins of  my comp. there for i can run much commmands. anyone? please i dont feel like re-installing ubuntu

---

### Post by kickenchicken on 2006-10-09
please. anyone?

---

### Post by DarkN00b on 2006-10-10
The default user in Ubuntu never has root priveleges. That is why "important"commands must be prefixed with sudo. Sudo stands for "**S**uperuser **D**o. To enter a command with root priveleges, just type ```
 sudo command -options
``` (where "command" is the thing you are trying to do and "-options" are any well, options for that command) into the terminal. It is actually a bad thing to give yourself permanent root prevelege because it opens up all kinds of possibilities for bad things to happen.

Did that even make any sense? Hydrocodone (legal prescription for back pain!) makes you say some wierd stuff.

---

### Post by meng on 2006-10-10
> **DarkN00b said:**
> Did that even make any sense? Hydrocodone (legal prescription for back pain!) makes you say some wierd stuff.
Yeah sure darknoob or should I say Rush Limbaugh!

---

### Post by DarkN00b on 2006-10-10
I just spent the last 5 days looking at the ceiling because of a pinched sciatic nerve.:p 

I think I deserve a little -um- rest! Yeah that's the ticket.

---

### Post by meng on 2006-10-10
Just teasing. Seriously, hydrocodone for short-term use is fine, with low addictive potential. Hope you're back on your feet soon.

---

### Post by DarkN00b on 2006-10-10
Last off topic reply and I'm done, I promise.

I went back to work today and dealt with excruciating pain for about 4 hours, then the pain almost totally disappeared.  I'll sleep good tonight though.

Oh, and thanks for the well wishes.

---

### Post by meng on 2006-10-10
Back on topic:
after typing a command using sudo, when you are asked for a password, remember to enter your user password.

---

### Post by DarkN00b on 2006-10-10
...and when you type in your password, you will not see any change on-screen. Just keep typing and then hit enter.

---

### Post by kickenchicken on 2006-10-10
am i supposed to see anything type while i type? because i dont. no when i installed ubuntu i was able to see synaptics package thing.. now i cant and i need it to install pacakges. how would i go about top restore em? when i type that sudo thing eas somethin supposeed to pop up? one more thing i really need to get those priveleges back as when i try to do something here:  [http://ubuntuforums.org/showthread.php?t=224321](http://ubuntuforums.org/showthread.php?t=224321)
i try to do the steps in 9 but it denied me access to anything.

---

### Post by meng on 2006-10-10
> **DarkN00b said:**
> ...and when you type in your password, you will not see any change on-screen. Just keep typing and then hit enter.
No you won't see anything when you type the password.

---

### Post by kickenchicken on 2006-10-11
ok i tried but when i i just need the code to at least access the privaliges folder or something so i can give my self my original rights. i remeber doing somehing under users and groups i changed my self or somthing to root and it was to tweak some files to try to install my sound card. look this is what im trying to do 

 

 1) Open a terminal by going to Applications>Accessories>Terminal
2) Get to the root directory with permission to edit the /etc/modules file by typing "sudo -i"
3) To open and edit the /etc/modules file, type "nano /etc/modules"
This will open up a text editor and (obviously) the /etc/modules file. Than, I simply...
4) Enter "snd-cs4236" on a blank line underneath everything that's already typed.
5) Hit Ctrl-X to exit.
6) It will ask you if you want to save the changes, I *think* you just hit "Y" and it saves and exits at the same time.
7) Reboot
(note....between 5 and 7, I opened the file again using "nano /etc/modules" just to make sure it saved correctly; it did for me)
Log back in to ubuntu
9) Do the dance of joy now that you have sound working!

these are the steps im trying to do but when i go into the etc/modules thing it try to save it and it denies me access.

---

### Post by kickenchicken on 2006-10-12
Bump??

---

### Post by codejunkie on 2006-10-12
kickenchicken

what exactly is the problem your having have you completly lost root/admin access or are you just unable to edit /etc/modules

---

### Post by mssever on 2006-10-12
Reboot into recovery mode, then edit /etc/group:
```
nano /etc/group
```

Add your username to both the adm and admin groups in that file, save, and reboot normally (you reboot by typing reboot). For example, in my group file, I have a line that reads ```
adm:x:4:scott
```

---

### Post by jtmedin on 2007-03-14
Wife had sciatica pain but we bought a new sleep number bed & she set hers to 100. Next am no pain & hasnt returned. PTL

---

