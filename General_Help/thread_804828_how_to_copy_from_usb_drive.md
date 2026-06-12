---
title: "how to copy from usb drive?"
date: 2008-05-23
forum: General Help
---

### Post by digikwondo on 2008-05-23
might be a simple issue to solve, but for some reason i cannot access the "absolute beginers" section of the forum...

anyway i hope someone will be abel to help.

i have a mp3player with portableapps installed. and im running many programs from that drive on windows platforms. what i want to do is to create a bash script that copies/replaces over the whole profile folder for thunderbird  from that usb drive to t my linux system. (some kind of syncronisation u might call it) 

the command im trying to run looks like this, 

digikwondo@redhawk:~$ sudo cp -r /media/"ARCHOS 204_"/portableapps/thunderbirdportable/data/profile/ /usr/share/thunderbird/defaults/
[sudo] password for digikwondo:
cp: cannot overwrite non-directory `/usr/share/thunderbird/defaults/profile' with directory `/media/ARCHOS 204_/portableapps/thunderbirdportable/data/profile/'
digikwondo@redhawk:~$ 

as you can see i get "cannot overwrite non-directory" and both directories excists. im running the "cp" command with the "sudo" infront witch should eliminate any premissions issue (am i right?)

the primissions of /usr/share/thunderbird/defaults/ are these. ( the  folder i want to ovewrite is "profile"
ls -l
drwx------ 2 digikwondo root 16384 2008-05-14 11:39 gpg
drwx------ 2 digikwondo root 16384 2008-05-14 11:39 plugins
drwx------ 5 digikwondo root 16384 2008-05-22 17:44 profile
drwx------ 3 digikwondo root 16384 2008-05-14 11:39 profile_bak
drwx------ 2 digikwondo root 16384 2008-05-14 11:39 settings 

thanks in advance for any response!
//digi

---

### Post by Het Irv on 2008-05-23
What happens when you take out the "-r" or add a "-f"?

I'm not the best with commands, but here is the cheat sheet I use.  [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

btw: what do you mean, you cannot access the Beginners Section?

---

