---
title: "Apply chmod to software : how to ?"
date: 2013-01-17
forum: General Help
---

### Post by Akasashasha on 2013-01-17
Dears,

Ubuntu 12.04 LTS
We are few person sharing the same computer.
I'd like user_1 to be the only one to be able to use few software (like xampp, terminal, filezilla, .... )
as I'm new to Ubuntu (coming from windows XP) and I do not know what is the path to this softwares (in windows they were all stock in "C:/.../Softwares"), can someone point to me the right direction ?
I imagine I then need to write a terminal command such as: 
sudo chmod user_1 700 /path_to_software/
but I'd like not to write the command line each time I open a new session, so how to write this command line in such a way that this permissions do not change when turning the computer on and off ?

hope is clear ... sorry for my broken english.

;)

---

### Post by cogier on 2013-01-17
Can you not set up controls using the "User Accounts" for each person?

---

### Post by Akasashasha on 2013-01-17
not possible in this version of Ubuntu, we can just change the language and choose if it is an administrator or a normal account ... so all this should be done via command line ... 
other suggestions ? :p

---

### Post by irv on 2013-01-17
Here is a couple of links that might help.

[http://www.howtogeek.com/54036/how-to-create-a-family-friendly-ubuntu-setup/]("http://www.howtogeek.com/54036/how-to-create-a-family-friendly-ubuntu-setup/")

[http://askubuntu.com/questions/8149/how-can-i-restrict-program-access-to-other-users]("http://askubuntu.com/questions/8149/how-can-i-restrict-program-access-to-other-users")

---

### Post by mcduck on 2013-01-17
Chmod won't help you here, there aren't any separate permissions for each user, and anyway pretty much all the system files should keep their current ownership (root) and permissions. So the file permissions will not allow you to exclude a specific user while leaving your own user still able to run the program.

The usual way to accomplish what you are trying to do would be simply using the lockdown options of whatever desktop environment you are using. For example Gnome allows you to configure certain user's menus to only show selected applications, and then lock down the menus so that the user can't edit them himself. And there is also an option to prevent suer from starting a terminal (or printing, or saving any files, and so on). I have no experience how this stuff works on Gnome 3, though, but it's definitely something you should be looking at. 

...and you could also check how the guest account works, it's quite strictly limited and taking a look at how it's done would likely be helpful for your purposes as well.

---

### Post by snowpine on 2013-01-17
Can you give us some background on why you feel this is necessary? 

The non-technological solution would be to implement a clear computer use policy at your office/school/home. For example if certain users are caught playing games or surfing inappropriate websites, there will be consequences. (Or consider simply allowing your employees/students/children to play games or whatever as a reward for satisfactorily completing the assignment.)

---

### Post by rnerwein on 2013-01-17
> **cogier said:**
> Can you not set up controls using the "User Accounts" for each person?
hi
whats about: acl (acces control lists): apt-get install acl
i think this will help
cheers

---

